Instructor: [0:00] On the topic of making too many network requests, let's explore some ideas for caching. When we talk about caching, we're talking about mapping a key -- in our case, it could be this URL -- to the result of this data, which is this result here.

[0:15] All of that happens inside of this map broadcaster. Let's copy that in. I'm going to grab from operators -- look for mapBroadcaster. I'm going to copy this and bring it over, back into my index file, paste it right here. I'm going to name this one mapBroadcasterCache and name this mapBroadcasterCache as well.

[0:41] What we're going to do is set up a cache in here, so call this cache, and create a new map. The way this is currently set up, we have access to the key, but we don't have access to the resulting value. I need to create a new listener in here. We'll say newValue and then listener with that new value. This is the same as before.

[1:07] Before that happens, I can use my cache to set the value that comes through to the newValue. This would be the URL and this would be the response from getURL. Let's go ahead and check that out. I'll console log out a cache, then in my console, I'll type in STAR. You can see we have a map with one value that has mapped the URL to that response.

[1:34] We just have to prevent this from being called if the cache already has this newValue. I can go ahead and check here, if cache has value, then we can invoke the listener with cache.getValue. We just return because we just want to skip all of this. We don't even want to create this new broadcaster.

[1:58] I'll hit Save here, I'll type in STAR, you'll see it does our network request right here and it sets the cache. I'm going to delete one character and then type R again. You'll see it did not do anything here. The network did not make another request.

[2:20] If I come in and type an S, it will make another request. You can see that in the network, it searched for stars. My console, it added to my map. I have two keys in there now. If I delete one, the results change back to the cached result. If I type in the S again, it changes to the cached version of that stars key.

[2:44] Looking into our Network tab, you'll see there's only two requests, the first one for star, the second one for stars. No matter how many times I delete the S or add the S, it doesn't make a new request until I type something new like star site. In the console, you'll see the new request.
