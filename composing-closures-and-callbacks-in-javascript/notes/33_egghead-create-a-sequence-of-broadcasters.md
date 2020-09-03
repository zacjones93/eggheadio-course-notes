John Lindquist: [0:00] Another great thing about defining when done happens is being able to set up a sequence of broadcasters. Let's comment this out for one second here. I'm going to set up a function that creates broadcasters called delayMessage(), which can pass in a message and then hard code that message to a createTimeout. We'll just put that at 500 ms.

[0:25] Let's make sure to import hard code. We can use delayMessage like so. We'll say delayMessage("Hello") and just log that out. Hit Save. We also need import createTimeout, createTimeout. After 500 ms or half a second, we get "Hello" and the done symbol.

[0:49] Because we got that done symbol, we can go ahead and chain or sequence a few of these together. Let's set up a broadcaster called sequence. This can take as many broadcasters as we want. Let's pass in a bunch of broadcasters, and then a listener, then set up a way to loop through the broadcasters, and fire off the next one once it hits done.

[1:14] Our first broadcaster comes from the start of the array. Broadcasters shift and get the first broadcaster. Then we can hook that up to a new listener here. That will push out values to the original listener, but if the value is done, then we're going to shift off the broadcasters again, paste that there, and then hook up this broadcaster to this listener.

[1:43] Essentially, what that means is we write broadcaster here. This listener we're going to pass in as this one. We got to extract this. We'll call this a sequence listener. I'll paste that. Now I can use my sequence listener both in here and in here, which sets up that little bit of asynchronous recursion we've seen before.

[2:07] I'm also going to toss in a return statement to prevent listener from pushing out done, so we only get the done value on the last step in the sequence. To use this sequence, I'm going to say sequence, and then pass in a bunch of delayed messages. We'll say delayMessage("Hello"), then do five of these. "My name is John." We'll console.log this out.

[2:36] You can see this prints out each message as it comes in. Looks like we also need to check if there's any broadcasters left. We can handle that in here. Value is done. We also have some broadcasters left if the array has any length. Hit Save again. We made it to the end.

[2:58] The beautiful thing about this compared to other solutions is that I can cancel this anytime I want. If I want to cancel that sequence, I have to make sure and set up each time I invoke the broadcaster a reference to the cancel. There's cancel. That's the cancel, and that's the cancel, and then return a function which captures the cancel.

[3:23] Be careful here, because if you return the cancel, then you're returning just this first assignment. You want to return a function that knows about the future assignments we'll be doing in here.

[3:33] I'm going to use our inputClick for this, and just say inputClick, call our cancel. I hit Save. At any point, I can click in here and stop the entire sequence. If I refresh, I can stop it anytime, click right then. I can try and stop it before it starts. I may have to give myself some more time. Hit Save there and click. That stopped before it starts. Again, I can stop at any point.

[4:08] When thinking about sequence, you do have to remember that this only works with things that are going to push out done. If I would have put a button click in here, I would have had to use a done if to be able to trigger the next things in the sequence since your add listener buttons don't push out dones unless you tell them to.
