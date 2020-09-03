John Lindquist: [0:00] Closure() is a function that accesses stuff not defined inside of it. If I defined a name up here of John and then console.logged out a name in here and called the closure, that would log out John. If I reassigned name to Mindy and then called the closure again, it logs out John then Mindy.

[0:27] If I set this to i and set this at , and then I logged out i++, every time I called the closure, we'll call it three times, you'll see, I'll zoom in, , 1, and 2. The huge difference here is if I was defined inside the closure and I hit Save, you'd see , , and  because this is inside of the scope of this function and is recreated each time the function is called.

[0:59] It's the ability of functions to capture anything outside of the function and use that value each time the function is called, that make closure special.
