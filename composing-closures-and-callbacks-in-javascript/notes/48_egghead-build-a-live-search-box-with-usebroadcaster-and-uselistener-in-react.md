John Lindquist: [0:00] With everything we've set up so far, let's look up this input text box through our getURL and build out some live search functionality. We'll do that with the Open Library API. Querying the Open Library API looks like this. Let me just leave that there for a second where this is the endpoint, and this is our query.

[0:23] I'd be looking for the book "Star Site." The results for this in this tab is an object that has docs on it. The docs are individual books. Each book has a key where you can find it on their website and a title which we can use to display the title.

[0:42] We'll use that title and that key. If you want you can use whatever information you want in here, but we use those two things to build out our search. Let's get rid of some demo stuff. We don't need a request GitHub anymore. We can delete those.

[1:02] We're no longer doing a message sequence. We can delete the message sequence stuff. We're not doing the profile anymore. We do have a text box, which triggers our onInput. We'll take the value of that, and then take that and pipe it through a waitFor, and then map that to a new broadcaster, which in our case, is going to be a getURL.

[1:26] To create the URL to get, we need to take the value from the input. This value here would be what's coming through this input over here. Because this is a name of a book, I'm going to call it name. Then we want to create the URL from that name. We'll take this, copy that there, paste it in here. Replace "Star Site" with ${name}.

[1:53] This way, we've created a URL which will get passed down into this map, which then will pass that into our getURL, so that this broadcaster here essentially gives us a value to switch over to this broadcaster.

[2:10] I also need to delete this, because we're not using that profile. Right now, I still need to import map. We'll do that, import map. Right now, we're in a state where it's waiting for input. When I type something like Star Site, you'll see it'll bomb out, because state is an object, not a value. That object it's getting is this one.

[2:34] We want to take these docs off of it and then map on those docs. I'm going to map the result of this to result.docs, so that this array here is what is set to this state.

[2:50] Let's go ahead and name this. We could name it docs. I'm going to name it books. While we're at it, I'm going to name this one inputToBookSearch. Then on my books, which I'm going to get out of that p tag, so books.map. We'll take each book and build up a div. In that div, there can be an a tag. That HREF can point to book.key. Inside there, it can be book.title.

[3:24] Hit Save here. I'll come back. It looks like map is bombing out right here because we didn't define an initial state. We'll fix that by passing in an empty array, because you can try and map on an empty array. We'll hit Save there. That fixes that error.

[3:42] Now I'll search for Star Site. You can see I get four results. Also, to make React happy, we need to add a key on anything we map like this. The key can be book.key. Those should be unique. Hit Save there. I'll type Star Site. It looks like these links right now would try and go to localhost if I clicked on it. That's not going to work.

[4:09] I have to go ahead and take this part of the URL, copy that, and add that into our HREF. Paste that there and append it here. That should do better. If I type Star Site and click on the first one, it should take me to the open library to the book I was looking for.

[4:31] Also, this can be a live search box. If I just type Star, and it'll give me a bunch of books based on Star. I continue typing for Stars. That'll fire off another request. Keep on typing, and then stop typing. It will show me only the books that match Star Site.
