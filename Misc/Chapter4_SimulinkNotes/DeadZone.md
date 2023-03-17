# Looking at Dead Zone Effects

The provided file uses the dead zone block, and according to MATLAB's documentation it functions as so:

You set a region of dead zone with an upper limit (UL) and a lower limit (LL). If this block receives any input X such that
$$LL\leq X \leq UL$$
then the output of the block will be zero. And then, for inputs outside the deadzone (i.e. inputs that will cause an output) the rules are:

- For input X greater than the upper limit UL, the output will be the original signal X with the upper limit **subtracted**

$$ \text{For }\hspace{2em} X > UL \hspace{2em}\text{we have}\hspace{2em} \text{Output }= X - UL$$

- Similarly, for input X less than the lower limit LL, the output will be the original signal X with the lower limit **subtracted**.

$$ \text{For }\hspace{2em} X < LL \hspace{2em}\text{we have}\hspace{2em} \text{Output }= X - LL$$

Note that this means that if your upper or lower limit are positive it will shift the output down, and if they are negative it will shift the output up.

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

![image](https://user-images.githubusercontent.com/84261577/225809411-8516d27b-ea35-4e26-b3bc-fc43f5eeb103.png)


# Proper Use

Now, I don't think it's supposed to be used as we did above, but instead to probably set a dead region around 0 like you might experience in the real world, where an old control may not be responsive until you move it far since it's worn out. For this, we'll dead zone a region around 0, we'll do one case where the region is symmetric and another where the region is asymmetric (i.e. not equal UL and LL).

## Equal Upper and Lower Limit

We'll use 
$$LL =-2\hspace{2em}\text{and}\hspace{2em}UL = 2$$

Here the output is:

![image](https://user-images.githubusercontent.com/84261577/225809518-60b82b58-4f5c-41bd-851a-10de7e0d47da.png)


## Different Upper and Lower Limits


We'll use 
$$LL =-5\hspace{2em}\text{and}\hspace{2em}UL = 3$$

Here the output is:

![image](https://user-images.githubusercontent.com/84261577/225809738-82ef66cd-1fd8-45f5-a834-cc5b6a59efef.png)

### Notes

So in the case that we saw in class, with a region around 0, we see that it ultimately pulls the curve towards 0 (i.e. voltages above 0 become smaller, and voltage below 0 get larger, both closer to 0 than the original input.


# Effect of Deadzone When Applied to System

Now let's see what happens in each case when we apply it to the system shown in class, namely:

![image](https://user-images.githubusercontent.com/84261577/225810083-52680572-38f3-48d2-904c-f855f0155d05.png)

Note for all plots below:
- Blue Trace is output of system using the unmodified original sine wave (orange) as input (labelled as "Integrator 1" in the plot legend)
- Yellow Trace is output of system using the *deadzone output* (green) as input (labelled as "Integrator" in the plot legend)
- Orange Trace is the unmodified sine wave with amplitude 10 (labelled as "Sine Wave" in the plot legend)
- Green Trace is the *deadzone output* using the sine wave as input (labelled as "Dead Zone" in the plot legend)

## Only An Upper Limit

MATLAB will not let you specify only one parameter, so we'll "trick" it by making our lower limit the maximum output we want, and we'll set the upper limit to something over 10. By doing thise we're basically trying to have a deadzone whenever our original input is over 3V.

We'll use 
$$LL = 3 \text{ and }UL=100$$

Here the output is:

![image](https://user-images.githubusercontent.com/84261577/225810627-af7f700d-1ab7-4fe7-a919-20955a3726e1.png)

This is interesting. Since the input is always less than the lower limit LL, and LL is positive, then the signal will always be shifted down, and simply cutoff when the original input is over 3. This results in the deadzone input always being negative, making the system output trend downwards.


## Only Lower Limit

We'll use 
$$LL = -100 \text{ and }UL=-3$$

Here the output is:
![image](https://user-images.githubusercontent.com/84261577/225810687-e37a936a-d7fb-40ff-8464-731eb4d166f1.png)

This is interesting too, as it's basically just the reverse of the previous case. Since the input is always greater than the uppler limit UL, and UL is negative, then the signal will always be shifted up since subtracting UL is basically adding. Likewise, the deadzone signal will simply cutoff when the original input is under -3. This results in the deadzone input always being positive, making the system output trend upwards.

## Equal Upper and Lower Limit

We'll use 
$$LL =-2\hspace{2em}\text{and}\hspace{2em}UL = 2$$

Here the output is:
![image](https://user-images.githubusercontent.com/84261577/225810736-0b5208fe-3eac-482a-8a2e-3862626ec47d.png)

This case is more interesting (I think at least). Here since the deadzone is in a positive and negative region, it does the opposite of what we saw previously, and results in the dead zone curve being pulled towards 0. We wee that when the input to the dead zone block is over 2, the output is simply the original sine wave -2, and conversely when the input is under 2, the output is the signal +2. However, because this is symmetric about 0, it basically weakens the signal by pulling it in.

The affects of this on the output are understandable, the output doesn't change as much since the input is reduced, and so it is almost a scaled down version of the original system output. But since our deadzone is symmetric about 0, there is no drift like we saw previously, this will change if do not have a symmetric dead zone, as you can see below.

## Different Upper and Lower Limits


We'll use 
$$LL =-5\hspace{2em}\text{and}\hspace{2em}UL = 3$$

Here the output is:

![image](https://user-images.githubusercontent.com/84261577/225810965-a6a7a914-d7cd-486b-9ce2-ae0543ac73c0.png)

This is an interesting case. Because the deadzone favors the negative region, then on average we receive less of an input there, and so this causes the curve to drift up slightly over time (the dead zone output in yellow). I guess this is an important lesson in that if your controls aren't equally wrong, then you will have even more problems to deal with than just not proper functioning. 
