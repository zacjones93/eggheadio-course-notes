Instructor: [0:00] Let's move our operators we created over to our operators file. We'll cut those and paste them down here, make sure to export both of them.

[0:14] Let's start on a game of Hangman. I'm going to delete our buttons and create an input for our text. I can go ahead and delete all of this and grab our input. The selector is just the ID of input. We want the input event. We're also going to want the event.target.value each time input fires. We can call this our input value.

[0:47] We'll need to import map from our operators. Grab map from operators and then we can check our input value, we'll just console.log. Now, anything that I type should show up in the console.

[1:06] I've seen this enough that I'm going to extract that as an operator. I'm going to call it targetValue. Let's say we'll import this, we'll go into our operators file, and scroll to the bottom, and we'll export. Let targetValue just equals what we cut out. I'll hit Save and we are back in business.

[1:32] Anytime you see an operator like this reused a few times, just feel free to cut it out, give it a name, and then you can reuse that wherever you want.

[1:41] We're also going to want to create a word. Let's import for...of, then we can for...of on the word of honeycomb. Seems like a good word for Hangman. We'll call this ourWord. If we check out ourWord, we'll see that we get each of the letters and then the done symbol.

[2:01] The logic we're going for is that once you type something into the input, this will give us a value to check against. We want to check the word, we'll check each letter, then we can check to see if the letter is in the value. We can say if value includes letter. If it does, we'll go ahead and console log the letter for now.

[2:28] If I type in here, I'll type an H. You can see it logs out the H and errors on the done symbol. If I type an A, you'll see it types the H, but ignores the A. If I type an O, you'll see we get an H, no A, and then two Os or this O and this O.

[2:50] If the letter doesn't match the value, let's console logout an *. Since the end result we want is something like say, we only typed in O, *O, and this, then O, something like that. If I come up here and I type an O, you'll see that we have each of the values and then the done symbol, which we're not handling yet.

[3:15] Let's go ahead and group these together. If I just have a string, we'll call it result. Each of the letters, I'll say result += letter or result += *. Once this is done going through this, if letter is done and make sure to import done, then, we can console.log out the result.

[3:43] I'll hit save, I can start typing in here, I'll type an H, an A, an O and you can see this is mostly working. We're still running into the problem of the symbol being pushed out. We have to guard against that case. We'll return before done can make it down into this logic. Hitting save again, now we can start typing H, A, O, then just the rest of honeycomb.

[4:09] This is where we want to get to. We want to refactor all of this into reusable functions. Something that's new to us is this idea where we have logic based on the value coming from this outside broadcaster and a letter coming from this broadcaster on the inside.

[4:29] The operator we create for this is going to have to take into account both of these things and then wrap around this word broadcaster. There's something from the inside of the word broadcaster and something from the outside of the word broadcaster, which will have to modify its behavior. I'm going to comment this out, just so this doesn't show us results and start building this up.

[4:51] First, we want our input value. Because you see this value here coming from the input value, this usually indicates something like a map where you would take the value and then return something else, value +1 or whatever the transformation would be we're mapping to this broadcaster.

[5:11] If I tried to say, take that value and map to word and then console.log this, you're going to see that we're going to get functions out. Meaning, that it's returning this broadcaster, but it's not passing the listener to it. Let's set up something called a map broadcaster.

[5:32] This can take our transform function, which would be this function right here. Then it takes a broadcaster and a listener, because it's an operator. We can wire these pieces together by saying, take the broadcaster any time a value comes through, so this should look like this right here.

[5:53] We want to take the transform, which is this function, which will return a new broadcaster. We want to pass the value in. This essentially creates a broadcaster. That actually makes more sense for a function name. We'll call this createBroadcaster.

[6:12] Now that I have a new broadcaster, I can tell that new broadcaster to start listening. Now if instead of map, I use our map broadcaster. Hit Save here. Once I type a value, I'll hit H, you'll see it's outputting all the letters, because it hooked this, which is this up here, to our listener.

[6:36] Now we have some work to do to get all of this logic into this listener. Again, we can think of map here. I'm going to wrap this for some more space. We can think that I want to map this word, the value's coming out of this word, so that H-O-N-E-Y and on. These letters, I want to bring in this logic here, if value includes letter.

[7:02] I'm going to copy that and paste it right here. Because this is simple enough, I'm going to use a ternary. I'll say if that's true, return the letter. If it's false, return an asterisk. Then make sure to return this entire thing. I'll hit save here. Once I start typing H, you'll see H and eight asterisks, and O-N-E-Y. You'll see that this is working appropriately.

[7:26] Let's do a little formatting to make this more readable here. When you see a function being called inside of an operator, that means that I can move this to the next step or into another function that can compose with this function. I'm going to do that by cutting this out and wrapping all of this. This will be a broadcaster.

[7:47] I'll use our map broadcaster out here, where this is returning an operator. This can map normally, since it's returning that operator. That operator can be passed into map broadcaster. Then we can apply our operator to our word. If I hit save here, and I start typing H-O-N, you can see we're back to the same behavior.

[8:13] Something you might want to do here is take all of this, cut that out, and call this something like Hangman logic. Hit Paste here. Then we can just drop our Hangman logic inside of our map. I'm going to change my formatting a little bit so it doesn't keep running over. This is in our print with settings.

[8:37] Let's try 60. Go back here. Hit Save. There we go. Now things don't span across so many characters. We're still working here. If we want, we can even extract this, like we did with our target value, into a new operator. We'll call this APPLY operator.

[8:56] This will take our broadcaster that we want to apply our operator to, and then it can return all that other stuff. I can take this broadcaster, copy it, and paste it in here. Then I can use APPLY operator like this, APPLY operator, pass in word. Hit Save here. We're still back to where we were.

[9:18] Let's group these into some operators. We'll call this Hangman and pipe. We can pipe this one first. Let's map in our Hangman logic, and then map this one. Then it applies that operator from the logic. There's some extra parens here. I can say Hangman on the inputValue. We're still in business. Now we could write a simple operator which can live in this last step.

[9:51] This won't require any configuration. We can say this is a function that takes a broadcaster and it takes a listener. When our broadcaster broadcasts a value, we'll want to append it to a result string.

[10:07] I can say result += value. If the value is done, then fire off the listener with results and guard against doing more appending. We can reset the result to an empty string, hit Save here. Once I start typing HONEY, you can see it's concatenating to that string for us.

[10:34] If I just take all of this, cut that out, we'll give this a name of stringConcat(), just paste that there, and then put that function in here. Now, the entirety of our Hangman game is expressed right here. The logic is extracted right here.

[10:55] If you look at the after and the way that this reads, take the input and apply some Hangman to it. Hangman means to map the Hangman logic with these values and apply what comes out of that logic to a word and then concatenate it. You compare that to the way that our original version reads.

[11:15] We have an input value, broadcasting values, and a word nested inside of that, and then some concatenation. If it matches or if it's done, you can see that in the new version, I can easily swap out various versions of logic if I want this to be Hangman logic, too. Instead of an *, it does a $ sign and I can drop that in here.

[11:38] When I type in this, it does $ signs or we could get rid of this and still do one letter at a time or write a function that puts all the letters in array. We've broken things down into smaller pieces, which gives us more control.

[11:54] Especially, if we start getting into things like debouncing the input or something like validating against server, then breaking these all into smaller pieces makes a lot of sense.
