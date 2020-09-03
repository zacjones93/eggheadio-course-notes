John Lindquist: [0:00] Instead of hardcoding to HONEYCOMB let's go ahead and load a random from an API. This API gives us an array with one word in it. Let's bring in getURL to load that word.

[0:11] I remember I accidentally pasted getURL into my operators, and this belongs in broadcasters. Let's paste it down here. Go ahead and import getURL, and we can say that a word is getURL, then grab this URL, paste it right there.

[0:40] If we want to see this in action, we can just set up a quick useBroadcaster, and this is a random word. Just drop it in here, random word, hit Save, and you'll see this random word up here. This is properly showing us a word, but it's actually an array with a single word in it. Let's add a map around this, where we take that first word from the array and return that.

[1:14] This will look the exact same. It's just that now instead of an array with a word being rendered correctly, it's a single word.

[1:21] Now we need to figure out the sequence of events. Instead of starting with an inputValue, we're going to start with the word. Then I need to switch over to the inputValue inside of my game logic. I need to bring this down into here, past the inputValue. Now the word is being passed into here. Right now, it's comparing the word to the word HONEYCOMB. Right now, that would look like this, because realness has NEY.

[1:53] Now we have to do the comparison between our word and the inputValue. We can try dropping the inputValue in here and see what happens. We'll type some random characters, but you see, nothing is working. That's because this still needs to be this word. This still needs to be a for...of around the word. That is each letter of the word comes through, we can compare that to the inputValue.

[2:24] Let's rename this, because this is the word now. This is the word. The value needs to come from a map broadcaster around our inputValue. We'll do inputValue, wrap that map broadcaster, and then move all of this stuff so the value comes through here and paste that in there.

[2:49] With that all set up, I'll try and type the word UROLOGISTS, but you'll see it mashed up the word ASTROBIOLOGISTS. It's really funny those words were that close to begin with, but if you look in the Network tab, it's because it made the word request twice, once for ASTROBIOLOGISTS and once for UROLOGISTS.

[3:14] That's because this broadcaster and this broadcaster each fired. Really, the only way to fix that is to have the word only load once and then share that value with any future listeners that want that value from the broadcaster.

[3:29] We'll write an operator to handle that. We'll just call this shareFirst. This is going to need to close over some things and then return a broadcaster and our listener because there'll be a couple of states going on in here.

[3:44] First, there's the state of isTheBroadcasterSetup. We'll set that defaults. There's the state of isTheSharedValueEvenReadyYet, because when I called broadcaster and get that value, there's a time before this is set up and there's a time after this is called, but it's still waiting for the value to return.

[4:05] Because if that sharedValue is ready, then we just want to take the listener passing the sharedValue, but also if this is set up, then we just want to return because we only want to call this once. After that setup, we want setup to be true to block this from happening.

[4:26] Once this listener is called, we'll go ahead and set the sharedValue to the value. If you think through, if I just pass the listener, the sharedValue here, there's that time in between when this broadcaster is set up, and then once the callback listener is called where other listeners might come in and try and get that sharedValue.

[4:49] That's the scenario we're facing here is if I wrap shareFirst around my word, so shareFirst and wrap that, you'll see it only calls the word once, so NONANTIGENIC. I can type NONANTIGENIC, but this useBroadcaster for the random word never got that word to display the answer underneath it.

[5:14] To invoke that listener as well, I can set up some listeners. These are the late listeners that come in after the callback has been invoked the first time. We'll go ahead and push those late listeners onto our listeners' array, and then we'll loop through the listeners in the callback with the forEach and take that listener and just call it with the sharedValue.

[5:44] Now we finally have the random word displayed here, and I can just type writable to match it. Essentially, this sharedValue, if I just return here, because sharedValue means everything is ready and done, all featured listeners just want this one value.

[6:00] This should still work. I type LYMPHS. SharedValue inside of this listener being assigned is essentially the way of saying everything is fired and done and ready. You don't need to run any async stuff anymore.

[6:15] There's also that weird phase in between where the network request is in-flight, so we need to let this run once. While that's in-flight, gather listeners that might be called once the response comes back.
