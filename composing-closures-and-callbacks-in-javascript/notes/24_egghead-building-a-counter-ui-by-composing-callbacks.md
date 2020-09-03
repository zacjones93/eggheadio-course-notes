Instructor: [0:00] As a quick exercise to make sure we're not getting bogged down in functional terms or patterns, let's do a simple counter where if I click a button that has a plus sign on it, it'll add a value. If I click a button that has a minus sign on it, it will subtract a value. Clicking here would plus one. Clicking here would minus one.

[0:23] In our index, I'm going to delete everything. I'll set up our broadcaster first, our addListener. The configuration for this will be a selector and an event type. Every broadcaster ends in a listener. In here, we'll use the document to query selector, the selector which gives us our element and the element addEventListener with the event type. Passing in a listener hooks everything together.

[0:57] For now, we're going to ignore cancellation and doneness just for brevity's sake.

[1:03] With addListener, I'll set up a plusClick. addListener takes the selector for plus and click. minusClick is addListener and takes the selector for minus and click. Let's hook this up just make sure it's working. We'll check the event just to make sure that it logs out the event value. I'll click on the plus button. We see mouse events.

[1:29] Now, instead of mouse events, we want to hard-code a 1 or -1. I'm going to define an operator called hardCode. The configuration for this will be the new value which we can hard-code. An operator takes a broadcaster and a listener.

[1:45] In here, we set up our broadcaster. We set up our new listener, which is this function. We use our current listener to ignore this value and instead pass in our new value. This way, if I hook this together, hardCode the value of one to plusClick, I could then just name this +1.

[2:06] I'll use +1 and check the value and make sure we're just getting a bunch of ones. Hit save and click here. That gives us a bunch of ones. We'll set up -1 as well. We'll hardCode -1 to plusClick.

[2:22] Now we want an operator to add these together. I'll say, "add." We'll need an initial starting value as our configuration. This takes a broadcaster and a listener. Notice up here, this broadcaster and listener matches up with this. We're taking a configuration here and that one takes a configuration.

[2:41] Inside of add, we'll set up our broadcaster. The new listener is a function that takes a value. The listener will take the initial value plus equals the value that comes in.

[2:53] If I take add and start it at zero and wrap that around +1, this can just be an incrementer. If I increment and logout this value or console log the value, hit Save, when I hit Plus, it will increment the value one at a time.

[3:16] The behavior I want is not an incrementer. I want a counter, which can go up or down. That means we need a merge. This is a function which creates a broadcaster. It takes a broadcaster one and a broadcaster two and returns a function that takes a listener which is also known as a broadcaster. Just hooks these both together, broadcaster one, broadcaster two.

[3:43] Inside of here, I can merge together +1 and -1. If I hook this up to a listener, I'll say value, and console log the value, hit Save, I'll hit + and looks like I have a bug. It's right here, I typed in + click. This should have been - click.

[4:05] It shows you why testing along the way would have been important. Now I can go back here and click + and -. Now I have a fully working counter.

[4:16] To review, this is our broadcaster. It ends in a listener. Merge also creates a broadcaster, but it does it from taking into other broadcasters and returning a function which takes a listener. These both invoke the functions that create broadcasters. These are functions that accept listeners.

[4:38] Hard code ends in a function that takes a listener, that's a broadcaster. It also accepts a function that takes a broadcaster, that makes it an operator. There's also a chance to give it configuration that's similar to this add function, which we'll move up here.

[4:53] It ends in a function that takes a listener, that's a broadcaster. There's a function that takes a broadcaster, that's an operator and there's a configuration step. Hooking these together, hard code, takes its configuration, and then expects a broadcaster so that's + click going to here, same with - click going to here.

[5:12] Counter is an operator with configuration, which then accepts a broadcaster. Merge created that broadcaster by taking two other broadcasters. It took two broadcasters and then output a function that accepts a listener, also known as a broadcaster. Then everything wired together means that we can click some buttons and count up and down.
