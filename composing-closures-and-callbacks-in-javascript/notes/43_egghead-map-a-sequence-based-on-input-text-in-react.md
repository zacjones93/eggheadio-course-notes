John Lindquist: [0:00] Because we have this broadcaster which we used before, we just put that before down in here, this used to just be broadcaster and it said, "Hi, my name is John," I can combine these things. I'll undo that. Combine this, because the thing coming through here now is the value from the text built.

[0:21] If I change this into a function which accepts a message and make sure to switch on that message, I can now use our mapBroadcaster operator we set up before and map that to the function we created. Let's call this messageSequence and we'll pass that in here, messageSequence, then wrap that around this.

[0:52] When I hit Save here, looks like I haven't imported mapBroadcaster from my operators, so mapBroadcaster, hit Save. When I type something, hit Enter, it'll say, type something. If I type, "Hi, mom," it says, Hi, mom. If I type, "How are you today?" it responds with How are you today?

[1:21] One thing I am going to do, because this got a little busy here, I'm going to bring in pipe from lodash, so lodash/fp, import pipe. Then we can define our...Let's call it inputToMessage or something and say that's a pipe. You can bring these steps in. Allow when paste. Then after that, map the broadcaster, cut and paste. This all goes around inputValue. With all of that gone, I can just say inputToMessage. Now this makes a little more sense. Enter.

[2:08] To finish this up, I'm going to just extract this into my operators, paste that there. Go ahead and export it and import from operators. I'll delete previous message. That's looking pretty good here, but I want to go back to my allow when, and make sure I return a function to cancel things. This can be mainCancel. This can be the cancelAllow. Then we can cancel both of these if the situation arises.

[2:45] The final note here is that these are functions to create broadcasters which are specific to our app. I don't think I'd extract these into broadcasters, but I may move them into a file for application-specific utilities.

[2:59] Another one I see in here is this, is something I might use a bit. I'd define this as let filterByKey, and then allow myself to pass in a key. Then paste in what we had before and say key there. That way, it could use this as a filterByKey and pass in enter there. Hit Save. Now I have a filterByKey operator, which I can extract to operators.

[3:37] I'll paste that in here and export that. This goes to show that many operators are just other operators based on filter and map. Don't worry so much about doing this every single time if you just want to build some utilities around mapping and filtering. It's a very, very common scenario. I'm going to export filterByKey. I think this demo is done here.
