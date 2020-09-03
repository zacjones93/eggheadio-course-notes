Instructor: [0:00] If we look in the Network tab, we do notice we exposed a bug here. This is making two requests. This must mean we didn't handle a done scenario.

[0:10] If we look in this createTimeout, you'll notice we don't handle done, which means the listener's called twice with a value. The reason it's called twice is because in createTimeout, if I Command-click on that, you'll see it does that first call and then it passes in done.

[0:27] We need to handle that done scenario inside of our waitfor. That means we have an innerValue here, which if the innerValue = done, then we must guard against that. When I hit Save and I type STAR, you'll see only one request coming through.

[0:50] Another bug we have is if we delete all of this, it still makes a search for nothing. I'd also like to prevent it from making searches if I only type a single character, because that's just way too many results. Maybe even limit it to something like four characters.

[1:07] For that, before we construct the URL when we only have a name, we can filter on that name and only allow if the name.length is greater than three characters. We need to import filter from our operators. Import filter right there.

[1:28] Now I can type S and it won't do a search. I can type TA, it still doesn't do a search. I can type R, and now it finally makes that search for me. Everything else works as expected.
