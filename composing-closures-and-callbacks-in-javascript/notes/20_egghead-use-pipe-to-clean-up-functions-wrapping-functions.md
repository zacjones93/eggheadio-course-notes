Instructor: [0:00] Now we really have to clean up this mess, and I promise it was intentional. When you start to see this this mess-up parens or functions inside of functions, inside of functions, inside of functions, that's when your brain should go to Compose.

[0:15] I'm going to switch over to lodash/fp and import a function called compose(). Compose is going to let me take a collection of functions and unwrap them from each other. If I say let operators, and I assign it to invoking compose, I can then take each function one by one cut and paste, cut and paste, and cut and paste, and cut and paste.

[0:52] We'll clean up this huge mess of missing parens, so paren and comma, paren and comma and paren and comma, then clean up all of these, clean up all of these. Now, I have this operators. I hit Save to format. I can take this operators, which is a function returned by composing all these functions. I can wrap that around my broadcaster.

[1:23] I hit Save here, and now we're back to where we were. The purpose of compose is to save you from that mess that we created before. This used to be a function inside of a function inside of a function inside of a function. Now, it's a simple list of functions.

[1:40] Remember, the only reason that this works is if you look at our operators, they each take a broadcaster. That means when we compose these, the result is a function called operators that takes a broadcaster. Each one of these individually could take a broadcaster, or when you compose them all together and return a new function, they can also take a broadcaster.

[2:09] The way compose works is you read the functions from bottom to top. The first step is to grab the letter from the array, then filter out commas, then append the letters, and then lowercase it.

[2:23] In the JavaScript community, the preference for working with asynchronous composition is using a function called pipe(). We bring in pipe. What that does is it lets us to order these in a way that it reads from top to bottom, so the first step being take that letter out, filter out commas, append them together, then lowercase.

[2:47] If I hit Save, this is the exact same thing. The only thing that changed is the order we pass in the functions. Conceptually, we're still unwrapping a function, which was inside of a function, which was inside of a function, which was inside of a function. All of these individually can take a broadcaster. When we group them together, it gives us a new function, which can still take a broadcaster.

[3:09] It's just the difference between pipe and compose is the order you pass these in. The asynchronous mindset is usually reading these steps, step one, step two, step three, step four. Whereas, often with the synchronous mindset, you're reading this as a function inside of a function, inside of a function, inside of a function, so it makes sense to do it the other way.

[3:29] Based on your preference, you can do it either way. For now, we will leave it as a pipe function.
