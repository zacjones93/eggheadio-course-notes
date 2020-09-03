John Lindquist: [0:00] With caching enabled, I can easily show what happens when you don't cancel a previous fetch request. Because if I type in STAR, you see it makes that search, puts it in the cache, which means that when I load STAR again, it'll load super-fast.

[0:16] If I try to load something that's uncached and then go back to cached, I'll type S for STARS and watch the network down here, because as soon as that STAR search shows up, I'm going to delete the S. S, delete. You'll see the current state of my search box is STAR, but the results show the results from STARS.

[0:36] To quickly show that again, I'll type in STAR and you'll see the result show up. I'll type in an S, you'll see the search and quickly delete it. We're stuck in that bad spot again. To cancel the outgoing fetch request, we need to cancel this broadcaster if a new value comes in before this listener is called. The moving pieces here are a cancel function.

[1:00] You'll notice I installed a cool extension, which shows my warnings and errors in line. I found it very useful during my personal development. I'm going to leave it enabled for the rest of these lessons. Anyway, we're setting up a cancel variable to track the cancel function that comes back from newBroadcaster. In our scenario, it's this function which calls controllerAbort.

[1:23] Then right after our listener is called here, we'll check if cancel exists, we'll call cancel. Again, it's important you do it here. If you were to do this down here, then you'd get the value from the cache, and it would return before this could be canceled. It goes to show there's a lot of moving pieces in this asynchronous code.

[1:45] I'm going to put some login in here. I'll say, attemptingCancel. Up here, because this is the function that's calling, I'll say, aborting. We'll type STAR. I'll go into my Network tab. I'll type S, and watch for that search to pop up, and hit delete as soon as it does. S, delete. It looks like something errored out.

[2:12] That's because the STARS request got mapped to a DOM exception, meaning it got mapped to this error which got passed through the listener. We can handle that by setting our cache only if the new value is not an instance, so instance of, not an instance of error. Only cache then, but we still might want to send the error down. We'll hit Save.

[2:40] Try this out. I'll type STAR. Go into my network, type, S, and delete. You'll see in the console now the cache doesn't have STARS assigned to an error anymore. That's correct. Now the error is passed down as the result for our books.

[3:00] The way I'm going to handle this one is we have a map error which allows us to transform errors. For right now, I want to ignore the error, it's aborting the request, and not call the listener at all. I'm going to duplicate this, call this ignore error. I can delete my transform and delete this line altogether.

[3:26] This is an operator that checks to see if the value is an error. If it is, then do nothing. Otherwise, call the listener. If I drop that into our pipe down here, I'll put that right here, ignore error. Hit Save. Now, if I type STAR, go to my Network, and type S, and then delete, you'll see it aborted the request for STARS.

[3:53] The console has a cache with only one value in it, which is mapped to STAR. There were no errors. Now I can do a search for STARS. I can also delete and get the cache value and type S and get the cache value. Hopefully, this has been able to demonstrate how complex caching and error handling combined with debouncing and fetching can be.

[4:17] The last thing I want to call out is you'll see that it's attempting canceling and aborting even when the previous value had completed. You might think, "Well, if this is done, the listener has been called, I did a fetch. I might as well remove the cancel function, because I don't want to attempt again."

[4:36] Always take into consideration this might not be a fetch request. It might be an input box, a button click, or something that would push out more than one value. Even if a single value has come through, we're not sure that more values won't come through.

[4:52] That's the mindset when working with these listeners and broadcasters, is this function could be called multiple times. There's always a hidden variable of time in there.
