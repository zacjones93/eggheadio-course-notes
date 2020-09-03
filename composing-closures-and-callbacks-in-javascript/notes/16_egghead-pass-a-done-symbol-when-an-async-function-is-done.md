John Lindquist: [0:00] In our zip, we have a createInterval pushing out every 10th of a second. If we check that buffer, which is this buffer(1), we'll console.log(buffer(1)). I'll hit Save. You'll see that after we stop receiving the string, the buffer keeps on growing and growing and growing. That's bad.

[0:21] That's because buffer(2) is that iterable using the for...of we're just passing in "Hello, John." After it's reached that N, this is done. You can see after it's looped through everything in iterable, it's never going to call the listener again.

[0:38] The iterator protocol for arrays, and strings, and similar has a next method, which is roughly similar to our listener. They pass in objects with values and a key of done, which is either true or false. We're not passing in objects. We're just passing in the value itself. Once we're done, we can just pass in a done.

[1:00] To make sure this is unique, I'm going to take this and put it inside of a symbol. Symbols will guarantee unique values. If I say done as a symbol of done, then when I pass done into a listener, it'll be much easier to check for this.

[1:16] If you'd like your library to match up with the iterator protocol, so that you could use your broadcasters and functions with for...of loops, that's a good challenge to take on your own, but that's not our goal here. After this for...of loop has run its course, we should get a done. If we check our demo, you'll see the last thing that comes through is done.

[1:36] Let's change it back so we get both of the values in the array, just so you can compare the values coming in through the interval and the values coming in through the string. By showing both of these values, we expose the problem that we are done after this. We received another value of 11 from our interval, even though we successfully received done here.

[1:57] That means we have to stop after our listener to make sure it doesn't come through again and push in any more values. We can do that by checking our buffer. Since we're using shift, we can check to see if the value at position  is equal to done on either buffer(1) or on buffer(2). If they are done, we need to shut down this entire thing.

[2:19] We already have a function to shut down everything. That's down here. What I want to do is give this function a name. I need to make sure that that name exists at the top. We'll call this cancelBoth(). I'll assign it after both cancelOne and cancelTwo are defined. Then I can return cancelBoth, so we can still cancel it on our own.

[2:45] I can bring cancelBoth into here to shut everything down. Now when I run this, you'll see that we never get that done symbol, and the interval is shut off right after we hit 10. It'll never push out an 11.

[3:00] Right before we cancel, I do want to send down a done, just in case we have something downstream that's listening for some dones. When we do this, you'll see we get a symbol done, which we can check against, but we're still preventing the interval from sending out an 11.

[3:18] I'll need this little block of code in both the buffers here. I'll take this and paste it down here because we're not sure when we use our code, which of these is going to come first. It might look like this, might look like this, or may have other things in there. I'll hit Save here. You can see this is behaving like expected.

[3:38] You'll want to handle the value in your final callback, if value is done, probably want to do something else. In our case, we're just going to console.log out("Shutting down"), and then return so that it never gets to logging out done down here.

[3:58] You can see all the values came through, but then once it was done, we're doing some different behavior and adding in a return to stop us from getting to the default behavior.

[4:08] To check, let's make sure that our cancel type greeting still works. That's good. Nothing ever came through. We'll comment it out again. Everything's working great.
