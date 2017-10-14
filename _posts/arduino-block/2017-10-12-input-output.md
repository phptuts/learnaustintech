---
layout: post
title: Arduino 101 Input & Output With Blocks
excerpt: "Arduino Basic with blocks."
modified: 2017-10-12
categories: arduino_block
comments: true
share: true
sort_order: 1
---

## Project Kit For the Workbook

![kit](/images/arduino-block/2017-10-12-input-output/kit.jpg)
 

## Bill of Materials 

- 1 x Arduino Uno
- 1 x led 
- 1 x 220 Ohm Resistor
- 3 x jumper wires
- 2 x regular wires 
- 1 x push button
- 1 x breadboard
- 1 x usb type b cable


## Steps


1) Install the [Arduino IDE](https://www.arduino.cc/en/Main/Software) for your Operating System.

2) Install [python 2.7](https://www.python.org/downloads/release/python-2713/) for your Operating System.

3) Open a command prompt / terminal and type in python --version.  Make sure you see something like this.

![step3](/images/arduino-block/2017-10-12-input-output/step3.png)

4) [Download](https://github.com/phptuts/blocklyarduinoclass/archive/master.zip) the block environment and move it your desktop.  Rename the folder to ArduinoBlocks.

5) In the command prompt type:
``` 
cd ~/Desktop/ArduinoBlocks/ 
``` 
![step4](/images/arduino-block/2017-10-12-input-output/step5.png)

6) In the command prompt type:
``` 
python arduino_web_server.py 
``` 
![step6](/images/arduino-block/2017-10-12-input-output/step6.png)

7) Now open your [Block Environment](http://127.0.0.1:8080/), http://127.0.0.1:8080/.  Click on Discard if you see blocks on the screen.

![step7](/images/arduino-block/2017-10-12-input-output/step7.png)

So you are going to learn how to control the arduino.  You will do this by dragging blocks onto the screen.  Each block represents something that the arduino will do.  The first thing we are going to learn how to do is send electricity to the pin.  The blocks you drag onto the screen will be executed for ever.  Meaning that program will repeat itself until the arduino is unplugged.

8) Click on Input/Output and drag the DigitalWrite block.  Change the pin to 13 and make sure Stat is HIGH.  High means that the electricity will be sent through that pin.

![step8a](/images/arduino-block/2017-10-12-input-output/step8a.png)

![step8b](/images/arduino-block/2017-10-12-input-output/step8b.png)

9) Plug the arduino into the computer.

![step9a](/images/arduino-block/2017-10-12-input-output/step9a.jpg)

![step9b](/images/arduino-block/2017-10-12-input-output/step9b.jpg)

10) Click the upload button.  This will upload program to the arduino.  Once you are done you should see a yellow light.  That yellow light is the arduino's built in led.  When you send electricity through pin 13 that led will light up.

![step10a](/images/arduino-block/2017-10-12-input-output/step10a.png)

![step10b](/images/arduino-block/2017-10-12-input-output/step10b.png)

![step10c](/images/arduino-block/2017-10-12-input-output/step10c.png)

![step10d](/images/arduino-block/2017-10-12-input-output/step10d.jpg)

11) Take the led and plug the long end of the led and put into (3, e) of the breadboard and the short end into (5, e).

![step11](/images/arduino-block/2017-10-12-input-output/step11.jpg)

12) Take a male to male jumper wire and plug it into (5, d) and the blue line of the breadboard.

![step12](/images/arduino-block/2017-10-12-input-output/step12.jpg)

13) Take the resistor and plug it into the blue line, leave one space at the end.

![step13](/images/arduino-block/2017-10-12-input-output/step13.jpg)

14) Take a male to male jumper wire and plug it into (gnd) ground of the arduino and the end space of the blue line on the breadboard.

![step14](/images/arduino-block/2017-10-12-input-output/step14.jpg)

15) Take a male to male jumper wire and plug it into pin 7 of the arduino and (3, d) of the breadboard.

![step15](/images/arduino-block/2017-10-12-input-output/step15.jpg)

16) (Challenge) Can you change the program to make led light up by sending electricity to pin 7.  To see your change click the upload button on the block web page.  If you have trouble ask for help. :)

![step16](/images/arduino-block/2017-10-12-input-output/step16.jpg)

17) (Challenge) Move the wire to that is plugged into pin 7 to pin 8.  Then change the blocks to make the led light up.

![step17](/images/arduino-block/2017-10-12-input-output/step17.jpg)


 Now it's time to make to Led blink.  To do that we are going to learn a new block called delay.  Delay pauses the program for period of time.  The number you put in delay determines how many milliseconds the program will pause.  A millisecond is 1/1000 of a second.

18) Open the control block and drag delay on screen.  Then connect that block to the DigitalWrite Block.

![step18](/images/arduino-block/2017-10-12-input-output/step18a.png)

![step18](/images/arduino-block/2017-10-12-input-output/step18b.png)

So the DigitalWrite Block takes 2 inputs, the pin number and (HIGH / LOW).  If it is set to HIGH it will send electricity to the pin.  If it is set to LOW it will not send electricity to the pin.

19) Drag the DigitalWrite Block on the screen and connect it to the delay block.  Set it to  LOW.

![step19](/images/arduino-block/2017-10-12-input-output/step19a.png)

![step19](/images/arduino-block/2017-10-12-input-output/step19b.png)

20) Now Drag another delay block onto screen and connect it to the block chain.

![step20](/images/arduino-block/2017-10-12-input-output/step20a.png)

![step20](/images/arduino-block/2017-10-12-input-output/step20b.png)

21) Now click the upload button. 

![step21](/images/arduino-block/2017-10-12-input-output/step21.png)

22) (Challenge) Notice that led does not blink. Can you fix the blocks to make the led blink.  What you are doing is called debugging.  Debugging is fixing something that is wrong with a program.  A bug is what is wrong with the code. 

![step22](/images/arduino-block/2017-10-12-input-output/step22a.jpg)

![step22](/images/arduino-block/2017-10-12-input-output/step22b.jpg)

23) (Challenge) Can you make the led stay on for 2 seconds (2000 milliseconds).

Congrats!! You have just written your first complete arduino program.  Go ahead and stand up and walk around for a minute.  

24) Now we are going to delete all the code you have written.  If you want to save it click on Save XML and store it some where you can find it later.  

![step24](/images/arduino-block/2017-10-12-input-output/step24a.png)

![step24](/images/arduino-block/2017-10-12-input-output/step24b.png)

25) Now plug in the button.  Plug ond wire into ground (gnd) and the other end into pin 2 of the arduino.

![step25](/images/arduino-block/2017-10-12-input-output/step25a.jpg)

![step25](/images/arduino-block/2017-10-12-input-output/step25b.jpg)

26) Now drag DigitalRead with PULLUP RESISTOR block to screen.  Set the block to pin number 2.

![step26](/images/arduino-block/2017-10-12-input-output/step26a.png)

![step26](/images/arduino-block/2017-10-12-input-output/step26b.png)

27) Drag the Serial Print Block onto the screen.  This block is used to send messages to your computer from the arduino.

![step27](/images/arduino-block/2017-10-12-input-output/step27.png)


28) Connect the Serial Print Block to the Digital Read Block and throw away the green block with quotes.

![step28](/images/arduino-block/2017-10-12-input-output/step28.png)

29) Connect the delay block to the bottom of the serial block.  Set the number in the delay block to 100.  This means that arduino will pause for a 10th of a second.

![step29](/images/arduino-block/2017-10-12-input-output/step29.png)

30) Upload the program to the arduino.

![step29](/images/arduino-block/2017-10-12-input-output/step30.png)

31) Open the arduino ide and go to tools -> ports and select the usb port the arduino is on.

![step31](/images/arduino-block/2017-10-12-input-output/step31.png)

32) Go to tools -> serial monitor.  Notice that this output is 1.  If you press the button it will start to output 0.  So when the button is pressed the block reads 0.  Once you are done with the step be sure and close the serial monitor.

![step32](/images/arduino-block/2017-10-12-input-output/step32a.png)

![step32](/images/arduino-block/2017-10-12-input-output/step32b.png)

The Serial Block is a great way to help debug your code. :)

33) Now we are going to learn about variables. A variable is how we store data in the arduino.  Go ahead and delete all the blocks and pull out variable block.

![step33](/images/arduino-block/2017-10-12-input-output/step33a.png)

![step33](/images/arduino-block/2017-10-12-input-output/step33b.png)

34) Now rename the variable to btn, for button. We will use this variable to store 0 or 1 for the button push.

![step34](/images/arduino-block/2017-10-12-input-output/step34a.png)

![step34](/images/arduino-block/2017-10-12-input-output/step34b.png)

![step34](/images/arduino-block/2017-10-12-input-output/step34c.png)

35) Now drag the  DigitalRead Input PULLLUP Resistor Block and connect it to the btn variable block.  Set the pin number to 2.

![step35](/images/arduino-block/2017-10-12-input-output/step35a.png)

![step35](/images/arduino-block/2017-10-12-input-output/step35b.png)

Now we are going to learn about if blocks.  If blocks are used to make decisions in your program.  If what is connected to the if block is true it will do all the blocks in the do space.  Let's build something to make this concept more clear.


36) Drag the If block and connect it to the bottom of the variable block.

![step36](/images/arduino-block/2017-10-12-input-output/step36a.png)

![step36](/images/arduino-block/2017-10-12-input-output/step36b.png)

37) Now drag the compare block onto the screen and connect it to the if block.  So if what is on the right and left side equal each other the arduino will run the blocks in the do space.  

![step37](/images/arduino-block/2017-10-12-input-output/step37a.png)

![step37](/images/arduino-block/2017-10-12-input-output/step37b.png)

38) Go into the variable blocks and drag the btn block into the first part compare block.  The btn block is variable that we created earlier.

![step38](/images/arduino-block/2017-10-12-input-output/step38a.png)

![step38](/images/arduino-block/2017-10-12-input-output/step38b.png)

39) Now go to the math section and drag the number block the second part of the compare block.

![step39](/images/arduino-block/2017-10-12-input-output/step39a.png)

![step39](/images/arduino-block/2017-10-12-input-output/step39b.png)

40) Drag Digital Write Block into the do space.  Set the pin to 8.

![step40](/images/arduino-block/2017-10-12-input-output/step40a.png)

![step40](/images/arduino-block/2017-10-12-input-output/step40b.png)

41) Upload program to the arduino and push the button.  Notice that when u stopped pressing the button the light continues to stay on.  Can you tell me why?

![step41](/images/arduino-block/2017-10-12-input-output/step41a.png)

![step41](/images/arduino-block/2017-10-12-input-output/step41b.jpg)


42) (Challenge) Can you create another IF block that will turn the led off when you stop pressing the button?

![step42](/images/arduino-block/2017-10-12-input-output/step42a.jpg)

![step42](/images/arduino-block/2017-10-12-input-output/step42b.jpg)


## Challenge Projects

- Make it so that when you push the button the led blinks 2 times.

- Ask for a second led and wire set.  Hook the other led to the side of the led in the breadboard.  Make it so that when you push the button it makes the right led on and the left led off.  And when you don't push the button make it so that the opposite happens. You will want to hook the short side of the led to the blue end of the breadboard and the long side of the led to pin 4 of the arduino. 

- Just have fun and do what you want :)

## Resources

- [https://www.arduino.cc](https://www.arduino.cc) 
- [http://www.instructables.com/id/Arduino-Projects/](http://www.instructables.com/id/Arduino-Projects/) 
- [Blockly, the language](https://developers.google.com/blockly/)
- [The github project this was based on.](https://github.com/BlocklyDuino/BlocklyDuino)