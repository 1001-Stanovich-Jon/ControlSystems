# Looking at Dead Zone Effects

The provided file uses the dead zone block, and according to MATLAB's documentation it functions as so:

You set a region of dead zone with an upper limit (UL) and a lower limit (LL). If this block receives any input X such that
$$LL\leq X \leq UL$$
then the output of the block will be zero. And then, for inputs outside the deadzone (i.e. inputs that will cause an output) the rules are:

- For input X greater than the upper limit UL, the output will be the original signal X with the upper limit **subtracted**

$$ \text{For }\hspace{2em} X > UL \hspace{2em}\text{we have}\hspace{2em} \text{Output }= X - UL$$

- Similarly, for input X less than the lower limit LL, the output will be the original signal X with the lower limit **subtracted**.

$$ \text{For }\hspace{2em} X < LL \hspace{2em}\text{we have}\hspace{2em} \text{Output }= X - LL$$

So we see that in both cases the input will ultimately be shifted *down* by the upper and lower limits. Let's look at an example. Let's have an input that is a simple sine wave with amplitude 10. The normal output will look like:

![image](https://user-images.githubusercontent.com/84261577/225808070-cbd203d3-ee91-4bdf-a6da-94a9fcbf4791.png)

Note that the normal output will be kept for reference, and will always be the orange trace. The dead zone output will be the green trace.

Now let's apply a few dead zone conditions. The first will be:

## Only An Upper Limit

MATLAB will not let you specify only one parameter, so we'll "trick" it by making our lower limit the maximum output we want, and we'll set the upper limit to something over 10. By doing thise we're basically trying to have a deadzone whenever our original input is over 3V.

We'll use 
$$LL = 3 \text{ and }UL=100$$

Here the output is:

![image](https://user-images.githubusercontent.com/84261577/225808946-3d8d964f-cf6a-44c2-96ad-c9e56f888c34.png)


## Only Lower Limit
Again, MATLAB will not let you specify only one parameter, so we'll "trick" it by making our upper limit the lowerst output we want, and we'll set the lower limit to something under 10. By doing thise we're basically trying to have a deadzone whenever our original input is less than -3V.
$$LL = -100 \text{ and }UL=-3$$

Here the output is:


# Proper Use

Now, I don't think it's supposed to be used as we did above, but instead to probably set a dead region around 0 like you might experience in the real world, where an old control may not be responsive until you move it far since it's worn out. For this, we'll dead zone a region around 0, we'll do one case where the region is symmetric and another where the region is asymmetric (i.e. not equal UL and LL).

## Equal Upper and Lower Limit

We'll use 
$$LL =-2\hspace{2em}\text{and}\hspace{2em}UL = 2$$

Here the output is:

## Different Upper and Lower Limits


We'll use 
$$LL =-5\hspace{2em}\text{and}\hspace{2em}UL = 3$$

Here the output is:









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




