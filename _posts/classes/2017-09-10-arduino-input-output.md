---
layout: post
title: Arduino 101 Input & Output Work Book
excerpt: "Arduino Basic."
modified: 2017-09-17
categories: articles
comments: true
share: true
---

## Project Kit For the Workbook

![kit](/images/2017-09-10-arduino-input-output/kit.jpg)
 

## Bill of Materials 

- 1 x Arduino Uno
- 1 x led 
- 1 x 220 Ohm Resistor
- 2 x jumper wires
- 2 x regular wires 
- 1 x push button
- 1 x breadboard
- 1 x usb type b cable


## Steps

Before you begin be sure you have the [arduino ide](https://www.arduino.cc/en/Main/Software) installed.  You might want to review the [class presentation](https://docs.google.com/presentation/d/1MoRwCLQkwIvOVirSYqP_qpZK4cVCWzgDfzAIcsbjcqk/edit?usp=sharing)
if you found this on the internet.

1) Adjust the arduino setting / preferences to include line numbers and click Ok.

![step1a](/images/2017-09-10-arduino-input-output/step1a.png)

![step1b](/images/2017-09-10-arduino-input-output/step1b.png)


2) Plug the arduino into the computer.

![step2a](/images/2017-09-10-arduino-input-output/step2a.jpg)

![step2b](/images/2017-09-10-arduino-input-output/step2b.jpg)

3) Go to tools -> boards -> and select the (Arduino/Genuino Uno)

![step3](/images/2017-09-10-arduino-input-output/step3.png)

4) Go to tools -> ports -> and select the usb port the arduino is plugged into.

![step4](/images/2017-09-10-arduino-input-output/step4.png)

5) Go to files -> examples -> and select blink program.

![step5](/images/2017-09-10-arduino-input-output/step5.png)

6) Now click the upload button on the arudino ide.  It looks like a play button.

![step6](/images/2017-09-10-arduino-input-output/step6.png)

7) The arduino should now blink every second.  Congrats!! You uploaded your first arduino program.  Remember that pin 13, is the built in led.  The red circle is where pin 13 is.

![step7a](/images/2017-09-10-arduino-input-output/step7a.jpg)

![step7b](/images/2017-09-10-arduino-input-output/step7b.jpg)

8) The take breadboard and put the positive (long end) of the led into (3, f) and the short end into (5, f) of the breadboard.

![step8](/images/2017-09-10-arduino-input-output/step8.jpg)

9) Take the resistor and plug that into (3, g) and (1, i) of the breadboard.

![step9](/images/2017-09-10-arduino-input-output/step9.jpg)

10) Take one jumper wire and plug it into pin (1, j) and the other jumper wire and plug it into (5,j).

![step10](/images/2017-09-10-arduino-input-output/step10.jpg)

11) Take the jumper wire plugged into (1,j) and plug it into pin 7 of the arduino.

![step11](/images/2017-09-10-arduino-input-output/step11.jpg)

12) Take the other jumper wire and plug it into ground of the arduino.

![step12](/images/2017-09-10-arduino-input-output/step12.jpg)

13) Now open a new arduino sketch and paste in this code and paste the code in below.

![step13](/images/2017-09-10-arduino-input-output/step13.png)

```
// This is the pin connected to the led
int led = 7;

void setup() {
  // Here we are saying that the pin will be an output pin
  // This means that this pin will output electricity.
  pinMode(led, OUTPUT);

}

void loop() {
  // This will turn the led on
  digitalWrite(led, HIGH);
  // This will make the program wait 1 second
  delay(1000);
  // This will turn the led off
  digitalWrite(led, LOW);
  // This will make the program wait another second
  delay(1000);
}

```

14) Now upload the arduino sketch like you did in step 6.  You should see the led blink.

![step14a](/images/2017-09-10-arduino-input-output/step14a.jpg)

![step14b](/images/2017-09-10-arduino-input-output/step14b.jpg)

15) Next we are going to hook up the button.  Take one end of the push button and plug that into ground (gnd).

![step15](/images/2017-09-10-arduino-input-output/step15.jpg)

16) Plug the other wire of the button into pin 3.

![step16a](/images/2017-09-10-arduino-input-output/step16a.jpg)

![step16b](/images/2017-09-10-arduino-input-output/step16b.jpg)

17) Now paste the code in below.

``` 
// This is the pin connected to the led
int led = 7;
int button = 3;

void setup() {
  // Here we are saying that the pin will be an output pin
  // This means that this pin will output electricity.
  pinMode(led, OUTPUT);
  pinMode(button, INPUT_PULLUP);
}

void loop() {

  if (digitalRead(button) == false) {
     digitalWrite(led, HIGH);
  }
  else {
     digitalWrite(led, LOW);
  }
  
}
```

18) Upload the code like you did in steps 6 and 14 to the arduino.  When u push the button the light should go on.

![step18a](/images/2017-09-10-arduino-input-output/step18a.jpg)

![step18b](/images/2017-09-10-arduino-input-output/step18b.jpg)



## Challenge Projects

- Write code so the push button can act like a light switch.  You push it once and it turns on the light and you push it again it turns off light.  So it does not require continually pushing.

- Make it so that the light blinks the number of times the button has been pushed

- Just have fun and do what you want :)

## Resources

- [https://www.arduino.cc](https://www.arduino.cc) 
- [http://www.instructables.com/id/Arduino-Projects/](http://www.instructables.com/id/Arduino-Projects/) 
- [https://create.arduino.cc/projecthub](https://create.arduino.cc/projecthub) 
- [https://circuitdigest.com/arduino-projects](https://circuitdigest.com/arduino-projects) 
- [https://makezine.com](https://makezine.com)