Instructor: [0:00] When working with callbacks, time is always the hidden variable, meaning that if my broadcaster had a setTimeout and in the setTimeout, after one second it called this listener, and I hit Save here, you'll now see 2, 5 and then after one second, 6. That was this number, then plus this number, then plus this number after a delay of one second.

[0:27] Similarly, if inside of my broadcaster down here, I created a setTimeout, and I do this from the value*1000 to make it a second, and then I'll call the listener with the value, you'll now see one, and then two, and then three.

[0:52] You could even make it more complicated by still using the currentValue where you do currentValue again is += value, then passing that into here, currentValue and currentValue. Hitting save. Now you see 6, and 6, and 6.

[1:17] That's because this line had been run three times because these were invoked immediately, and currentValue value was trapped inside of this function as a closure and was updated before this function was called.

[1:30] These are all valid scenarios where your broadcaster could be timeouts, intervals, button clicks, input events, WebSockets, anything that takes a callback and pushes values into it.

[1:44] Then your operators, the key is giving them a good name, whether it's delay, buffer, state, or something that tries to describe what's going on inside. Code is never great at expressing the future. It is great to be able to capture functions that define the future inside of operators, where you could have this function capture this logic.

[2:04] If I duplicate this, change this to timeoutByValue, and set it back to what we had before, where these are the values, then I have the option of swapping out this operator for timeoutByValue, which is an operator, and getting 1, 2, and 3, or I could swap out my original operator, and now get 6, 6, and 6.

[2:37] Throughout the course, we'll be writing a lot of operators which will be able to capture asynchronous behaviors. We'll do our best to define the future in individual functions using closures and using callbacks.
