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


    - Ticks with ir:
           opto interrupters are an electronic component with many applications. in fact, one of the most common uses of this is in the mouse scroll. it consists of a light, usually an ir led, and a phototransistor. there is a small gap between these two sensors. when the led emits light onto the phototransistor, it completes the circuit and the current flows through it. so now when the opaque encodes moves in between the opto interrupter, it interrupts the flow of current. 
rotary encoders have 20 equally spaces slots on them. so when the encoder rotates, it allows small pulses of light to reach the photo sensor. these pulses are further used to calculated the speed and the distance. 
to calculate the speed, we need the distance and the time required to cover it. we also need the circumference of the wheel. 
generally the diameter of such rotary encoders is 66 mm. so the circumference is 207.4 mm.
66 x pi = 207.4 mm.
so we can easily calculate the distance now from the number of revolutions of the encoder. 
let us consider the case where the encoder has done 10 revolutions in a minute. 
distance covered = 207.4 x 10 = 2074 mm = 2.074 meters
time taken to cover that distance = 60 seconds
speed = 2.074 / 60 = .034 m/s or 34 mm/s
this is how the speed and the distance are calculated. 

    - Stplizer:
        To stplize the speed of the motor
    - Server video streaming:
    
    - Parking with ultrasonic (Space detiction):
        The system is a low-cost prototype for implementing a parallel parking algorithm on a mobile robot car, using a Raspberry Pi, camera, Ultrasonic sensors and an optical sensor. A hardware push button starts process of self-parking the car. On pressing the button, the robot moves forward, while scanning for vacant spots on the side using ultrasonic sensor array and the camera. On finding a suitable spot of appropriate dimensions, the robot moves forward and stops at an appropriate distance. The robot then makes a 45 degree turn and back up into the spot. The ultrasonic sensors at the back of the robot allows it to move backward till the obstacle. Then the robot makes another 45 degree in the opposite direction to become straight. After this using the front and rear sensors, the robot can park itself within the spot. The control algorithm goes through various stages, where the Raspberry Pi would use various combinations of the sensor data to make decisions and rotate the servo motors in appropriate direction to maneuver the robot. The robot car should select only those spots in which it can fit in. It should also not collide with the walls or other vehicles during the entire process.
        ![1](https://user-images.githubusercontent.com/76526170/227623194-fb06d989-4043-4877-a772-8c4d1b8c055c.png)

The system software consists of the Self-Parking State Machine and associated functions and interfaces .

Self-Parking State Machine: The FSM is used to move the Robot Car from initial position to the final parked position. The various states make use of different combinations of sensors to control the movement of the robot .
![2](https://user-images.githubusercontent.com/76526170/227623418-976710dc-20fd-49ed-950a-62ae1e500d43.png)
![3](https://user-images.githubusercontent.com/76526170/227623524-1b4adf11-6638-442d-9542-aff67b5e8551.png)

Hardware PWM generation: The PWM signal required for controlling the servo motors is generated using the pigpio library. Pigpiod is a utility which launches the pigpio library as a daemon. Once launched the pigpio library runs in the background accepting commands from the pipe and socket interfaces. The pigpiod utility requires sudo privileges to launch the library but thereafter the pipe and socket commands may be issued by normal users .


Optical mouse odometry: The position of the robot at any point of time is sensed using an optical mouse connected over USB port. The optical mouse, when being used on the computer for a graphical user interface, returns a dx (change in the x coordinate) and dy (change in y coordinate) to move the mouse pointer on the screen. These values can be integrated to obtain the real time x an y coordinates of the mouse. Hence, the mouse is attached with the robot. When the robot moves forward, the x coordinate of the mouse should remain constant to make sure it is running in a straight line. The y coordinate of the mouse would provide the distance travelled by the robot. The mouse movements in the x and y direction are accumulated using a background process. Any movement in mouse is captured and immediately updated on a FIFO. The main application reads from FIFO to get the current position .

Movement control: To make the robot move in a straight line, the initial x and y positions are stored, the left motor is rotated in anticlockwise direction and right motor is rotated in clockwise direction. The right motor is moved at a constant speed and the speed of the left motor is varied in proportion to the difference between current x position and initial x position to minimize the error and maintain straight line movement until current y position matches the desired value. For rotating the robot, the motors are rotated in same direction and same speed. When the current x value matches desired value, the rotation is stopped .

Fire hydrant detection: The image processing algorithm looks for red objects in the frame and if a red object of dimension larger than the set value is detected, it is tagged as a fire hydrant. The detection was carried out using OpenCV library. The frame from the camera is captured and converted from RGB to HSV color space. The image is masked to detect only red pixels. Further computation intensive processing is done only if number of pixels exceed the minimum threshold, otherwise the frame is discarded. The boundary and center of the object is then extracted. If the radius is higher than the minimum set value, the object is tagged as a fire hydrant .

Ultrasonic Interface: The HC-SR04 distance measuring transducer can be easily interfaced with code. However, using readily available library makes it easier to add multiple sensors and avoid cluttering up the main program code. The Bluetin_Echo library was installed using PIP used to read the sensor in centimeter scale .

User Interface: The user interface for the systems consists of a pushbutton and a PiTFT. The push button is sensed through interrupt processing using RPi.GPIO library. The Pygame library provides an excellent platform for implementing the GUI. The GUI provides feedback to the user about the current state of the parking algorithm and also forms a useful tool for debugging .
## Tested and fails

    - Optical flow
       by detecting local features in frames using Scale-invariant feature transform algorithm
       then supply the output points to Gunnar Farneback to find the translation and speed of the car
      
    - Detecting speed with ultrasonic :
To calculate the speed, the ultrasonic sensor needs to read the distance of object at least twice between a fixed interval of time, say 1s.
Let’s visualize this with an example, Object X is moving with speed Y The ultrasonic sensor is will measure the distance of the object every 1 second. When the sensor measures the distance of the object the 1  time, the object X is at position A When the sensor measures the distance of the object the 2 Since the object moved |A-B| distance in 1 second, using the speed formulae, we can calculate the speed of the object speed = distance / time 
Here, speed = |A-B| / 1 The given result will be in the units of cm per second or cm/s
