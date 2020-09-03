John Lindquist: [0:00] I brought repeat and repeatWhen into our operators, and we need to be able to stop and restart the game when the score hits . Let's setup a system for that. I'm going to add listener to the input onClick. We'll call this inputClick. Then I'm going to set up a score hype, and I'll write an operator in line so a broadcaster and a listener.

[0:25] We'll capture some state, and this can just be the value of 3 for now. Each time the broadcaster pushes out a value we'll subtract from the state, and then just push out the state through the listener, meaning that if we use score to wrap around the inputClick and log this out, once I come over and click in here, we'll see it goes 2, 1, . For us we want this to be game over.

[0:49] I'm going to capture this just as state right now. We'll work on this a bit more later. We'll call this state, paste it right there, bringing back into our pipe. Now we need to set up something that knows that once we hit  in here, that this broadcaster is now done.

[1:07] Let's set up a done if. This done if can take a condition. Then our broadcaster, and then our listener. Our broadcaster will push out values. We'll do the default behavior of pushing out the values to our listener, but we're also going to check if the condition is true then we'll push out a done, which we also need to import from our broadcasters.

[1:34] This means I can use this like so. State, done if. The condition is value. This is a function here. Value = . Now when I hit Save here, and I click one, two, three, you can see we get a done symbol. Now, let's make sure to shut everything down once we're done. We'll go to cancel. We'll go ahead and cancel on here. Make sure to return our cancel. This also needs to return.

[2:08] So that now when we're done, I'll hit Save. I'll click one, two, three. I'll check my event listeners. You'll see there's no event listeners here. I refresh, you can see the inputClick. If I click one, two, three, and refresh here, event listener's gone.

[2:24] Let's bring in our repeatWhen from our operators. Import the operators. Bring in repeatWhen. I'm going to repeatWhen here. We'll say repeatWhen. I'm going to say input enter, meaning I'll set up an addListener called input enter, which filters on an event and checks to see if the event key is the enter key. That'll wrap around an addListener on our input, just on keydown.

[3:01] I also need to import filter. Hit Save here. If I go back to the console, and click, click, click, everything's done. If I hit Enter on my keyboard, now I can click, click, click again, and it's done again. Hit Enter on my keyboard, click, click, click, and it's done.

[3:22] One thing I noticed when setting up this demo, you can see that once I click, that it's now looking for the keydown with Enter on it. Once I hit Enter, if I refresh again, you can see it has both the keydown and the click. That means that if I just hit Enter a bunch of times, so one, two, three, four, five, and then I click, you can see I get five different values in there.

[3:51] That's caused by a little bug which I casually made when I wrote this line. This line is saying to cancel that input enter event the next time a done comes through from clicking. If I click, click, click, and I look over here, you can see the clicking event listener's gone, but keydown just sticks around no matter what I do.

[4:14] What I want this to be is essentially a one-shot, where after I hit Enter, it immediately cancels. I don't even need the if statement now, because cancel when is defined right before it. The behavior is if I click, click, click, and refresh here, you'll see the keydown. If I hit Enter now and refresh, keydown was removed, because I invoked the cancel right after I hit Enter.

[4:43] This also in our console. If I click and hit Enter, and click again, you see that it did not interrupt anything going on in here. It's still tracking down to . This isn't added until I get to . I hit Enter. I can restart 2, 1, .

[5:02] When working with asynchronous code, it's always good to poke at your UI with lots of clicks, lots of keyboard presses, and make sure that addEventListeners, removeEventListeners, the timings, and everything fire appropriately when someone does something unexpected with your UI.
