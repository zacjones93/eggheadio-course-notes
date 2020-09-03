Instructor: [0:00] It's also worth noting the value of a function called partial, which we can use to supply arguments one at a time and return functions that still need arguments. It comes close to being useful here.

[0:13] Let's say I comment out addListener. With window.addEventListener, which would typically look like this, I'll say copy, which tracks when I try and copy something from the page. Then you'd supply an eventListener.

[0:27] Instead, I could turn this into partial then wrap window eventListener. I want to apply copy and this will return a function that expects a listener, so by our definition, a broadcaster. I'll hit Save here and you'll see that cancel1 is not a function, meaning that this did not return a function that could cancel or remove the eventListener from the window.

[0:50] Let me refresh this. If I try and copy from the page, Command-C, you can see that it's firing a bunch of events. It's definitely good to be aware of, even though it doesn't quite meet our requirements of returning a function that can cancel this out.

[1:05] If I were to try and partial on a setInterval, so I'll say partial(setInterval), the signature of setInterval looks like setInterval, and then the callback, but in our situation, we need the callback to come last. We need to flip a callback and the amount of time which it would take.

[1:25] To do that, we could bring in another function, which is called flip. This can change the order of arguments. I'll say flip on the setInterval, and then pass in one second. Now we'll have two functions which are both really close. You'll see it's still ticking away, even though there's no way to stop it. This can still copy, even though there's no way to remove the event.

[1:48] As you're working with APIs, you don't have a lot of control over, and you want them to fit into your patterns, there are many helpful functions in Lodash that can help you manage applying individual arguments, changing the order of arguments, and other helpful utilities.
