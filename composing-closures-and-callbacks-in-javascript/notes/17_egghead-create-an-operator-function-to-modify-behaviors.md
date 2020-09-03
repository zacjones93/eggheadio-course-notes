John Lindquist: [0:00] I'd like to create a typing behavior where we take a string and then add these values to the string. Instead of just logging out the value, we'll log out the string += the letter that comes through. That's the second one in the array. I'll hit Save and you'll see a typing behavior there.

[0:20] Instead of putting the behavior inside of our final callback, I'd like this to be a reusable behavior, which I could wrap around any of my broadcasters.

[0:29] To start with, let's take the broadcasters we've created. I'll cut them and paste them into our broadcasters file, make sure that we export everything. Export our zip and our for...of. We can import them here, import for...of.

[0:47] Now, done is not defined. Let's move done over as well. Go to the top here, we'll paste done here. Make sure to export it. Also, make sure to import it, so it's available in both files. Clean up some empty lines and we're back to where we were.

[1:04] Let's take this behavior and extract it into something reusable. So far, we've been using broadcasters where those are functions that take a listener, so createTimeout, this, this. You can see all of these took listeners as their final argument.

[1:21] Because we follow that pattern, we can now follow a new pattern. We'll curry a function that can take both a broadcaster and a listener. This is the function, and this is the function being passed to this. This will give us a chance in here to change a behavior.

[1:40] I'm going to name this modify and I can wrap modify around any broadcaster. Let's wrap it around this zip right here. Zip is creating a broadcaster, which is passed here. This listener is coming from right here because that's what's passed into zip, which is now passed into modify. This function is this and this function is this.

[2:11] Now we have a chance to change what those do. The default is just if we return a broadcaster, it takes a listener. You'll see the exact same behavior because we didn't do anything other than just call broadcaster with listener. That's what this is doing, it's calling our broadcaster with a listener.

[2:35] We want to bring up this string, which I can paste here, and also this behavior of appending to a string. We want to put that inside of a new listener.

[2:46] Our listeners have been functions that take a value. That's exactly what we're going to do here. I can just copy and paste this. Copy, paste. Now this is a new listener. Instead of console.logging where these happen, what we want to do is use the listener that we passed in.

[3:06] We'll take the listener, and here we'll paste and define that behavior of string += value, and grabbing the letter. Then done is listener, and passing in done. Once I save here, we don't have anything, because we're no longer logging anything out. All we need to do is take this value, place it down into our console.log, hit Save. You'll see, we've now extracted that behavior, and we're back to where we were.

[3:39] This modify function, if you look at it without the string and without this custom behavior, will serve as a template for any behavior that we want to create. Any function we create where we pass in a broadcaster and a listener, we can then override the behavior by returning the broadcaster with a new listener, taking those values, and doing something different with them.

[4:05] This can include capturing variables, delaying things in time, only allowing certain values, or mapping to different values. We can go over all of those scenarios.

[4:15] We'll restore this to where it was. Hit Save. Double check that we can still shut it down. Hit Save. It looks like we're good.
