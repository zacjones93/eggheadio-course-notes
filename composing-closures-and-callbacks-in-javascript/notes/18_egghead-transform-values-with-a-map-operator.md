Instructor: [0:00] Let's create another one of these that will allow us to uppercase characters coming through. I just duplicated everything here, and I'm going to call this map. To start with, I'm just going to get rid of this and change the inside of this to just value just to make sure it works.

[0:19] We'll wrap our broadcaster with map, and we should still be at the default behavior, and that looks right. Now with this template where we can configure what we want to do, I want to value to uppercase.

[0:36] I'll hit save here, and you'll see everything is now uppercased. Now, rather than hard-coding in the behavior that we want, we can pass in a function before the broadcaster. We'll call this transform. Then we can wrap the transform around our value.

[0:57] Now we can define a function here. We'll just say x is x toUpperCase. Once I hit save, you'll see everything is still uppercased, because this function is going into here. Then we're using that on our value.

[1:15] The value comes through here. Then value toUpperCase is what's being applied to each value. I can either extract this or there's even just a t upper on lodash that I can use. I'll just put that in here, toupper. I'll hit save, and we're back to where we were.

[1:34] There's lots of methods I could toss in here. I could try tolower. Hit save. Now we're at lowercase. Again, notice that modify and map look almost exactly alike, where they take a broadcaster and a listener, define a new listener inside of that broadcaster, and then invoke the original listener with its new behavior.

[1:56] As we go through creating more of these, we're going to call this pattern an operator. I'm going to create a new file called operators. Grab these. I'll grab both modify and map. Cut them out. Go into operators, paste them here. Make sure to export both of these. I also need to import done from the broadcasters.

[2:26] Then in my index file, I can import map and modify from operators. Looks like we also need curry in operators. I'll copy this line, paste that here. Hit save. Now, we're back in business. We'll clean up the unused things.

[2:47] Now, our index file looks much simpler as we divided our broadcasters into a collection of broadcasters and our operators into a collection of operators. We assemble those functions together to get the behavior that we want.
