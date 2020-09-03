John Lindquist: [0:00] While if...else works, I do consider there to be another better way. I'm going to revert by checking out to back before the if...else. We're just at the filter operator again.

[0:13] If I've set up this entire line of logic, and I set up a second broadcaster, I'll call this inputToClearSearch. This will look pretty simple. I'll just say filter the name when the name length is less than four characters. Then if that's true, we'll go ahead and map the name just to an empty array, and then we'll hook that into our inputValueUseListener callback.

[0:44] Now we have two broadcasters, each with a distinct responsibility. One to do the search and one to clear the search, so you have a function called merge which can take two broadcasters.

[0:56] We'll put in inputToBookSearch and inputToClearSearch. Make sure I import merge. That's in our broadcasters, since it takes two broadcasters and returns a single one.

[1:11] Now we'll go ahead and hit Save here. I'll start typing STAR. You can see that nothing happens. If I put into my empty array something like title Hello, and try it again, you'll see if I type S, that Hello shows up. This ClearSearch is working. It's this BookSearch which isn't.

[1:33] The reason for that is in our useListener, if we navigate to that, you can see we have this single assignment of a listener. When I pass in ClearSearch, that hijacks that single listener. Instead, what we can do is set up listeners as an array. Say, listeners push value. Now each time a function comes through, it pushes that on to my listeners.

[1:59] Then listeners, for each, take that listener and then invoke it with this value. Now when I hit Save here, I'll type STAR. You'll see it does that search. If I remove one character, I'll go back to my ClearSearch. If I fix and clear this out, so it's just back to clear, hit Save again. I can type STAR, delete a character and clear the search.

[2:26] Instead of thinking of these two things as conditions, you can think of them as both going through the broadcaster. This one pushes out an array of books and this one pushes out just an empty array. You also get the benefit of specifying the conditions where it pushes values out.

[2:42] For example, I could clear only when it's less than two characters. If I hit Save here and type in STAR, I'll do the search. I'll delete one character, it doesn't clear. I'll delete another, no clear. Once I delete this one, it clears out.

[2:58] This didn't have to be an if...else. You can define individual conditions for when each of these fires using filters.
