John Lindquist: [0:00] Let's pull out our useBroadcaster hook. Before we do that, we don't want all of our states to start with Hi, so switch that over to null. I'll grab this, I'll cut it out, and I'm just going to add it to my broadcasters. We'll paste this at the bottom here, make sure to export it.

[0:20] We also have to make sure to import useState and useEffect. I'm just going to grab that from here, copy all that, go to my broadcasters, and paste that here. We don't need React. I can just import useBroadcaster from broadcasters. I hit Save and we're back in business.

[0:45] Let's change this to an input, so that we can react to some text that's coming through. On the input event of this, we're going to want to fire an onInput callback, or onInput listener. The way I can set this up is with useCallback, then bring this down here, and we'll say our onInput is a useCallback. Then we can define the callback we want triggered when this happens.

[1:19] Say, for example, I did this to the console.log("Hello"). Hit Save. Let's check this out. I'll just type a character, and you see Hello, because it's using that callback.

[1:32] We have to get a bit creative here, because we want this to be a broadcaster we can use in here, but we also want it to be a listener, which we can pass into here.

[1:44] We've seen similar patterns before in previous lessons, where I can set up a custom listener. I'll call this callbackListener, which takes a value, and then use that to call an original listener. We'll also set up a reference to that listener. The logic for us is that most of the time on input, we'll just receive values. We want to push the value into the listener.

[2:12] If I push onInput into here as a broadcaster, the value being passed into here is this...Let me scroll all the way down, is this setState, is being passed into the broadcaster. That's a function being passed in the broadcaster. The simplest logic we can use is say, if typeOfValue is function, then the listener is that value, meaning that this is the setState, so we want listener to be setState.

[2:50] We can just guard against this, we just wanted to pass the value to this function, which is now setState, so callbackListener just goes into here, so I can just add callbackListener. Right now, if we try and show off the state, and I type something, you'll see this bombs out because the thing being passed through here is one of React's events.

[3:18] Let's go ahead and bring in a map from our operators. I believe we set up a target value map. Yes, so we can just wrap around our own input target value, which is just mapping the event target value. Now when I hit Save, and I start typing, you can see letters coming from here are going out to there.

[3:46] Let's wrap this in a paragraph, just so it's on the next line. We can type "Hello."
