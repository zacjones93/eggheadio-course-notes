John Lindquist: [0:00] Before we can go any further, we have to fix a couple of bugs. The first one to point out is with createTimeout, which is in our broadcasters. If I set up a createTimeout, or oneSecond, I'll just call this 1. If I log out, what comes out of 1, hit Save here, you'll see absolutely nothing show up.

[0:22] That makes sense, because setTimeout doesn't pass anything to this function, so there's nothing to log out. Let's go ahead and import a hard code from our operators, so that we have a value that we can map it to. If I hard code "Hi," wrap that around createTimeout, and hit Save, you'll see we get a singular Hi, and then nothing else.

[0:47] That's concerning, because this is done, and we didn't get a done. We must have missed calling the listener with done. Let's go ahead and add that in. The first time through, we can say this just passes out null. We also need to pass in done, so that operators down the line can be notified.

[1:08] Hit Save there and now you see a Hi and a Hi, which means that hard code is overriding done with Hi. Done is a special value, which should always be allowed through in a hard code.

[1:20] Let's use our createOperator around this since createOperator handles the doneness of an operator. I mean, they make these into arguments. I'll go ahead and delete the arrow since this curries this. I'll hit Save here and now we should get Hi and done.

[1:37] The reason this is so important is if we want to try and make something that repeats, if I set up a repeat operator, this would take a broadcaster and a listener just like always. We'll invoke our broadcaster with a new listener. We would need to know and hear how to repeat or when to repeat. The answer to that question is we repeat when the value is done.

[2:04] What is repeating? In this sense, repeating is setting up the broadcaster to this listener, again. That means we need to take this listener and then get a reference to it up here. We'll call this repeatListener, paste it there, and go ahead and pass it down into here.

[2:24] Now I can say, if the value is done, I can copy and paste this and put it in there, essentially causing an asynchronous recursion inside of repeat. This is the first pass and then these are the future passes. We need to return, so done doesn't get passed to our listener because repeat will essentially never be done right now. We also need to call our listener with the value.

[2:49] Now if I take my repeat and wrap it around the broadcaster here, go ahead and hit repeat. Save here. It's like we didn't import done. We need done from broadcasters. Hit Save now. Now you should see Hi being called over and over again each second.

[3:11] While this may look like a glorified setInterval, since all it's doing is logging out Hi every second, think of repeat as something like restarting a game after a game is over, where you either won or you lost and you want to reset everything back to the beginning.

[3:24] The repeat operator can go ahead and capture everything it needs in this repeat listener, and then reconnect it to the broadcaster when it gets a done signal. Let's also clean up after ourselves. We'll need a cancel. The first cancel would be this one.

[3:41] If this is done, we can go ahead and cancel. Future cancels would be this one. Then make sure to return cancel. At any time, we could grab our cancel function, call cancel, and shut the entire thing down.
