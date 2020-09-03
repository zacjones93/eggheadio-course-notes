Instructor: [0:00] With our zip in place, let's set up a scenario where we can type out a letter every second. To do that, we need a way to handle iterables.

[0:08] An iterable is anything that can be put inside of a forof loop. This could be an array, or a string of some sort, or technically anything that has the symbol iterator in its internals. Understanding that anything that fits into a forof loop will work for us.

[0:29] We will call our broadcast creator here forof and we'll bring in curry and curry takes a function. The last argument is going to be a listener. The first argument can be our iterable. Inside of here, we can go for that i of iterable and then use our listener and pass in i. If I say, "forof hello", we'll call this hello and then pass hello a listener, where we take the value and log it out.

[1:02] In our console, you'll see H-E, two Ls, and an O. If this was an array of one, two, three, four, I'll hit save, you'll see one, two, three, and four logged out one line at a time.

[1:17] Now with our zip, we'll take our zip and zip together a create interval. We'll make it go fast, so a tenth of a second, and then a forof of, "Hello, John." I'll call this type greeting. Then type greeting will take our listener, which will take the value and just log it out.

[1:38] I'll hit save here. You'll see "Hello, John" being printed out. If we only want the letter, we can just grab the second value in the array.

[1:48] One thing to be aware of. If we try and cancel type greeting, you'll see that once we invoke this, I'll hit save, that cancel too is not a function because we didn't return anything from here. To be able to cancel this, meaning that we want to stop this before it runs, we'll put this inside of a setTimeout that runs after zero seconds. It just runs on the next tick.

[2:13] I can grab all of this, move it up inside the setTimeout, then grab the ID, and return the function that clears the timeout of ID. Now we can cancel an iterable before it runs by calling cancel type greeting so that never comes out. If I comment this, you'll see it types it out again.
