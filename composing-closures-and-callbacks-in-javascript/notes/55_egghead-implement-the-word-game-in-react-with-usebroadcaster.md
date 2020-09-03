Instructor: [0:00] I'm going to move over all of the operators we've created. Cut this out and move them into our operators. I'll paste them at the bottom down here. We'll make sure they're all exported, export, export, export. That looks good. We'll switch back over and run an organizeImports command to clean those up.

[0:26] Let's build out our game. Just going to delete all of the book search stuff. We're down to just this. A good starting point would be using a broadcaster to capture the input value. We'll start with an empty string and call this the result and then put the results right here.

[0:47] Once I hit Save and start typing, I'm going to zoom in on this a bit. We should be in business here. It looks like there's more operators we can get rid of. I'll run that organizeImports again.

[1:02] Our game consists of...We'll say our game is a pipe. Let's import that from lodash/fp. We'll import pipe. The steps were to take the value coming from the input and map it. We'll map this to a different broadcaster. This was our value. We wanted to map that to a for...of on Honeycomb.

[1:28] Let's make sure an import for...of. Hit Save here. Make sure an import map broadcaster. Now if I wrap my game around my input, and then type something, I'll type HONEY, you'll see that B always comes through. That's because we want to add our String.concat. Right now, it's just getting the very last letter. Make sure and import that, so String.concat.

[1:56] We'll do HONEY. This looks good. It's pushing out the entire word. It's just that now on this one, we need to map using our map operator. We'll map to see if the letter coming through is included in so value includes letter. If that's true, we'll return the letter. If it's not, an *. Hit Save there.

[2:22] Now I can type HONEYCOMB. We have all of our pieces in place. We have values coming from our input being pushed through here, then those values go into our game. That value is here. That's been remapped to a broadcaster, which is going to loop through every letter and check if that letter's in the value.

[2:47] If the letter's in the value, it returns a letter. If not, *, and then it concatenates that string altogether.
