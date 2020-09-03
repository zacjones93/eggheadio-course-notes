Instructor: [0:00] Let's show this pattern one more time with setInterval for a repetition sake. setInterval takes a callback and then an amount of time. We'll say one second and then it returns an id, which we can use to clear the interval, so we pass in that id.

[0:18] If we make a function called createInterval() and we'll want the time and a listener, then we can write time, listener and then cut this here, paste it here. Now we can return a function that will call clearInterval.

[0:36] We'll take these pieces out. This is time, we'll copy and paste. Then listener is here, we'll copy and paste that right here. We can use createInterval, we'll pass in one second. We can call this oneSecond. We can say, "Every second, just log out Hello." I'll hit Save, and you'll see Hello start logging out every second.

[1:02] With this in place, we could do createInterval every two seconds. We'll call this twoSeconds. Every two seconds, we'll console.log("2"). Let's replace this Hello with a 1. You'll see a 1 every one second and a 2 every two seconds.

[1:20] We can show off how we can cancel oneSecond by invoking this cancelOneSecond() function before this listener is called. Hit Save here, and you won't see 1, but you will see 2.

[1:35] The pattern in all these functions we created is to find the pieces that we can pull out. createInterval had time, and listener, addListener had a selector, an event type, and a listener. The timeout had time and a listener. Let's refactor that so it's listener, to be consistent. You can use the words callback and listener fairly interchangeably.

[1:55] For consistency, each of these return a way to cancel or tear down the asynchronous thing planned for the future.
