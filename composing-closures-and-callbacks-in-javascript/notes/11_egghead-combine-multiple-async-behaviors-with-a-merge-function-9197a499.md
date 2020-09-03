John Lindquist: [0:00] The most important thing we've done here is establish consistency. You can see that in the last function that we return in each of these, they're each expecting a listener. This function expects a listener, this function expects a listener, and this function expects a listener.

[0:18] When you've put together a pattern like that where you know what a function argument is going to be, you can start combining functions in interesting ways. Let's add a listener and create an interval.

[0:30] We can create an addButtonListener and assign that to addListener. We can pass in the id of button, then an addButtonClickListener. We'll use addButtonListener and pass in click.

[0:49] We can also create a oneSecond, which is our createInterval and pass in one second. Now we have two functions, addButtonClickListener, and oneSecond, which are each expecting a listener.

[1:04] Here, we passed in time. Time is here. Now we're expecting a function that accepts a listener, an addButtonClickListener. Took in the selector and the event type. Now we're expecting a function that accepts a listener. I'm going to name functions that accept listeners as broadcasters.

[1:22] You may also hear these named sources or other words that describe things that push out values. For now, a broadcaster is a function that accepts a listener. I can create a function, like merge, that accepts two broadcasters. We'll say broadcasterOne and broadcasterTwo.

[1:43] We're calling this merge because these two broadcasters are going to return a broadcaster, meaning a function that accepts a listener. Merge will take both broadcasters, broadcasterOne, and pass in the listener, and broadcasterTwo, and pass in the listener.

[2:03] Now we can use merge, invoke it, and pass in addButtonClickListener, and oneSecond. I'm going to name this clickAndTick. Although mergedAddButtonClickListenerWithOneSecond would be more descriptive, that's a lot of typing. clickAndTick can take a listener, which will be invoked when either the button is clicked or an interval has ticked.

[2:31] So, console.log(clickOrTick). I'll hit Save. You'll see it start ticking away. If I click the button, I can add a whole bunch of them. Because we also follow the pattern of having a broadcaster, again, a function that accepts a listener, return a way of canceling the broadcaster.

[2:51] We returned a clearInterval, we returned a removeEventListener, and we returned a clearTimeout. Because we're creating a new broadcast with merge, we also have to return a way to cancel both of these. Because we followed a pattern, we simply have to say cancelOne is the result of calling broadcasterOne, and cancelTwo is the result of calling broadcasterTwo.

[3:18] Then we can return a function which calls both cancelOne and cancelTwo. Actually, let's rename this to clickOrTick, because logic is this broadcaster or this broadcaster. Invoking clickOrTick will now return a way to cancel clickOrTick. If I hit Save, we're back to ticking and clicking. If I invoke cancelClickOrTick, hit Save, you'll see no ticking, and clicking does nothing.
