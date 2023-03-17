# For Saturation in Series with Input

For our nomal system we have the direct input of our signal, but we can model saturation in simulink by providing the saturation block.

Some notable things here:
1. Since our input signal is simply a step function, having the *lower limit of the saturation block* below 0 does not affect anything.
2. Changing the *upper limit of the saturation block* will affect things, only when the limit is lower than our maximum input

This makes sense, because if we're within operating range then nothing weird should happen. So, the simulink file is below

- Source is a 10V Step
- Top branch is Saturation (you can set saturation limits)
- Lower branch is ideal scenario where we have no saturation

![image](https://user-images.githubusercontent.com/84261577/225768236-5f285b1f-2726-48eb-a902-c06fc8be9fb1.png)


If we set the saturation block to -5V lower and +5V higher, it's affects are the same thing as simply settup the upper limit to +5V and the lower limit to 0 or below.
The output is shown below (blue trace is unmodified response | yellow trace is response with saturation)

![image](https://user-images.githubusercontent.com/84261577/225768060-e8df139f-a82b-4d53-9d3f-29246a88cf5f.png)

Notice that the final value of the saturated response is(approx 0.6) one half the unsaturated one (approx 1.2), this is because out input's magnitude is limited to one half of it's value (input is 10, saturation is 5). Let's test this theory.
 
We should expect an output of around 1 for a saturation level of +8V  and an output of around 0.8$$\cdot$$1.2 = 0.96 for the saturated response:

That is exactly what we get:

![image](https://user-images.githubusercontent.com/84261577/225768923-4cb332b9-39d1-482b-8990-56e8bbb867cb.png)

Lets work backwards more. This means for a saturation level of 3V then we would expect 0.3$$\cdot$$1.2=0.36V final value for the saturated response.

This is exactly what we get:

![image](https://user-images.githubusercontent.com/84261577/225769085-53c0ba8f-ef65-4fd7-96ad-56f81b45ba8e.png)
