John Lindquist: [0:00] Rather than a list of broadcasters like this, it'd be much easier for us to just define a message and say it's, "Hello. My name is John." Turn it into an array and split on it, which means that we have an array that looks like this. We could map each of the values in the array to new broadcasters.

[0:22] The idea would look like mapSequence. Each word that comes through could create a new broadcaster. We can use our delayMessage on the word to create that new broadcaster. If I were to wrap this around a for...of of our message and then console.log that out, that's essentially the API we want. We have to define what mapSequence looks like.

[0:48] We'll define mapSequence here. This takes a function that creates a broadcaster. It takes the broadcaster, and the listener, and then hooks up the broadcaster, checks the value. Now we have to figure out how all these pieces fit together, our function, our listener, the values that come through, to create those broadcasters that wait for each other.

[1:11] The general idea is to create the broadcaster using the value. This would give us an inner broadcaster. Then hook that up to the listener. We'll work from there.

[1:21] Right now, we get all of the values we expected, but they all happened at the same time. Hello comes from our array. Then the done comes from our delayMessage, which passed in Hello and a done symbol after that delay happened. These all happened at the same time.

[1:39] What we want to do is take the value. Once it's done, then create the next broadcaster, which would push out this value. Once that's done, do the next one. These done symbols represent where we need to break these up. When you run into these scenarios where you're getting too much information too fast, you can always rely on a buffer being the answer.

[2:02] I'm going to push the values into the buffer when innerBroadcaster isn't defined. I'm going to go ahead and pull this up to here. Then do the assignment down here, and just say, if inner broadcaster, then I want to push the value into the buffer. If the innerBroadcaster doesn't exist, then we want to go ahead and create it.

[2:26] This should mean that we get our Hello and a done. The rest of the words are hiding inside of this buffer. That means in this listener, which is passed into the broadcaster, we need to access the values from the buffer. We've seen a scenario before where we set up this asynchronous recursion.

[2:44] I'm going to define an innerListener using that pattern. Call this an innerListener. It'll say this takes an innerValue. We can just hook up the listener to that innerValue, and it will be in the same spot. I can check if innerValue is done. Then I can get the value off of the front of the buffer, so we'll shift that off the front, and use that to create the next broadcaster in the list.

[3:14] This can be our innerBroadcaster now. We can hook up our innerBroadcaster to the innerListener, so it sets up that recursion where this goes back up to that same function. If I check the behavior now, you'll see, "Hello, my name is John," and then a bunch of undefines.

[3:41] Those undefines are coming from us trying to shift values off the buffer that might not be there, meaning that if the buffer has length or has values, then we should do this stuff. I'll hit Save here. You'll see, "Hello, my name is John." We don't get those undefines anymore. We're still not guarding against these dones coming through.

[4:10] If that innerValue is done, let's go ahead and guard against passing that done down to the listener. I'm going to go ahead and speed up this, so we don't have to wait as long. I'll hit Save here. Hello, my name is John. Now we're not getting the done value, even if the original broadcaster, this for...of message, is done.

[4:35] To check on that scenario, that done would have been pushed into the buffer. I can check if value is done, then just pass done down to the listener, and go ahead and guard against doing anything after that. When I hit Save here, you'll see, "Hello, my name is John," with done coming down at the appropriate time.

[4:56] It's important to note, there are many scenarios where you won't get this done. Say, for example, I used our input click and just mapped it to a "Hi," so I could say hardcode hi to our input click and pass that in here. When I click in here, I'll see Hi. If I keep on clicking, I'll click really fast four times, one, two, three, four. You'll see nothing comes through. That's because our innerBroadcaster is still left as defined, and still assigned from this latest time it was assigned.

[5:30] We need to go ahead. When the innerValue is done, just tell our innerBroadcaster, "You know what, you might not be reassigned, so we'll go ahead and set you to null."

[5:39] This way, by clicking here, you'll see Hi once. If I click four times, one, two, three, four, you'll see that four more values came through in a timely manner where I clicked really quickly, but they each waited a half a second in turn.

[5:55] If I click as quick as I can five times, one, two, three, four, five, you'll see those values are delayed as we define them.
