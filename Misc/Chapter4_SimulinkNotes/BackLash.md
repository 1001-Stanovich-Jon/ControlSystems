# The Backlash

One thing to note first is that unlike the saturation and dead-zone blocks, this is a block that interacts with the final signal's *output* in thise example. Previously we just worked with altering the input signal.

So, this block will provide a region that is **centered around the output** and will let you define a **deadband**. This **deadband** is a region where when the original output would normally change direction, nothing will happen, and it will take the amount of change in output specified by the **deadband** until the output will begin to change again.

So if you were thinking of gears, you can basically think of a 0 width deadband as being super-snug fit gears that have absolutely no "play" and are always in contact.

You can image a deadband of 1 being something like having a width of one gear-tooth's worth of play between all teeth on the gear, and so whenever the gears change direction for rotation, it will take one gear's worth of output from the driving gear before it can engage the other gear (which would be the system output in this example). This means that during that change in rotation, the second gear is basically just sitting and waiting, assuming it doesn't keep spinning when the other gear changes direction. 

So, with this block, if you define a deadband of 0, it's equivalent to the original system. But as you increase the deadband, it's like slowly wearing down the gear teeth, taking longer and longer the more worn out they become to engage with each other during a change in rotational direction. Eventually, if the deadband is large, and the original input changes frequently enough, the output won't even change from the middle position. You can imagine it like a gear that never really rotates completely, but just rotates one direction for less than a full cycle, and then backwards, and the gear is so worn down that nowhere during this rotation does it have a chance to engage the other gear.



All outputs are set so:
- Blue trace is with no backlash
- Yellow trace is the output with backlash introduced

## Backlash Settings Menu

## Deadband of 0

![image](https://user-images.githubusercontent.com/84261577/225821452-98115fb5-b5e4-4707-b38f-34ffc13f683e.png)

Note here they curves overlap so you only see the one, the other is hiding behind it.

## Deadband Width = 0.1

![image](https://user-images.githubusercontent.com/84261577/225821588-800f4a79-7c77-46cf-85c6-34393c6381da.png)

## Deadband Width = 0.15

![image](https://user-images.githubusercontent.com/84261577/225821701-e8d1a3e0-a458-4174-833f-19fc5c4b0556.png)


## Deadband Width = 0.2

![image](https://user-images.githubusercontent.com/84261577/225822326-752ac989-895e-4939-987b-2d4e780a588b.png)


## Deadband Width = 0.25

![image](https://user-images.githubusercontent.com/84261577/225822376-9c1b099c-cb06-469a-8a13-c74b0aa8c7d0.png)


## Deadband Width = 0.5

![image](https://user-images.githubusercontent.com/84261577/225822477-6dd8ad4b-6181-4537-b104-50d9ece511e6.png)

## Deadband Width = 0.75

![image](https://user-images.githubusercontent.com/84261577/225822544-97fbe569-4219-4daa-911d-5da0fecec02f.png)


## Deadband Width = 0.8

![image](https://user-images.githubusercontent.com/84261577/225822628-8fbb0fbd-0e12-497a-93ef-e3fe064ed398.png)


## Deadband Width = 0.9

![image](https://user-images.githubusercontent.com/84261577/225822689-2b75c402-c726-4e17-8814-8fd90456c72d.png)

## Deadband Width = 1

![image](https://user-images.githubusercontent.com/84261577/225822748-a43f7288-8a2c-4576-b901-411f395bbc71.png)


## Deadband Width = 1.1

![image](https://user-images.githubusercontent.com/84261577/225822861-b17fddff-bdbb-4c6b-a7fe-4962c11e8f7b.png)

## Deadband Width = 1.2

![image](https://user-images.githubusercontent.com/84261577/225822822-5f2738a2-9d00-4e11-8648-c20630f1f656.png)

## Deadband Width = 1.3

![image](https://user-images.githubusercontent.com/84261577/225823100-05afc493-67d2-4b06-81d0-18ed4297577d.png)



## Deadband Width = 1.5

![image](https://user-images.githubusercontent.com/84261577/225823153-fd3bb604-dd82-4463-bfb2-eb325fa8640e.png)


## Deadband Width = 2.0

![image](https://user-images.githubusercontent.com/84261577/225823236-d103ee7f-c7a4-40fb-9b8a-fa8c6b33b891.png)

## Deadband Width = 2.2

![image](https://user-images.githubusercontent.com/84261577/225823449-fb4318b9-5468-4bf5-b046-9be7e2870ea2.png)


## Deadband Width = 2.3 (and anything over)

![image](https://user-images.githubusercontent.com/84261577/225823523-b1f37f23-42d5-4109-b17f-593617487d79.png)






