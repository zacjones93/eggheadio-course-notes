Instructor: [0:00] Since we have a text box, let's put it to good use by allowing ourselves to type something into the text box. Hit Enter and show all those words in sequence. My first thought is that, we need to wait to detect. When we hit enter, we're going to do this onkeypress and set up an onkeypress listener up here.

[0:20] We'll say, "Let onkeypress, and this is a useListener." If the idea is to get the text off of onInput, that means we can bring in target values. We'll do that here, target value. I'll call this input value and wrap target value around onInput.

[0:43] Onkeypress, I only want that to broadcast when the enter key comes through. We'll bring in filter and save that enter is filtered by an event where the event.key is equal to enter, and then wrap that around onkeypress.

[1:06] The way these two work together can look something like an allow when operator, where I can have an allow broadcaster, then the main broadcaster listener, then we can track the current value from our broadcaster where we just say that current is equal to the value.

[1:28] Our allow broadcaster would just ignore any values, but instead send the current down to the listener. You think of this as the input event getting the text from the text field, and then this as the Enter key, which will take the current text and then just pass that along.

[1:49] We can use this together inside of here where I can take the input value, and then wrap that with an allow when you hit Enter. Hit Save there, and now type something. Hit the Enter key, and then the text shows below. Type another thing. Hit Enter, and the net text changes.
