John Lindquist: [0:00] Let's create a file called broadcasters and move all of the functions we've created so far into that file. We'll select all, cut, and then paste over here, and then here, here, here, and here. We'll export these, so we can use these inside of our index.js.

[0:19] I would like to create a broadcaster that can group two values together while merge did an or behavior. Let's call this zip and do an add behavior. As it will take two broadcasters, a broadcasterOne and a broadcasterTwo and then return a function which takes a listener.

[0:38] We're going to follow the curry pattern. Let's import curry again from lodash. We can use curry to wrap all of this and move listener into the arguments. The way to think about this, if we're going to group two of these together, it means that our listener will return an array containing the value from the first broadcaster and the value from the second broadcaster.

[1:03] While the or behavior of merge looked like broadcasterOne, and just passing in the listener, and broadcasterTwo, and just passing in the listener. This time, we're going to capture the value that comes through the broadcaster and is passed to the listener.

[1:19] We're simply going to write a new listener, so we'll say value, and then do stuff here, and then pass a new value to the listener. If you were to compare this and this right now, they're doing the exact same thing. It's just that we're giving ourselves some room to do stuff before that value makes it to the listener.

[1:36] Whereas with this approach, there's no chance to intercept that value and do anything. We'll do that for both of these. In here, I'll pass in that new listener, do stuff, and then listen. Let's see what this looks like right now. If I zip together a addListener and VSCode, automatically imported that from broadcasters.

[1:56] AddListener button, click. A create interval of 1 second. I'm just going to format this a little bit, so these are our new lines. We'll call this clickAndTick. clickAndTick can take the value and console.log(value). Right now, when I hit Save, you'll see a bunch of undefined come through. I'll try and click. You'll see mouse events come through.

[2:25] Now, the undefined are coming from our broadcasters, because our interval, the listener, is not sending any values through. We might as well send something through. We'll just set up a value of i set to . Then our listener be inside of a function. Then we'll call it with i++.

[2:48] When I hit Save here, you'll see , 1, 2, 3, and a bunch of clicks. You'll see mouse events, 5, 6, 7. Again, the behavior of zip is that we want it to group together two values and send them both at the same time.

[3:04] Let's set up a buffer for both broadcasters. We'll call this bufferOne, which is an array. Then a bufferTwo, which is also an array. When a value comes into broadcasterOne, we'll add it to the buffer, push value.

[3:23] When it comes into broadcasterTwo, we'll add it to our bufferTwo, push a value. Then the logic in broadcasterOne is if bufferTwo has any length, meaning the array > , then inside of our listener, we can send an array of bufferOne.shift, which gives us the oldest value, and bufferTwo.shift. We'll get the oldest value off of each of the buffers.

[3:52] Then in broadcasterTwo, we'll do the same thing, but this time we'll check to see if bufferOne has any length. If it does, we use our listener to send an array. This will be this exact same line here. We'll just bring it down.

[4:06] Now when I hit Save here, broadcasterTwo is going to start buffering up some seconds, which won't be displayed until I start clicking. If I click really quickly five times, one, two, three, four, five, you'll see I get  through 4.

[4:18] I'll do five more quick clicks. One, two, three, four, five. One, two, three, four, five. One, two, three, four, five. Now I have more clicks than seconds, so my seconds catch up while there's still mouse events. My seconds are buffering waiting for more clicks. I'll click and create a buffer of clicks. Now my seconds will catch up with the clicks.

[4:40] This zip behavior is a way of using these two buffers together where this was buffering up clicks, this was buffering up seconds. If either of the buffers had values inside of it, they will be pushed out into a listener the next time an event came through.

[4:55] We do have to complete this by grabbing the cancelOne and the cancelTwo, and then returning a function. If I return a function which invokes cancelOne and cancelTwo, now I could cancel clickAndTick. I'll call that. I'll hit Save. You'll see that if I click, nothing happens.
