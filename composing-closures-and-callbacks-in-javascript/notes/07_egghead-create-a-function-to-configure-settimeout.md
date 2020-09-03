Instructor: [0:00] When you create a setTimeout, you can pass in a function and the time that elapses before that function runs. In the body of the function, you say what you want to happen. We will console logout done. Once I hit Save, after one second, you see done up here in the console.

[0:22] To gain more control of this, we're going to look at the pieces you can extract out and control. Say, for example, the time, the function that gets called, and even the fact that setTimeout gets called immediately is something we can control.

[0:36] We do that by putting all of this inside of a function. We'll create a function called createTimeout. This will start as just a function. Inside of the body, you can grab the timeout and paste it inside of there. When I hit save, you won't see done up here because we have not called the function.

[0:57] We would need to invoke createTimeout, then hit save. Then after one second, you'll see done up here. The first piece I want to extract is this one second here. I'll cut that out. I'll call it time. I'll move it up into our arguments, call this time. Now we can customize in here how long the timeout will take. I'll hit save.

[1:16] Now this will run after one second. If I make this a much lower value, like 100, I'll hit save, and it runs in a 10th of a second. Now we're back to the same problem we had at the beginning, is that once we invoke this function, this is being run immediately.

[1:31] The solution, as we did before, is to wrap all of this inside of a function. We can do that by putting an arrow function right here. Now when I hit save, nothing runs, because this is now returning a function. We need to assign something, like let timeout equals, and then invoke that. We'll invoke timeout.

[1:53] Now, when I hit save, you see done appears after that quick 10th of a second. Let's delete this. I'm going to rename this to one second, and change this back to a full second. You can see if I duplicate this a few times, I can make a function that supports two seconds, one that supports three seconds.

[2:12] I call this two seconds. Call this one three seconds. Now I can call one second, two seconds, and three seconds. I'll hit save. You'll see done after one second, after two seconds, and after three seconds, which introduces a new problem.

[2:28] That's that this behavior is stuck inside of this function. There's no current way to change the behavior for what would happen after one second, or what would happen after two seconds, or three. We can change that by selecting all of this, cutting it out. I'll just name this callback.

[2:43] This callback can be passed in right here. Meaning, if I put callback here, the function that I cut out of here can now be pasted here, here, and here. After one second, I could have it say one. After two seconds, have it say two. After three seconds, have it say three. When I hit save, you'll see one, two, and three.
