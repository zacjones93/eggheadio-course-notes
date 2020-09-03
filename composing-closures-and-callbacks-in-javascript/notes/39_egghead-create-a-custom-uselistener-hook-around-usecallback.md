Instructor: [0:00] Creating a custom useListener hook for this useCallback CallbackListener is as simple as getting a function called useListener. Then inside of that function, I will copy all of this, cut, paste. I will copy this, cut, paste, and just return that from the function. Now, the onInput can be a useListener. I'll hit Save here.

[0:29] Now, when I type, you'll see that it bombs out on that second character. That's because useCallback also has that same list of dependencies that tell it when to change. Those dependencies can be added here. We'll pass them in if we need them, but we'll default them to an empty array. That should clear up that issue.

[0:49] Now, when I type something, it'll hang on to this listener, whereas if you don't pass in these dependencies, it will define that listener on the first character. You see it works, but then it bombs out on the second because on line 22, listener is not a function. That's this line. Making sure you're tracking those dependencies will keep this from being reset.

[1:12] Now with this all set up, we can go ahead and extract the store broadcasters. We'll export and paste it down here. Make sure to bring in useCallback. Then inside our index.js, we'll import useListener. Delete the stuff we're not using. I can remove all of the main React hooks because we're not using any of those right now.

[1:40] Then I'm going to move React up to the top. Up here, paste that there, clean up some blank space, add a line of white space there, hit save, and now we're ready to build something cool.
