John Lindquist: [0:00] A callback is when you -- let's set up an addEventListener("andClick") -- it's when you pass a function like this function in as an argument. If I console.log(andClick), come over here and click a few times, this right here is a callback.

[0:18] If I cut this out and give it a name, we'll call it callback, solid ame, paste that right there, and then pass in my callback this still works. Click, click, click because this function is being called by the internals of this.

[0:36] If we don't use the document addEventListener and instead, we just make another function, and this function takes a function, and inside that function, we call that function three times.

[0:51] If I call another function with my callback, hit Save, you'll see click, click, click because this function is being passed in as an argument. That makes this function right here, which means that this function is being called one, two, three times.

[1:11] That's the power of a callback is that you can define a behavior and then pass that into another function, which controls when that function is called. I could call it three times. I could wrap within a statement. I could use for loops or any scenario you want to think of. I have complete control over when this callback is called.
