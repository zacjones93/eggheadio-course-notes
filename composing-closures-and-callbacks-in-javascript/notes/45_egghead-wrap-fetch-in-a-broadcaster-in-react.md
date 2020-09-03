John Lindquist: [0:00] Debouncing is especially useful for fetching remote data. Let's build a broadcaster, which can grab my profile from the GitHub API. I'll grab this URL, paste that here, and then build a broadcaster, we'll just call this getURL, which takes an URL, then a listener.

[0:20] Then we can use fetch to fetch the URL. You'd probably think let's use async/await, because that's what everyone uses. Let's see how this plays out. I get the response like this, and then I get the JSON by awaiting the response JSON. Then I pass that to the listener.

[0:44] Then I could say getURL, grab this URL here, copy and paste, and then console.log that. Let's go back here. Looks like I have a regeneratorRuntime error. That must mean in my parcel configuration, so in my package.json, looks like I misspelled browsers list when I set this up.

[1:12] By default, this was targeting browsers that did not support async/await. I had a typo, without that s in there. This was just using the defaults. Once I fix that, now, it should target the latest Chrome version, and automatically work. We're back in business. It looks like when I get this URL, it logs out just fine, and I get the data back as expected.

[1:39] The problem here with using async/await arises when we try and cancel this. If I were to try and invoke cancel right now, even though I'm not returning anything, there's no return statement in there, and I hit Save, you'll see that cancel is not a function.

[1:58] If you're wondering what cancel is, I wrap this and console.log, you'll see that this is a promise. That means that anything being returned from an async function is by default a promise. From this function, I need to return something that cancels. I need to return a function that defines how to cancel. Even if I do that, you see, it's still a promise.

[2:28] For this broadcaster function, we cannot use async. We need to do the traditional way with thens. Fetch then. This is the response. Then response.json goes inside of here, so it'll return response.json. I have the JSON, which I can then pass to the listener.

[2:54] When I hit Save, you'll see here we have a function that could cancel. Also, everything still works. I could already move this getURL into...Let me copy this. I'll set up a new broadcaster called profile. Say, use broadcaster, and just paste in that getURL.

[3:17] Now, if I put my profile down here, I hit Save. Let's see. It's profile.login. Hit Save. I see that we do get an error, because right now, profile is null, meaning that before fetch fires and returns that object to our listener, profile's just null. That's the starting state.

[3:44] I could check if profile exists, and then do this, which now, finally, if I hit Save, should give me John Lindquist. This will do a check against it being null. Otherwise, it makes more sense to update our use broadcaster from our broadcasters.

[4:01] Meaning that we can define an initial value to pass into useState. If I say initial here, and default this to null, I could then pass initial in here. Then with my use broadcaster, I could say that for our needs right now, an object with a login that has an empty string. Then I could delete this check. Hit Save.

[4:26] I don't get an error now, because profile exists right here, and this login starts as an empty string.
