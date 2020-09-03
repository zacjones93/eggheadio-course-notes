John Lindquist: [0:00] Let's compare repeatWhen with startWhen. With startWhen, when I click on the input box, you'll see cat and a symbol of done. That's not right, because I can click again. That's definitely not done. If we look into startWhen, you'll see we're not handling the done scenario. Let's go ahead and set that up.

[0:22] We'll say if value is done, and we've done this a bunch of times before, we'll fire the listener with done, but then return the guard against done getting down here. I'll hit Save. I'll click again. We're still getting done. To realize why, you have to look at how this is an inner broadcaster controlled by an outer broadcaster.

[0:47] While this isn't done, if this one says it is, then it's also telling the outside one that it's done. What we need to do is check on both of them. We check the value of when(value) here. My first thought would be, toss in an and when(value) is done, and I think that's the right thinking, but there is a scenario where value is done, and when(value) is not done, so we're still getting that done symbol.

[1:16] Because we need to guard against firing off this listener, instead of doing it this way, we're going to nest this and say when(value) is done and bring the listener inside of there. If this value is done, it'll always prevent it from going down here, but only when both value and when(value) are done will it push a done out.

[1:40] I'll hit Save now, I'll click, and you won't see a done. To see a done in action, I could go ahead and just type in word here. This broadcaster would push out a done, and this broadcaster would push out a done. If I hit Save, you'll only see one of them, because of the way we set this to guard against going into here.

[2:00] Keep in mind, when you're writing these broadcasters that can control inner broadcasters that you need to take into account the doneness of them and the cancellation of them to make sure it's matching the scenario you're going for.

[2:14] To compare this to repeatWhen -- let's put this back to inputClick -- you'll see that when we start up, we don't get that initial value. If I check the elements, I can see I already have my event listener. If I click again, I still have that same one event listener, which always sticks around, never goes away, no matter how many times I click.

[2:37] If I compare that to repeatWhen, this fires automatically, but the event listener does not get attached until this broadcaster pushes out a done.

[2:49] Now this is sitting there, waiting to restart. Until I click again, this would tear this down, and then rebuild that event listener. The logic behind repeatWhen, where it has a captured repeat listener, which does an almost recursive behavior, where it calls that same listener when this fires, is almost the opposite of the startWhen behavior, where it automatically sets up the when behavior.

[3:15] That hangs around and will set up the main broadcaster whenever broadcaster fires. While clickToStart and clickToRestart may look very similar in the UI, the implementation of clickToStart is an outer controlling broadcaster with an inner broadcaster.

[3:33] The implementation of restarting is capturing that initial behavior, waiting for the initial behavior to be done setting up the when broadcaster, and then waiting for this to push out a value. Then it restarts.
