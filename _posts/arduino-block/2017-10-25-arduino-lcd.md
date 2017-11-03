---
layout: post
title: Arduino LCD Screen Workbook With Blocks
excerpt: "Arduino LCD Screen Workbook Work Book."
modified: 2017-10-25
categories: arduino_block
comments: true
share: true
sort_order: 3
---

## Project Kit

![Project Kit Coming Soon](/images/arduino-block/2017-10-25-arduino-lcd/kit.jpg)


## Bill of Materials 

- 1 x Arduino Uno
- 7 x jumper wires (male to female)
- 1 x usb type b cable
- 1 x passive motion sensor for the class
- 1 x lcd screen that uses an I2C Bus


## Steps

Before you begin be sure you have the [arduino ide](https://www.arduino.cc/en/Main/Software) installed.  You might want to review the [class presentation](https://docs.google.com/presentation/d/1NVXJuoGbR-pNWjyHMJpdIDgtxiLFyZJTAl8aILhjp4g/edit?usp=sharing)
if you found this on the internet.

#### Testing Setup

1) Turn the lcd screen on it's back side and notice that it 4 pins connected to it.  You can read more about it [here](http://i2c.info/i2c-bus-specification)

- ground (gnd)
- vcc (volts / +)
- sda (Serial Data Line)
- slc ( Serial Clock Line)
    
![step1](/images/arduino-block/2017-10-25-arduino-lcd/step1.jpg)

2) Take one of the wires and plug it into ground of the lcd screen and ground of the arduino.

![step2](/images/arduino-block/2017-10-25-arduino-lcd/step2.jpg)

3) Take one of the wires and plug it into vcc of the lcd screen and 5v of the arduino.

![step3](/images/arduino-block/2017-10-25-arduino-lcd/step3.jpg)

4) Take one of the wires and plug it into sda of the lcd screen and A4 of the arduino.

![step4](/images/arduino-block/2017-10-25-arduino-lcd/step4.jpg)

5) Take one of the wires and plug it into scl of the lcd screen and A5 of the arduino.

![step5](/images/arduino-block/2017-10-25-arduino-lcd/step5.jpg)

6) Take the arduino and plug it into the computer.

![step6](/images/arduino-block/2017-10-25-arduino-lcd/step6.jpg)

7) Drag the Big Lcd Block onto the screen.

![step7](/images/arduino-block/2017-10-25-arduino-lcd/step7a.png)
![step8](/images/arduino-block/2017-10-25-arduino-lcd/step7b.png)

8) Type something into each text block.

![step8](/images/arduino-block/2017-10-25-arduino-lcd/step8.png)

9) Upload the code to the arduino.

![step9](/images/arduino-block/2017-10-25-arduino-lcd/step9a.png)

![step9](/images/arduino-block/2017-10-25-arduino-lcd/step9b.jpg)

Great! We have just confirmed that our setup works and that we can write to the screen.  This simple allows us to 
print simple stuff to screen, but we are going to learn how to get more control.

#### How to control the back light of the lcd screen.

10) Drag the back light block on to the screen.

![step10](/images/arduino-block/2017-10-25-arduino-lcd/step10a.png)

![step10](/images/arduino-block/2017-10-25-arduino-lcd/step10b.png)

11) Drag the delay block onto the screen and connect it to the Back Light block.

![step11](/images/arduino-block/2017-10-25-arduino-lcd/step11a.png)

![step11](/images/arduino-block/2017-10-25-arduino-lcd/step11b.png)

12) Drag another back light block and connect it to the delay block and set it off.

![step12](/images/arduino-block/2017-10-25-arduino-lcd/step12.png)

13) Drag another delay block and connect it to the bottom of the blocks.

![step13](/images/arduino-block/2017-10-25-arduino-lcd/step13.png)

14) Upload the code the arduino.  You should see the back light turn on and off every second.

![step14](/images/arduino-block/2017-10-25-arduino-lcd/step14a.png)
![step14](/images/arduino-block/2017-10-25-arduino-lcd/step14b.jpg)
![step14](/images/arduino-block/2017-10-25-arduino-lcd/step14c.jpg)

#### How LCD Grid System Works

LCD screens have an x and y axis.  As you go to right the x axis number increase and as you go down the y number axis
 increases.

![lcd](/images/arduino-block/2017-10-25-arduino-lcd/lcd-grid-numbered.png)

To specify a point you put in the x axis then the y axis. For example the red point would be (1, 3).  


![lcd](/images/arduino-block/2017-10-25-arduino-lcd/lcd-grid-marked.png)

(Challenge) Can you tell me what the green point would be.

#### How to print something on the screen manually and clear the screen.

To position where to print you need to set the cursor.  The cursor is where the position where the words will start 
printing on the lcd screen.  


15) Delete all the blocks on the screen and drag the set position block onto the screen.

![step15](/images/arduino-block/2017-10-25-arduino-lcd/step15a.png)

![step15](/images/arduino-block/2017-10-25-arduino-lcd/step15b.png)

16) Drag the math number block and put it into row and column slots.  For the column set the first number block to 1,
 and set the second column slot number block 4.
 
![step16](/images/arduino-block/2017-10-25-arduino-lcd/step16a.png)
![step16](/images/arduino-block/2017-10-25-arduino-lcd/step16b.png)

17) Drag the print block and connect it to the set position block.

![step17](/images/arduino-block/2017-10-25-arduino-lcd/step17a.png)
![step17](/images/arduino-block/2017-10-25-arduino-lcd/step17b.png)

18) Drag the text block onto the screen and hook it into the lcd print block.  
 
![step18](/images/arduino-block/2017-10-25-arduino-lcd/step18a.png)
![step18](/images/arduino-block/2017-10-25-arduino-lcd/step18b.png)

19) Type Hello World into the text block.

![step19](/images/arduino-block/2017-10-25-arduino-lcd/step19.png)

20) Upload the code to the arduino.

![step20](/images/arduino-block/2017-10-25-arduino-lcd/step20a.png)
![step20](/images/arduino-block/2017-10-25-arduino-lcd/step20b.jpg)

21) Now drag the delay block and put that onto the screen.  Change the number in the delay block to 5000.  That will 
make the program pause for 5 seconds.

![step20](/images/arduino-block/2017-10-25-arduino-lcd/step21.png)

22) Drag the clear block on screen.  This block will make the screen blank.

![step22](/images/arduino-block/2017-10-25-arduino-lcd/step22a.png)
![step22](/images/arduino-block/2017-10-25-arduino-lcd/step22b.png)

23) Drag the delay block and connect it to the clear block.  Then put 5000 into the delay block.

![step23](/images/arduino-block/2017-10-25-arduino-lcd/step23.png)

24) Upload the arduino code.  Notice that after 5 second hello world goes away.  Then it appears 5 seconds later.

![step24](/images/arduino-block/2017-10-25-arduino-lcd/step24a.png)
![step24](/images/arduino-block/2017-10-25-arduino-lcd/step24b.jpg)
![step24](/images/arduino-block/2017-10-25-arduino-lcd/step24c.jpg)


#### Count Loop Block / For Loop Block

So we going to learn about count loops also known as for loops.  A count loops has three parts:
- Start Number: The starting number of the loop
- End Number: The ending number of the loop
- Step Number: The number to increase the starting number every time the blocks inside the loop is executed.

Let's see how this works with a simple demo:

25) Drag the count loop block onto the screen.

![step25](/images/arduino-block/2017-10-25-arduino-lcd/step25a.png)
![step25](/images/arduino-block/2017-10-25-arduino-lcd/step25b.png)


26) Drag the debug block inside the count loop block.  The Debug Block will pause the program and print the variables
 to logout.

![step26](/images/arduino-block/2017-10-25-arduino-lcd/step26a.png)
![step26](/images/arduino-block/2017-10-25-arduino-lcd/step26b.png)

27) Now click the reset button and upload a blank sketch to the arduino.  This is clear out any old code in the arduino.

![step27](/images/arduino-block/2017-10-25-arduino-lcd/step27.png)

28) Once it has successfully loaded, upload the code to the arduino.

![step28](/images/arduino-block/2017-10-25-arduino-lcd/step28a.png)

29) Open the Logging \ Debugging window and notice the debug block is black and high lighted.

![step29](/images/arduino-block/2017-10-25-arduino-lcd/step29a.png)


30) You can now see that the program has stopped and has printed value and name of the variable.  In our case the 
name of the variable is i and the value is 1.

![step30](/images/arduino-block/2017-10-25-arduino-lcd/step30.png)

31) Click the continue block and notice the value for i changed to 2.  Continue to click the continue block until i 
equals 10.

![step31](/images/arduino-block/2017-10-25-arduino-lcd/step31.png)

(Challenge) Create a loop using the debug blocks that will start at 10 and go to 50.

(Challenge) Create a loop using the debug blocks that will start at 2 and go 20 but will only print out even numbers.

#### Making something scroll left to right

We want to scroll you rock on the screen.  So we are going to at position print at position (0,0) and stop at 
position (11, 0).

![lcd you rock start](/images/arduino-block/2017-10-25-arduino-lcd/lcd-you-rock-start.png)

![lcd you rock end](/images/arduino-block/2017-10-25-arduino-lcd/lcd-you-rock-end.png)

(Challenge) See if you can print "You Rock!" starting at position (0,0).  See if you can do that as the without looking.

32) Drag the count block and connect it to the challenge block.

![step32](/images/arduino-block/2017-10-25-arduino-lcd/step32.png)

33) Drag the right scroll block inside the loop.

![step33](/images/arduino-block/2017-10-25-arduino-lcd/step33a.png)

![step33](/images/arduino-block/2017-10-25-arduino-lcd/step33b.png)

34) Drag the delay block inside the for loop.

![step34](/images/arduino-block/2017-10-25-arduino-lcd/step34.png)

35) Upload the code the arduino and watch the words scroll on the screen.

![step35](/images/arduino-block/2017-10-25-arduino-lcd/step35a.png)
![step35](/images/arduino-block/2017-10-25-arduino-lcd/step35.gif)

(Challenge) Try to copy and paste the count block and make it scroll back to the left.

## Challenge Projects

- Play with with the blink block and make it blink move around the screen
- Connect the passive motion sensor and print the number of times passive motion sensor sensed something
- Have fun and do your own thing.

## Resources

- [PIR Sensor](https://playground.arduino.cc/Code/PIRsense)
- [LCD Library](https://www.arduino.cc/en/Reference/LiquidCrystal)