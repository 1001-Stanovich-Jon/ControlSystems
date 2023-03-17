# Looking at Dead Zone Effects

We'll use the file provided to us with the diagram of an ideal, unmodified step input (bottom branch) and a step response with a deadzone model. 

The deadzone model works by **outputting zero** for any inputs within the deadzone. This allows us to model the system as basically not being able to produce input within these regions, and immediately jumpting to the associated out put when the deadzone is overcome.

For example, if your input was 

$$y(x) = 2x$$

and your deadzone was
$x \in \[0,1)$$
then you would have no output in that region, and then as soon at 
$$x=1$$ 
your output would jump to

$$y(1) = 2$$ 
without having a chance to take on any values from 0 to 2.

## At least this ^^^ is how the block works, I'm sure it's not exactly like that in the real world.

Let's look at some cases. 




