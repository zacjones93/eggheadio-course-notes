Instructor: [0:00] To add a broadcaster to React, let's add some state first. Go ahead and return this JSX, bring in the useState hook, and then just set up the basic useState. We can start it with high and say that state is high. setState would allow us to change that. Then we'll change this to state, hit Save. Now we have high.

[0:28] Let's use a createInterval broadcaster, which I'll import. We want our createInterval to call setState at the end. Essentially, something that looks like createInterval. We'll do a time of one second and then just imagine that this calls setState. We can do this behavior inside of a useEffect hook, which I can put after my useState hook.

[0:59] Go ahead and type useEffect, and this takes a function. Inside of that function, we'll go ahead and paste our createInterval setState.

[1:10] Now if I hit Save, see high, then , then 1, at least trying to change to 1. The reason this behavior goes into full panic mode is because the second parameter of useEffect accepts an array of dependencies that tells it when it should update.

[1:32] If I hit Save now, you'll see it works fine because there is nothing in this array telling it to re-render once the state changes. Before, this was trying to set this up every single time the timer updated.
