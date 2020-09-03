John Lindquist: [0:00] With almost all asynchronous scenarios, we need to be able to cancel what we told our code to do in the future. We said after one second, console.log("1"). Our challenge is to cancel this behavior before it happens. The problem is that to cancel a timeout, you need to get the id of the timeout, but now, this id is stuck inside of the body of this function.

[0:25] A straightforward solution is to return the id. That means that anytime one of these is called, we can get back an id, which we can use to clear a timeout and pass in that id. If I hit Save here, you'll see no 1, but then a 2 and a 3. This means we successfully cleared the timeout created by this oneSecond function.

[0:50] Because this is always the way to cancel timeouts, instead of returning the id, we can return this wrapped in a function. I can cut this out. Instead of id here, I can create a function. In the body of that function, I'll paste clearTimeout(id).

[1:10] Now this is returning a function which captures the behavior we want, the cancellation behavior. Instead of an id here, we'll have a cancel function, which we can then call. When I hit Save, you'll see only 2 and 3 up here.

[1:26] Because of the way we set this up, we have cancellation available to all of the functions we've created, to oneSecond, twoSeconds, and threeSeconds. I'll rename this one cancelOne. Then I can easily create a cancelTwo and cancel that as well. I will hit Save here. You won't see 1 or 2, but you will see 3.

[1:52] We gave ourselves a lot of flexibility by capturing behaviors, like clearing a timeout inside of a function and creating a timeout inside of a function. The complexity comes from understanding that your function returns another function.

[2:07] When I invoke createTimeout, it's giving me back this function, which expects a callback. CreateTimeout gives me back oneSecond, which is a function, and oneSecond takes this callback. Then oneSecond is also returning a function, which wraps the behavior of canceling what it's doing.

[2:27] You gain a lot of power and flexibility when you wrap things inside of functions. The complexity you need to grow accustomed to is the idea of returning functions from other functions, and also passing functions into other functions, like we do here.
