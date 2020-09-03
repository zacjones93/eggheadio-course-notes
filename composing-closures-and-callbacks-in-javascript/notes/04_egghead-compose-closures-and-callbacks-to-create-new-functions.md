Instructor: [0:00] When you think of composition, you can think of one function passing its value. Instead of log in, I'll return i++ to another function. We'll define a function called multiply(), which takes a value. This can just log out the value * 2.

[0:19] If you wanted these two functions to work in a chain where it calls this one and then this one, you define a callback here. So far, we've just been ignoring the event. This is a function that takes an event.

[0:33] We'll call our callback manually. We can't pass in the event, it doesn't matter. We're just ignoring it here anyway. This callback returns a value, so this value is i++. We can pass that value into multiply. There goes the value. If I click now, you see , 2, 4, 6 because it's incrementing one at a time and then multiplying it.

[0:59] You don't need to do this intermediary step of assigning a value to the result. You can just delete this, and then cut this out and paste it inside of here. The result of this is just going to be passed into this value here. If I hit Save now, I have the same result, click, click, click. This function is called and returns a result to this function, and then this one does that multiplying.

[1:26] This syntax currently is defining outer function. We could choose to pass that event into here. Then being called, and then this one's being called.

[1:35] There's utilities we can use to make this look a bit cleaner. The one we'll be using throughout the course is called pipe. We're going to import that from lodash/fp. I'll import pipe. Now, instead of this syntax, we can say pipe (callback, multiply). I'll hit Save. Now click, click, click, click. You see the same result.

[2:02] You can even extract this and give it a name, because this is just a function. If I give this a name of twosCallback, and just paste that there, and pass in our twosCallback, we're still in business. Click, click, click, click. Pipe is creating a function from two other functions.

[2:23] The close cousin of pipe is called compose. It works the exact same, except the arguments get flipped around. Compose would be multiply, then callback. This works, click, click click. The reason it's called this is because it more closely resembles our original function, which be event, then multiply around the callback and passing the event into the callback.

[2:55] Instead of doing this syntax, which works fine, click, click, click, and worrying about all these nested functions like this, composing allows you to list them out. Compose, which is (multiply, callback). Then the argument gets passed in, click, click, click.

[3:15] We're going to stick to using pipe, which takes the functions in a different order, because when thinking asynchronously, it makes more sense to think, "Well, the callback is called, and then multiply is called." We're sticking to this.

[3:31] Also, note that because this is a function, I can call it, use callback. I'll call it three times. Hit Save. You see it's called three times. Then it's also used, click, click, click, when I click. It's because it's passed in here as an argument that it's a callback. Otherwise, it's a function you can use whenever and wherever.

[3:50] Throughout the course, we will be revisiting pipe and reintroducing it in context. Throughout the course, keep in mind that we are writing functions that capture behaviors. This function captures an incremental behavior. This function captures a multiplying behavior. This function is also a closure, because it captures something outside of it, which gives us even more power.

[4:12] This course is going to be writing a lot of functions and giving a lot of examples in complex scenarios, where you can see the power of this, writing functions that are closures and callbacks, and combining them together to capture behaviors, and turn them into a reusable library.
