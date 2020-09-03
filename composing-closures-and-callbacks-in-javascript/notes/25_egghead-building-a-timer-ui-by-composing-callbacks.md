Instructor: [0:00] Let's switch our plus/minus buttons to start and stop buttons. This one will start, this one will stop. The idea is that once I click start, it'll start a timer, and once I click stop, it'll stop a timer. In our index, let's go ahead and save the operators we made.

[0:18] I'll cut these out, then paste them into my operators file, and export both of these. I'll save the format. Make sure to return here in case I need to cancel these in the future. Something I need to point out is that if you look at the body of these operators, you'll see they always have a listener, always have a broadcaster, usually have some configuration.

[0:41] They take those things and rewire them a little bit. This one did a plus equals, this one switched over to this value. We'll scroll up. This one had a bit more logic in it as far as a done condition and a split condition. This one has a filter condition. This one transforms the value.

[0:55] Hopefully, you can see a pattern emerging from all of these, where you're reorganizing the pieces you pass in into something new.

[1:01] These are all ways of capturing and defining asynchronous behaviors. It's just up to you on exactly what you wanted to do. To implement our counter behavior, let's delete everything.

[1:12] First, we'll import our add listener from our broadcasters and we'll grab our Start and Stop buttons. We'll get a startCick and a stopClick. Let's test out our startClick. Let's make sure that works. Click, click, click, click and you can see all the mouse events.

[1:31] I just did a shorthand here for value and then console.log value. It's the same thing. It's just that if you pass in console.log, it'll just call it the value here. Save me some typing where the listeners does console.log.

[1:47] Start click is working. Now we want to bring in a createInterval. On our createInterval, we'll map it to a 10th of a second and just call this timer. The idea is once we clicked this, this should start.

[2:00] If I were to write this without an operator, it would look something like this, where I say startClick. In the listener, I would say timer and then log out the value coming from the timer. If I click Start, you'll see a timer start, because we're essentially nesting timer inside of startClick.

[2:18] We want to capture this idea inside of an operator. We'll go ahead and call this startWhen. I want to start when some other broadcaster, I'll call this the when broadcaster, is called. We can have our main broadcaster and the listener. We just follow this pattern exactly well. Cut this, paste it here, this can be our when broadcaster.

[2:43] This can be a main broadcaster here. Our listener will be this console.log. As you can see, this is dimmed out. We're just ignoring this value for now.

[2:54] I'll go ahead and use startWhen like this, I'll say startWhen, startClick, the main broadcaster will be the timer, and then the listener will be a console.log. If I hit Save here, I can click the Start and you'll see the timer starts.

[3:09] You have to really put on your asynchronous hat and think deeply about the future. If I click Start three times, one, two, three, you'll see three different timers will start. That might be your desired behavior, so we can go ahead and leave it like this.

[3:23] If it's not, then we have to find out a way to get a reference to the cancel of our main. Cancel main and assign it here, cancelMain. Whenever we click, if cancelMain already exist, then we'll go ahead and cancel the main.

[3:40] Now I've hit save, I'll hit start three times one, two, and three. You'll see it started over at zero each time. Let me do that again, one, two, and three. Whenever you're working with these multiple broadcaster scenarios, you have to be careful about these cancellation scenarios as well, because they definitely affect how your app behaves in the future.

[4:02] What we return from this is also the cancel of the when, so cancelWhen. Then we return a function that can shut down both main and when, so that if we wanted to cancel this entire thing, this would cancel both of them.

[4:19] With the Start button working, let's go ahead and wire up the Stop button. If we say stopWhen, we'll set up a when broadcaster, a main broadcaster, and a listener.

[4:31] The behavior inside of stopWhen is going to be we want our main broadcaster to be running with the default listener. We want to grab the cancelMain from that default behavior. It's just that we also want when we click on Stop, we want to just ignore the value and call cancelMain.

[4:54] We also want a reference to the cancel for the when broadcaster, so that when we return, we could shut down both of these. It's going to be tempting when you think of this to wrap all of this inside of stopWhen.

[5:13] I'll say stopWhen in passing the stopClick, because I want to stop when it clicks and then wrap all of this inside our stopWhen. Let's move this to a new line, I'll hit save, I'll click Start, you'll see a timer start. I'll click stop. It looks like I forgot to assign cancel when. I defined it, but didn't assign it here.

[5:33] We'll go back up here. Assign cancel when. Hit save again. Hit start and stop. You'll see that it stops. Based on the way this reads, I'm going to try and hit start again, and you'll see what happens. I'm clicking start, but the timer isn't restarting. This reads as a broadcaster or an interval which starts when you click, and this is an entire broadcaster here.

[6:00] The start when or the start click is canceled when you click stop. Our stop click isn't just canceling the timer, it's also canceling the start click. The order here is very important. Our stop when for our behavior should be around the timer, and the start when should be on the outside.

[6:23] When I hit save now, I can start a timer and stop a timer. Start a timer, stop a timer, because now start click and the behavior from start when is a broadcaster that handles a timer that stops when you hit stop click. Let's pull these out into some piped operators. We'll do operators pipe. Make sure to import pipe from lodash/fp.

[6:51] Now on our operators, we can pipe these two operators. Remember, when we use pipe, think of it step by step. We want to stop when first, because we want to create an interval that stops when we click on stop click, and we want to wrap that with a start when, so that it starts when we click on start click.

[7:12] We'll go ahead and wrap our timer in our operators. Clean up that. Put in right there. I'll hit save here. I'll hit start, stop. We have a timer that starts and stops. Because we define that extra cancel here, our timer also starts and restarts every time we hit the start button.

[7:30] This is where operators really shine, when you're defining future behaviors, especially behaviors that cancel, because I can capture this entire start when inside of a single function, and my API, the way I use it, reads like this.

[7:44] I can tuck away all of the complexity and all of the nesting of listeners inside of this logic, which I can test and make sure it works exactly how I want it, and then store those functions away for use later on.
