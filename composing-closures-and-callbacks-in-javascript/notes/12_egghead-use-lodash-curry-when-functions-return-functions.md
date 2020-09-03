John Lindquist: [0:00] Let's npm install lodash and then we can import curry from lodash. This curry function is going to enable us to remove some of these intermediate arrows, which will make these look like functions with multiple arguments, rather than a function with a single argument, returning another function with a single argument, returning another function with a single argument.

[0:27] We can wrap all these arguments with parens, replace the arrow with a comma. We wrap this entire function with a call to curry. We'll do that on each of these. We'll wrap this. This is a comma and that's a comma. Let me wrap this and call curry. We'll do the same here. Remove the arrow, put in a comma, wrap this, and call curry.

[0:54] Now our code functions exactly the same. You'll see clickOrTick in there. I can click or tick and everything works just fine.

[1:02] These functions have function signatures that have the typical argument list. Because we're using curry, they're still treated as functions that can take a single argument and then return another function. addListener took a single argument and returned a function. Even though in addListener, you'll see, it looks like it requires three arguments.

[1:21] This curry function is a code-based way to split up arguments into functions that return arguments, which we had to do manually before. Curry will also allow us, in situations like this where we have addListener take a single argument and return another function which takes a single argument, we can now pass in two arguments.

[1:42] I'll take addButton click listener, I'll copy it here, paste it here. Now we no longer need this line, because curry enables us to pass in multiple arguments and still return a function that takes a single argument. Once I hit Save, you'll still see the ticks and the clicks coming through just fine.

[2:00] Let's also add curry down here to merge. We can combine the listener into that list of arguments of broadcasters, then select all of this, and wrap that with curry.

[2:11] Another added benefit is instead of these long method names, sometimes you might just want to write that in line here. I can say "merge addListener button click with a create interval one second." I'll hit Save. I will comment out cancelClickOrTick. Everything will work just fine.

[2:32] Then depending on your preferences, this might read better to you, or naming the functions might read better to you.
