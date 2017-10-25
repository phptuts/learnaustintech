---
layout: post
title: Passive Motion Sensor (PIR) With Blocks
excerpt: "Arduino Passive Motion Sensor (PIR)."
modified: 2017-10-12
categories: arduino_block
comments: true
share: true
sort_order: 2
---

## Project Kit For the Workbook

![kit](/images/arduino-block/2017-10-14-passive-motion-sensor/kit.jpg)
 

## Bill of Materials 

- 1 x Arduino Uno
- 1 x led 
- 1 x 220 Ohm Resistor
- 3 x jumper wires m to m
- 3 x jumper wire m to f
- 1 x passive motion sensor
- 1 x breadboard
- 1 x usb type b cable


## Steps

If you have not setup your block environment go [here](http://learntechaustin.com/arduino_block/input-output/) and do steps 1 through 4.  

1) Open a command prompt / terminal and type in:
``` 
cd ~/Desktop/ArduinoBlocks/ 
``` 
![step1](/images/arduino-block/2017-10-12-input-output/step5.png)

2) In the command prompt type:
``` 
sh start.sh
``` 
![step2](/images/arduino-block/2017-10-12-input-output/step6.png)

3) Now open your [Block Environment](http://127.0.0.1:3000/), http://127.0.0.1:3000/.  Click on Discard if you see blocks on the screen.

![step3](/images/arduino-block/2017-10-14-passive-motion-sensor/step3.png)

4) Plug your arduino into the computer.

![step4](/images/arduino-block/2017-10-14-passive-motion-sensor/step4a.jpg)

![step4](/images/arduino-block/2017-10-14-passive-motion-sensor/step4a.jpg)

5) (Challenge) Can you make built in led (pin 13) blink every second like we did in the first class.  Ask if you need help.  This is a test step, meaning that we want to test something small before we build something big.  It'a good habit to get into.

![step5](/images/arduino-block/2017-10-14-passive-motion-sensor/step5a.jpg)

![step5](/images/arduino-block/2017-10-14-passive-motion-sensor/step5b.jpg)

6) Take the long end of the led and plug it into (3,e) of the breadboard and plug the short end of the led into (5, e).
 
![step6](/images/arduino-block/2017-10-14-passive-motion-sensor/step6.jpg)

 
7) Take one end of the resistor and plug it into (3, d) and take the other end of the resistor and plug it into (1, b).

![step7](/images/arduino-block/2017-10-14-passive-motion-sensor/step7.jpg)

8) Take a  male to male jumper wire and plug it into (1,a) of the breadboard. Take other end and plug it into pin 7 of the arduino.

![step8](/images/arduino-block/2017-10-14-passive-motion-sensor/step8.jpg)

9) Take a male to male jumper wire and plug it into (5, a) of the breadboard. Take the other end and plug it into ground (gnd) of the arduino.

![step8](/images/arduino-block/2017-10-14-passive-motion-sensor/step9.jpg)

10) (Challenge) Can you take the current program and change it make the led on the breadboard blink.

![step10](/images/arduino-block/2017-10-14-passive-motion-sensor/step10a.jpg)

![step10](/images/arduino-block/2017-10-14-passive-motion-sensor/step10b.jpg)

Now we are going to hook up the motion sensor.  This motion sensor will send electricity from the S pin to the arduino if it senses    

![back of sensor](/images/arduino-block/2017-10-14-passive-motion-sensor/back-sensor.jpg)

11) Take a male to female jumper wire and plug one side into the S pin and the other side into pin 2 of the arduino.

![step11](/images/arduino-block/2017-10-14-passive-motion-sensor/step11.jpg)

12) Take a male to female jumper wire and plug one side into the + side of the sensor. Take the other side of the wire and plug it into 3.3 volts of the arduino.

![step12](/images/arduino-block/2017-10-14-passive-motion-sensor/step12.jpg)

13) Take a male to female jumper wire and plug one side into the - and the other side into ground (gnd) of the arduino.

![step13](/images/arduino-block/2017-10-14-passive-motion-sensor/step13.jpg)

14) Go back to the block webpage and clear out all the blocks on the page.

![step14](/images/arduino-block/2017-10-14-passive-motion-sensor/step14.png)

We are going to logout the output of pin 2 to see what happens when something is sensed.  But before we do stand up and take 5 deep breaths.  You are doing great!!!

15) Drag the digital read block from the Input/Output toolbox on the screen.  Set it to pin 2.

![step15](/images/arduino-block/2017-10-14-passive-motion-sensor/step15a.png)

![step15](/images/arduino-block/2017-10-14-passive-motion-sensor/step15b.png)

16) Drag the Serial Print Block onto the screen and hook it into the DigitalRead block. Besure and delete the green quotes block.

![step16](/images/arduino-block/2017-10-14-passive-motion-sensor/step16a.png)

![step16](/images/arduino-block/2017-10-14-passive-motion-sensor/step16b.png)

17) Drag the delay block and set the number to 100 milli seconds.

![step17](/images/arduino-block/2017-10-14-passive-motion-sensor/step17a.png)

![step17](/images/arduino-block/2017-10-14-passive-motion-sensor/step17b.png)

18) Click the upload button to upload the code the arduino.

![step18](/images/arduino-block/2017-10-14-passive-motion-sensor/step18.png)

19) Click on logging / debgging to make the serial monitor appear.

![step19](/images/arduino-block/2017-10-12-input-output/step19.png)


20) Notice that serial monitor is prints 0.  Put your hand over the arduino.  Notice that the serial monitor says 1.  Based on this we know that if it senses something it will equal 1.  Otherwise it will equal 0.

![step20](/images/arduino-block/2017-10-12-input-output/step20.png)

21) (Challenge) Try to build a program from scratch that will turn on the led when it senses something and turn it off when it does not sense anything.  This is very similar to the code your wrote in first lesson.  Ask questions if you need help.


22) (Challenge) See how far way an object needs to be fore the led goes off.

23) (Challenge) Use the if block to serial print "I see you" if the sensor outputs 1.

24) Go ahead and stand up and walk around for a minute.  Observe what the other students are doing.  Ask questions and see if you can help anyone out. :)

Next we are going to learn about loops.  Loops are used make stuff run on repeat.  They are often used to go through a list of things.  We are going to use a loop to make the led blink the number of times the sensor has sensed something.  

We are going to create a global variable. Global variables are created out of the normal program loop.  But can we used and changed inside regular code. 

25) Create a global variable called counter and set it's value to 0.

![step25](/images/arduino-block/2017-10-14-passive-motion-sensor/step25b.png)

![step25](/images/arduino-block/2017-10-14-passive-motion-sensor/step25c.png)

![step25](/images/arduino-block/2017-10-14-passive-motion-sensor/step25d.png)

![step25](/images/arduino-block/2017-10-14-passive-motion-sensor/step25e.png)

![step25](/images/arduino-block/2017-10-14-passive-motion-sensor/step25f.png)

26) Drag out the serial print block onto the screen and throw away the quotes block attached to it.

![step26](/images/arduino-block/2017-10-14-passive-motion-sensor/step26a.png)

![step26](/images/arduino-block/2017-10-14-passive-motion-sensor/step26b.png)

27) Drag the counter variable block and connect it to the serial print block.

![step27](/images/arduino-block/2017-10-14-passive-motion-sensor/step27a.png)

![step27](/images/arduino-block/2017-10-14-passive-motion-sensor/step27b.png)

28) Set the counter variable block to itself + 1.

![step28](/images/arduino-block/2017-10-14-passive-motion-sensor/step28a.png)

![step28](/images/arduino-block/2017-10-14-passive-motion-sensor/step28b.png)

![step28](/images/arduino-block/2017-10-14-passive-motion-sensor/step28c.png)

![step28](/images/arduino-block/2017-10-14-passive-motion-sensor/step28d.png)

![step28](/images/arduino-block/2017-10-14-passive-motion-sensor/step28e.png)

![step28](/images/arduino-block/2017-10-14-passive-motion-sensor/step28f.png)

29) Now add a delay block to the end of the block chain.

![step28](/images/arduino-block/2017-10-14-passive-motion-sensor/step29.png)

30) Click upload and upload the program to the arduino.

![step30](/images/arduino-block/2017-10-14-passive-motion-sensor/step30.png)

31) Click on logging / debgging to make the serial monitor appear.

![step31](/images/arduino-block/2017-10-14-passive-motion-sensor/step31.png)

32) Notice that the serial monitor is adding one to the next number.  Go ahead and explain to an instructor happening.  Do this before you move onto the next step.

![step32](/images/arduino-block/2017-10-14-passive-motion-sensor/step32.png)

33) Delete every block except for the global variable counter block.

34) Create a variable named sensor that will store the value of the sensor pin.  

![step34](/images/arduino-block/2017-10-14-passive-motion-sensor/step34.png)

35) Drag the IF block and attach it to the sensor block.

![step35](/images/arduino-block/2017-10-14-passive-motion-sensor/step35a.png)

![step35](/images/arduino-block/2017-10-14-passive-motion-sensor/step35b.png)

36) Drag the compare block onto the screen and attach it to the if block.

![step36](/images/arduino-block/2017-10-14-passive-motion-sensor/step36a.png)

![step36](/images/arduino-block/2017-10-14-passive-motion-sensor/step36b.png)

Remember how if the sensor is on the it will send electricity to the pin in the arduino.  The arduino represents this as a 1.  So we now need to say that if the sensor pin = 1 we want to do something.

37) Drag a number block and the sensor variable into the compare block.  Set the number block equal to 1.

![step37](/images/arduino-block/2017-10-14-passive-motion-sensor/step37.png)

38) (Challenge) Inside the if the block add one to counter.  Try to do this without looking at the pictures below this step.

39) (Challenge) Create a variable inside the IF block that equals 0.  Call it "blink times".

The repeat block is a lot like the IF block.  Except for one key difference.  It repeats the blocks inside the do until the  condition is no longer true.  The repeat block is also known as a while loop.  It will run while something is true.

40) Drag the repeat block onto the screen and put it inside the if block.

![step40](/images/arduino-block/2017-10-14-passive-motion-sensor/step40a.png)

![step40](/images/arduino-block/2017-10-14-passive-motion-sensor/step40b.png)

41) Drag the compare block that was used for the if statement and attach it to the while loop.  Change the equals sign to the less than sign ("<").

![step41](/images/arduino-block/2017-10-14-passive-motion-sensor/step41a.png)

![step41](/images/arduino-block/2017-10-14-passive-motion-sensor/step41b.png)

42) Put in the variable "blink times" for left side of the compare block and put in the counter block for the right side.  What this means is that the blocks in the  do space will run as long as "blank times" is less than counter.

![step42](/images/arduino-block/2017-10-14-passive-motion-sensor/step42.png)

43) Add one to the "blink times" variable block inside the do space.  This way it will not run the forever.  Loops that do not stop are called infinite loops. 

![step43](/images/arduino-block/2017-10-14-passive-motion-sensor/step43.png)

43) (Challenge) Inside the repeat block make the led blink for a second using the delay block and digitalWrite block.  Once you are done upload that to the arduino.

#### Congrats you have done a lot.  You learned about sensor's, global variables, and loops.

## Challenge Projects

- Add another led that turns on and does not blink while the one that is already setup does.  

- Serial Print the number of times the sensor has sensed something.

- Have fun you earned it!!!

## Resources

- [https://www.arduino.cc](https://www.arduino.cc) 
- [Passive Motion Sensor](https://learn.adafruit.com/pir-passive-infrared-proximity-motion-sensor/how-pirs-work) 