John Lindquist: [0:00] Let's move this behavior out into a map operator. I'm going to delete getting the first value, and instead, place a map before the modify. That takes a function to get that value. You can see we're back to our behavior.

[0:19] Now that we have that letter coming through right here, which is that second value in the array, we can create a filter. Let's just filter out commas. I'm going to select my map, duplicate it. I'll name this filter.

[0:38] Filters, instead of transforming a value, they check to see if some condition is matched. The condition you'd put right here is done by creating a predicate function and passing in a value. The predicate can live where this transform used to live. Then inside of our condition, we can move the listener up. We no longer transform it. We just pass in the value.

[1:09] Now, with the filter function available, let's go ahead and import filter. We can drop a filter right here. We'll wrap around everything. If this is looking a bit unwieldy, that's intentional. We'll fix that fairly soon. For now, let's create a predicate where we just say, if x != "," and then that should get rid of the comma from our typewriter behavior.

[1:36] All of the letters made it through, except for when it got to the comma. It just skipped the listener and did nothing. You could check that by seeing an anals block. Let's console.log(skippedValue). I'll hit Save. You'll see it skipped the comma, and then kept going. We don't need that, though. I'll delete that. Now we have a filter operator that we can use.
