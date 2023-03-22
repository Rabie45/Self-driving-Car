# Self-driving-Car

## Points to be explanied

    - Finding lane :
The idea is to find the path using color detection or edge detector and then getting the curve using summation of pixels in the y direction i.e a histogram. We    can split the task into 5 different steps. This includes Thresholding, Warping , Histogram, Averaging, and Displaying. Since we have been creating modules so   far, we are going to create a module for lane detection as well. This way we don’t need to put all the code in one script instead we can have separate python files that each perform their separate tasks. So for this project we will have a Main Script that will be connected to our Motor Module and the Lane Detection             Module. Since the Lane Detection code will take up some space we will separate all the functions into a Utilities file keeping the main Module neat and clean.
      ![image](https://user-images.githubusercontent.com/76526170/226867338-b16d2373-2b2e-47da-a4f1-d0e62292cb2f.png)

    - Warping lane :
 So we can simply crop our image, but this is not enough since we want to look at the road as if we were watching from the top . This is known as a bird eye view       and it is important because it will allow us to easily find the curve. To warp the image we need to define the initial points. These points we can determine             manually. So to make this process easier we could use track bars to experiment with different values. The idea is to get a rectangle shape when the road is             straight.
      ![image](https://user-images.githubusercontent.com/76526170/226867415-df8cb357-6dda-43db-a65a-7056272aee3a.png)
    - Finding curve :
Histogram(Make search to understad more)
Now comes the most important part, finding the curve in our path . To do this we will use the summation of pixels. But what is that? Given that our Warped image         is now binary i.e it has either black or white pixels, we can sum the pixel values in the y direction. Lets look at this in more detail.
![image](https://user-images.githubusercontent.com/76526170/226867899-21824d44-9c51-4519-9a34-e28c0d10421d.png)

    - Optimizing curve :
The picture above shows all the white pixels with 255 value and all the black with 0. Now if we sum the pixels in first column it yeilds 255+255+255+255+255 =          1275. We apply this method to each of the columns. In our original Image we have 480 pixels in the width. Therefore we will have 480 values. After summation we          can look at how many values are above a certain threshold hold lets say 1000 on each side of the center red line. In the above example we have 8 columns on the          left and 3 columns on the right. This tells us that the curve is towards left. This is the basic concept, though we will add a few more things to improve this          and get consistent results. But if we look deeper into this we will face a problem. Lets have a look.
![image](https://user-images.githubusercontent.com/76526170/226868243-02dee91d-3bec-4d15-bcd3-b73c543233bb.png)
https://www.computervision.zone/topic/optimizing-curve/
    
    - Maneuver :
A lane change has been described a lane change in three parts in  the head portion is the time and distance required for a vehicle to move from a straight-  ahead path to the first intercept of the lane line. The actual lane change starts when a vehicle  first encroaches on the lane line between the original and destination lanes. The maneuver ends once the vehicle has completely crossed that line. The tail portion of the maneuver is the time and distance required for a vehicle to return to a straight-ahead path in the destination lane after crossing the lane line. Another view describes three sequential phases of the lane-change maneuver based on steering. The first phase is an initial turn of the steering wheel to a maximum angle. The second phase begins when the steering wheel is turned in the opposite direction and ends when the vehicle heading approaches a maximum that occurs when the steering wheel angle passes through zero (straight-ahead). During the third phase, the steering wheel is turned to a maximum angle in the opposite direction to stabilize the vehicle in the new lane. 
![gggg](https://user-images.githubusercontent.com/76526170/226899679-4475659c-f47b-4dec-8515-eceb2357988b.PNG)


    - Ticks with ir
    - Stplizer:
    - Server video streaming
    - Parking with ultrasonic (Space detiction)

## Tested and fails

    - Optical flow
       by detecting local features in frames using Scale-invariant feature transform algorithm
       then supply the output points to Gunnar Farneback to find the translation and speed of the car
      
    - Detecting speed with ultrasonic :
To calculate the speed, the ultrasonic sensor needs to read the distance of object at least twice between a fixed interval of time, say 1s.
Let’s visualize this with an example, Object X is moving with speed Y The ultrasonic sensor is will measure the distance of the object every 1 second. When the sensor measures the distance of the object the 1  time, the object X is at position A When the sensor measures the distance of the object the 2 Since the object moved |A-B| distance in 1 second, using the speed formulae, we can calculate the speed of the object speed = distance / time 
Here, speed = |A-B| / 1 The given result will be in the units of cm per second or cm/s
