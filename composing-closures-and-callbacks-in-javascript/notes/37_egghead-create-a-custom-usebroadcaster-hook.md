Instructor: [0:00] Let's create our own custom hook by taking all of this, cut this out. We can define a useBroadcaster() custom hook. This can take two arguments. One is the broadcaster. The other is the dependencies, which will default to an empty array.

[0:21] The insides of this function is just the pasted content of what we cut out down below. We just wrapped everything that was in there inside of this function. That means we can pull this out because this is now this broadcaster.

[0:36] We'll just cut that out, type in broadcaster, and we can pull this out because that's just our dependencies. Instead of the array, we'll type dependencies. We can use our useBroadcaster hook just by passing in a createInterval. We'll say one second.

[0:58] For us, it's going to return the state that I want to use down here. That means up here, we need to return the state that came from the useState hook. If I hit Save here, I have the exact same features and functionality. It's just that now, I have my own hook, or I can just pass in a broadcaster and get some state out.
