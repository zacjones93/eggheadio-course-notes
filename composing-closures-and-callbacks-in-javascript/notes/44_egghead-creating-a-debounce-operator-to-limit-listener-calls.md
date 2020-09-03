Instructor: [0:00] On the subject of allow when, essentially waiting for this to happen, this gives us a good chance to talk about debouncing, or waiting for time to finish. If I wanted to wait for 500 milliseconds, this could also be called debounce.

[0:17] I would define a wait for like so. I'll say wait for an amount of time, then broadcaster listener. I can hook up my broadcaster, accept the value. Then create a timeout inside of here. We'll pass in the time. Then we can set up a listener for our timeout, where we ignore the value and pass the original value down to the listener.

[0:46] Instead of the value going directly into the listener, you're putting an amount of time in between it. If I use this right now, and I try and type something, we have an error, because listener is not a function.

[0:59] That's because we still have this Enter key trying to do something onkeypress, meaning, I pressed a key, but that never had a listener to go to. We'll save. Now I'll type something. You can see it kind of worked. Kind of worked. What's happening right now is every single keypress is creating a new create timeout, and it's not canceling the old one.

[1:27] We have to do this pattern of tracking the cancel. Cancel timeout. Assigning that to cancel timeout here. If that exists, we can go ahead and cancel the previous one. This is that pattern where if there's a timeout inflight, go ahead and cancel it, if another key comes through before the time has expired.

[1:52] Once I wait for a bit, I let go my keyboard, it should start printing out the message. Now let's also return the main cancellation. I'll return a function that would cancel timeout and cancel the main. We should have a nice system, where every time I pause for 500 milliseconds, something should come out. Nice await. Debounce. I'll wait again. Nice debounce.

[2:23] Then this time, we'll type, "Fast working for us. Nice debounce working for us." Let's extract this. That's a nice one to hold on to. Definitely can reuse that. Export, paste, and import. Wait for. Clear the ones we're not using. Hit save. We need to import createTimeout into our operators now. Let's import this from our broadcasters and now we're good to, good to go. Good to go. Yeah.
