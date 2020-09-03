John Lindquist: [0:00] Following the pattern we used for createTimeout, let's do something similar for an addEventListener on a button.

[0:06] First, we'll create a button with an id of button and just call it Click Me. We can document query selector and grab the id of button. We'll assign this to a variable called button and then button addEventListener. When we click on this, we want a callback that just logs out clicked. I'll click my button a few times and you'll see clicked logged out.

[0:35] Looking at this, the pieces that we can break apart are this button, this click event type, and this callback right here. If we define a function and we'll call this addListener(), we'll take the button and we'll call that element. We'll take the click and we'll call that event type. We'll take this callback, and we'll call it a listener.

[1:04] From here, we can cut and paste this inside of our addListener. This element is now this button. This event type is now our click. This listener is now our callback that's down here. We'd use this in a similar way. We'd say addListener. We want to add a listener to the button. This can be a function called addButtonListener().

[1:34] Since addListener takes an element and returns a function, which accepts an event type, this function now accepts an event type. When we invoke it, we'll say, addButtonListener, pass in a click. This now returns a function which accepts a listener.

[1:53] We'll say addButtonClickListener. Now, because this is a function, and it expects a listener, we can say, addButtonClickListener, then pass in a callback. We'll say, console.log(buttonClicked). I'll hit Save. Click on the button a few times. You'll see that it logs out buttonClicked.

[2:20] Each of these pieces return a function, which then accept the next parameter, so addListener accepts the element, then returns a function, which accepts event type. addListener took the button and then returned a function, which now accepts a click. This returns a function which accepts a listener. That's this function. You'll see, here, we pass in the listener.

[2:44] One other thing I like to do for convenience is I can cut out this line. I'll go ahead and paste it in here. Instead of looking at the element, I can just pass in a selector and then pass the selector into here. Now my button is my element. Here, I pass in the selector instead.

[3:07] Similar to how we remove the timeout, by returning a function that invokes clearTimeout, in our addListener, let's return something that can remove our event listener. This time, we can return a function that does elementRemoveEventListener, passing the event type, and the listener.

[3:29] Now when we invoke addButtonClickListener, we'll get back a function for removeButtonClickListener. If we hit Save now and start clicking, you'll see we get buttonClicked. If I invoke removeButtonClickListener, I'll hit Save, and you'll see, if I try and click, I don't have a listener on it because this was called before we ever got a chance to click on the button.

[3:57] You can confirm that by inspecting this button. Looking at the event listeners, you'll see that there are no event listeners. If I comment this, you'll see there's a click event listener. I'll uncomment this and hit Save again. Now there are no event listeners.
