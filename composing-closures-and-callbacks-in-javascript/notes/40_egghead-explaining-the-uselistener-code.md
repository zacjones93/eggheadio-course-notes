Instructor: [0:00] I want to be clear on how useListener and useBroadcaster work together. If we look at useListener and its internal callback listener, this might look more familiar if this was renamed to broadcaster and then this was renamed to listener.

[0:19] When used in this way, this callback can act as a broadcaster that receives a listener of setState. The first time this function is called is this exact line where setState is passed into or up to this function. This setState, which originates from here, arrives here and is assigned to our listener.

[0:47] In the future, we'll undo those, this block is ignored and the listener itself is simply a call to setState. This might make more sense if you looked at this as setState because on that first pass, when this is invoked with setState, then it's assigned, but in subsequent passes, the values come through, and we just pass those values to setState.

[1:16] The goal of useListener was to write a callback that could be fired by these events, then also use it as a broadcaster, and allow us to use our operators on that callback. The solution here, which is a bit clever, which I try to avoid...

[1:35] Since on this first pass, this function is a broadcaster, and on the second pass, it's a listener. On the first pass, this is a listener. On the second pass, that value is going into the listener defined. That's the solution I came up with so that useListener and useBroadcaster could work together inside of the React model.
