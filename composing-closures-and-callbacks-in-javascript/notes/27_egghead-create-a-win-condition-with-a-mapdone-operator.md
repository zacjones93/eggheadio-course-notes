Instructor: [0:00] Now that we can play Hangman, let's set up a win condition. If I take this broadcaster here and separate it from calling the listener, we're going to call this broadcaster play, so we can still just invoke that with the listener and play the game. I can also set up a win broadcaster based on play.

[0:21] Let's set up a win pipe. Essentially, what we need to do is check to see, so I'll bring in filter to check, to see if the string doesn't include any *. If I wrap play with my win pipe and then I can check to see if I win, we'll just was console.log("You win"). Let's save there. Looks like I need to import filter. We'll go ahead and do that.

[0:50] Now, if I type in HONEYCOMB, you'll see a "You win" pop up. All of these came from the broadcaster. The You win came from the win broadcaster.

[1:03] Unfortunately, if I type another letter, I still win. Let's go ahead and say that win is done once it meets this condition. I'm going to go ahead and set up a doneCondition operator. This can be the condition and the broadcaster and listener.

[1:22] Since I already have a filter operator, I can just invoke my filter operator based on the condition, then pass in the broadcaster. Now, this gives us the broadcaster, which will only push out values when the condition is met.

[1:36] If we set up a listener here, we can say listener with the value. If we swap out our filter for doneCondition, we're in the same state we were before. If I HONEYCOMB and win, we can still keep on winning by typing characters. We essentially just copy and pasted what we had down here up to this line.

[1:58] What I can do now is, instead of sending the value, I can send a doneDown, and set up a way to cancel this. I'll say cancel. After we're done, we'll go ahead and cancel. As always, I need to go ahead and return or cancel. I may have missed doing this in other operators as that wasn't the focus of previous lessons. We'll make sure you clean that up later.

[2:18] Now, when I type HONEYCOMB, I get my You win here. If I type another character, I no longer get You wins. I just keep on getting whatever is remaining here. I can't even win again if I delete characters and type HONEYCOMB again. I only still have this one win.

[2:35] It's important to note here that what's coming through right here in this value is a done. If I log this out, you'll see the done symbol. We just ignore that and logged out You win.

[2:49] We could also account for that by doing something like a mapDone passing in a done value with our broadcaster and listener, then with our broadcaster handling the value. If the value is done, then I could push out the done value we pass in. This'll be passed into here.

[3:11] If I said, mapDone("You win"). If I hit Save here and type in HONEYCOMB, again, you'll see we now have You win being passed down. We could just change this back to console.log of whatever and we now get this map value.

[3:29] The things to notice here with these operators is this is only ever sending a done. It'll stop everything after it gets that done. Nothing happens unless this condition is met. If it does happen, it sends out done and cancels.

[3:41] In this one, this is ignoring every other value other than done. If you're to use an operator like this, you'd have to realize that all these other values aren't being used at all. If you wanted to, you could set up an else and listen for those values, but that doesn't apply to our scenario.

[3:57] Now that we can both play and win, let's make sure that we stop playing after we win. I'm going to go ahead and bring play down here. I'm going to define a playWithWin that can take our original play and then do something once win is fired.

[4:15] Let's set up a pipe to handle that. Let's call thisRules for now and call this a pipe. We'll set up a cancelWin operator, say, we cancel when anything comes through on win. Meaning that if I get a value from here, just go ahead and cancel play, so that it stops accepting values.

[4:36] A cancelWin would look something like this. This is a cancel broadcaster. This would be our play broadcaster. This is the listener, the console.log. This is just the default cancel, which would be the broadcaster with the listener. Our cancel broadcaster would just take any value, kind of ignore that value and then call cancel on the original broadcaster.

[5:01] Then, we can return a function that would call the original cancel just in case these get canceled. I can just call this one cancel2 or something and then cancel that as well.

[5:13] If I wrap the rules around play and instead of play here, I'm going to playWithWin, with all this hooked together, if I type in HONEYCOMB now, I get to the You win. If I try typing anymore, you see I typed in A and nothing happened. If I delete characters, nothing happens. The game is essentially over.

[5:34] If I hooked up all of the cancellation correctly, if I check the event listeners on the input, you'll see that they're all gone. If I refresh, you can see this input has three event listeners. I'll address how we can share one event listener across those three broadcasters in the future. For now, it has these three.

[5:53] As soon as I type HONEYCOMB and I win, if I refresh this to check on them, they're all gone. Everything's canceled and my app has no logic left running.
