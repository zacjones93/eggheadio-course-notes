John Lindquist: [0:00] I'm anxious to get all of this out of the console and into the browser. I'm going to take all of the operators we've made and cut and paste them into our operators file. Those ones and all of this. That's not an operator. We'll delete that. We'll go ahead and export all of these.

[0:19] With map sequence, we still need to return a function that will cancel. We define cancel up here. Make sure that cancel's assigned to each time a listener is passed into our broadcaster. That should be good for now. If we run into bugs, we'll come back and fix it later. Now I'm going to clean up all of this stuff.

[0:44] I want to talk about what the challenges are for rendering stuff in the DOM. Say, for example, I take an addListener and that's on the input each time you type. I want to do something with that event and render something in the DOM.

[1:01] The challenge is the way the DOM looks when you set up and the way the DOM looks after you render may be completely different. You end up comparing the two and seeing if you need to add the listener over again.

[1:12] All of the Vue libraries out there solved this problem of comparing the DOM before and after those changes, whether it's React, Vue, Angular, or any others. I'm going to port this to React instead of trying to write my own Vue library.

[1:25] Since we're using Parcel, we can just go to the recipes page and look up React, which is the first result. I'll go ahead and npm install react and react-dom. This is just an expansion syntax I like to use rather than typing out ReactDOM again, this does react + react-dom and does both of them. I'll hit Enter there.

[1:50] If I import React from 'react' and import, from react-dom we'll import { render }. I can go ahead and make an app and just say, "Hello," and then render my app into my document.querySelector() and create a route.id and go back into my index.html, get rid of my input, and create a route.id.

[2:19] Let's save there, look back in my personal sandbox, and you can see we now have React up and running. I'm going to go ahead and disable this message. I'm just going to add a script tag, paste a snippet, it looks like this, hit Save so that's gone. That's just for these lessons where I can work in incognito mode without the React DevTools.
