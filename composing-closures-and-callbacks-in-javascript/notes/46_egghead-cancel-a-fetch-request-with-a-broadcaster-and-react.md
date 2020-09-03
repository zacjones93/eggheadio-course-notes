Instructor: [0:00] What we also have to do is find how we can set this up to cancel because we do need cancellation behavior with every broadcaster we create. With promises, we use AbortControllers. I'll create a new AbortController(). This is an object that has a signal on it. If I say controller.signal here and grab a signal, I can pass that signal into the config of the fetch.

[0:30] When I do this, it allows this controller to abort my fetch, meaning, from this cancellation function I'm returning, I would say, controller.abort(), and this would tell this signal to control this fetch and cancel it.

[0:48] If instead of console.log(cancel), I invoke cancel, I'll hit Save here and you'll see that I aborted that request. If I comment this out, hit Save, you'll see it goes through just fine. If I uncomment it, I successfully abort the request.
