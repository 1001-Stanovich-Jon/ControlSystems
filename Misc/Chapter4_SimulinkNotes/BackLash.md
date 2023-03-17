# The Backlash

One thing to note first is that unlike the saturation and dead-zone blocks, this is a block that interacts with the final signal's *output* in thise example. Previously we just worked with altering the input signal.

So, this block will provide a region that is **centered around the output** and will let you define a **deadband**. This **deadband** is a region where when the original output would normally change direction, nothing will happen, and it will take the amount of change in output specified by the **deadband** until the output will begin to change again.

So if you were thinking of gears, you can basically think of a 0 width deadband as being super-snug fit gears that have absolutely no "play" and are always in contact.

You can image a deadband of 1 being something like having a width of one gear-tooth's worth of play between all teeth on the gear, and so whenever the gears change direction for rotation, it will take one gear's worth of output from the driving gear before it can engage the other gear (which would be the system output in this example). This means that during that change in rotation, the second gear is basically just sitting and waiting, assuming it doesn't keep spinning when the other gear changes direction. 

So, with this block, if you define a deadband of 0, it's equivalent to the original system. But as you increase the deadband, it's like slowly wearing down the gear teeth, taking longer and longer the more worn out they become to engage with each other during a change in rotational direction. Eventually, if the deadband is large, and the original input changes frequently enough, the output won't even change from the middle position. You can imagine it like a gear that never really rotates completely, but just rotates one direction for less than a full cycle, and then backwards, and the gear is so worn down that nowhere during this rotation does it have a chance to engage the other gear.
