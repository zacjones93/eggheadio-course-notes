John Lindquist: [0:00] Throughout this course, you'll hear the words broadcaster and listener in almost every single lesson. I give them these names because listener is just a callback, meaning a function that you pass to something else.

[0:14] Our listeners will take values and do something with those values, usually console.logging them until we start building out UI later on. You can think of a listener as just a plain old function that you can pass to another function.

[0:28] That other function that we'll pass the listener to is a function we'll call broadcaster. This function takes a listener as a callback and then calls that listener in various ways. I could call it three times. I'll pass in the values 1, 2, and 3.

[0:47] Right now, nothing happens in our app until we actually call broadcaster and pass in the listener. Once I hit Save here, you'll see 1, 2, 3. The order is that we invoke broadcaster, which calls this function, with this listener function, which is this function. That listener comes through. We can call it with whatever values we'd like to pass into the listener.
