John Lindquist: [0:00] When designing your functions, you have complete control over how you want them to look. It's often good to start out with the API you want and then build out functions that can reorder and manage arguments for you.

[0:12] Say, I want myZip to take two broadcasters. We'll do our createInterval at 100 again, then a for...of of myZip. I want that to return a function where I can pass in my operators. It reads more like, "Here's the thing pushing out events, intervals, and for...of combined into zip and then here are the things that happen after taking a letter, filtering, appending, and lowercasing."

[0:45] Defining myZip would be simply let myZip and then the two broadcasters, so broadcasterOne and broadcasterTwo. This one is here and this one is here. This returns a function, which takes a number of operators. This returns our original zip with the original API, so broadcasterOne, broadcasterTwo. We wrap this with a piped version of our operators. I'll hit Save. Now myZip should behave the same way we had our original zip behaving.

[1:27] This approach expresses what this is doing in the browser a bit better, broadcasting stuff and then walking through steps. Whereas if I change this back to our original zip, and then I wrap this with the operators...We need to delete this. Hit Save. This expresses better what the functions are doing. Zip is returning a broadcaster, and the operators are wrapping around the broadcaster.

[1:54] Because this is educational content, I'm going to stick with the approach that expresses what the functions are doing. I'll leave this as a challenge to you as you're writing your code out, to express how best this would reflect what's happening in the browser.
