Instructor: [0:00] Rather than automatically repeating, it's important to be able to repeat when another broadcaster fires. Let's make a copy of repeat and name this one repeatWhen. We'll add in a whenBroadcaster. The scenario I want is if i for of, let's make sure we can import that. i for of on the word cat, so I'll create this as a word broadcaster.

[0:25] I want to be able to repeat when I click on the input box. If I set up a input click and use my addListener, we'll grab the input and onClick. If I say, "repeat when input click" on the word and I want to log this out, right now if I hit save, you'll see cat firing over and over again.

[0:56] Let's comment that out and hit save, because for of keeps firing off done, which keeps setting up the new broadcaster in that recursive loop. We want to wait here until whenBroadcaster fires and just ignore that value. Then we want to set up the new broadcaster.

[1:13] This should work right away. If I hit save here, you'll see cat. If I click, you'll see cat again. Click, see cat again. We have the initial, the second, and the third. One thing to notice is that on this input I now have three listeners. We also need to set up a cancel when and define that. Then if that exists, make sure to cancel when, if that's defined.

[1:46] Now, I'll click one, two times. If I refresh on my event listeners, I still only have that one event listener. If I check my console, you'll see the three cats in there. We need to bring this down to here as well. We'll create a function and paste that there. We have a fully working cancelable repeater.

[2:08] The cool part with the event listeners here, I check my elements, you'll see in this scenario the event listener shows up right away. If instead of the word, we did a create timeout, we'll set that to one second. I'll hit save. You see the event listener doesn't show up right at the beginning. I have to refresh. Then it would show up after that one second.

[2:28] This doesn't automatically refresh unless you click that. You'll see in my console I'll get that null. If I click again, I'll get that null. I'll still only have that one listener. That listener doesn't show up. I'm not able to repeat until I click on that box.
