John Lindquist: [0:00] Before we go and create any more operators, I've noticed a pattern here that has the same block of code if value = done, if value = done, and if value = done in each of our operators.

[0:14] The main takeaway from this course is if you see a pattern evolving you should be able to wrap it inside of a function. Let's delete this, because this is ideally what I want my function to look like, but you'll see that it bombs out, because it can't convert a symbol value to a string, meaning that done is making it through here, and it's trying to += our string to done.

[0:38] What we're going to do is create a function called createOperator(), and we'll put it right here where we had curry before. Our createOperator is going to curry a function with three arguments. The first one is the operator, or this highlighted part, which is an operator, because an operator takes a broadcaster and a listener. This function here is considered our operator.

[1:10] The arguments inside of our operator are broadcaster and listener. We need to bring these up as well. I'll copy these and paste them there, because those are the things we want to override. The body of createOperator can return an operator, which takes a broadcaster and a listener. If I hit Save here, we have the default behavior, which errors out just like it did before.

[1:40] So far, in all of our operators, we've been creating new listeners, and then invoking the original listener inside of the new listener. This time, we're going to create a newBroadcaster and invoke the original broadcaster inside of it. A broadcaster takes a listener. We're going to create a function that takes a listener.

[2:03] I'm going to call this behaviorListener. The reason for that is this listener is this function right here, meaning that when I invoke this, it's going to call the original listener with the defined behavior. This listener is this function, which we can call without the behavior defined in our custom listener.

[2:26] Inside of our operator, we'll return our original broadcaster, and then a newCustomListener. You'll see this looks exactly like this. Again, we're overriding the behavior of the listener. This time, we want to inject the pattern of value done that has existed in all of our operators.

[2:51] If value = done, then send it to the original listener, so that it doesn't try and apply some string += or any other operation. Then return before it can get to our behaviorListener where we want to send the value. This value will come through here and apply the behavior that's defined.

[3:17] Now if I hit Save, you'll see we're back to our original behavior. Now I can take createOperator. I'll copy it and paste it here. Here, I'll hit Save. Unfortunately, this will bomb out, because broadcaster is not a function, which means that our signature of createOperator takes the operator, broadcaster, and listener.

[3:44] Right now, the signature of map and filter is an operator. This one takes a transform, which createOperator doesn't support. This one takes a predicate, which createOperator doesn't support. We'll solve that by taking this, cutting it out, pasting it right here, and dropping in an arrow. Then selecting this, cutting it out, pasting it right here, and changing this to an arrow.

[4:14] I'll hit Save. It's back to our functionality. Now there's a clear delineation, which I like, where this defines what an operator is. These are the configuration options of an operator, things that you can pass into them. This allows me to get rid of these if blocks, so there and there.

[4:37] Now the body of our operators captures some simple behaviors. This one, a function checking a condition. This one, transforming the value. This one, concatenating a string. We can just tuck away this createOperator function and forget about it.

[4:56] If we want to do something different with done, we could go back to the previous curry and just implement done manually down here. I'll do that. Now we can quickly create some more operators.
