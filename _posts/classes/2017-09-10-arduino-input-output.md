---
layout: post
title: Arduino 101 Input & Output Work Book
excerpt: "Arduino Basic."
modified: 2017-09-10
categories: articles
comments: true
share: true
---

## Project Kit For the Workbook

![kit](/images/2017-09-10-arduino-input-output/kit.jpg)
 

### Bill of Materials 

- 1 x Arduino Uno
- 1 x led 
- 1 x 220 Ohm Resistor
- 2 x jumper wires
- 2 x regular wires 
- 1 x push button
- 1 x usb type b cable


## Steps

Before you begin be sure you have the [arduino ide](https://www.arduino.cc/en/Main/Software) installed.  You might want to review the [class presentation](https://docs.google.com/presentation/d/1MoRwCLQkwIvOVirSYqP_qpZK4cVCWzgDfzAIcsbjcqk/edit?usp=sharing)
if you found this on the internet.

### Step 1) Take the long side of led place it into breadboard (5,f) and short side into (7, f)

![step1](/images/2017-09-10-arduino-input-output/step1.jpg)

### Step 2) Take the resistor and plug one end into (5, g) and the other end into (2, i)

![step2](/images/2017-09-10-arduino-input-output/step2.jpg)

### Step 3) Take one jumper wire and plug into (7, j) and the other jumper wire and plug into (2, j)

![step3](/images/2017-09-10-arduino-input-output/step3.jpg)

### Step 4) Take jumper wire plugged into (2, j) and plug it into pin 4 of the arduino

![step4](/images/2017-09-10-arduino-input-output/step4.jpg)

### Step 5) Take jumper wire plugged into (7, j) and plug it into ground (gnd) in the arduino

![step5](/images/2017-09-10-arduino-input-output/step5.jpg)

### Step 6) Take one of the wires plugged into the button and put it into pin 5

![step6](/images/2017-09-10-arduino-input-output/step6.jpg)

### Step 7) Take the over wire and plug it into ground (gnd)

![step7](/images/2017-09-10-arduino-input-output/step7.jpg)

### Step 8) Plug the usb cord into the arduino

![step8](/images/2017-09-10-arduino-input-output/step8.jpg)

### Step 9) Open the ide and put copy the code

```
int btn = 5;
int led = 4;

void setup() {
  // put your setup code here, to run once:
  pinMode(btn, INPUT);
  pinMode(led, OUTPUT);
}

void loop() {
  // Because this means that btn is pressed and 
  // and that electricity is flowing toward ground
  if (digitalRead(btn)) {
     digitalWrite(led, HIGH);
  }
  else {
     digitalWrite(led, LOW);
  }

  delay(100);
}
```

### Step 10) Select the usb port for the arduino (tools -> ports )

![step10](/images/2017-09-10-arduino-input-output/step10.png)


### Step 11) Click the upload button on the arduino id

![step11](/images/2017-09-10-arduino-input-output/step11.png)

### Step 12) Play with the final project

![finalprojectoff](/images/2017-09-10-arduino-input-output/final-result-btn-off.jpg)

![finalprojecton](/images/2017-09-10-arduino-input-output/final-result-btn-on.jpg)


## Challenge Projects

- Write code so the push button can act like a light switch.  You push it once and it turns on the light and you push it again it turns off light.  So it does not require continually pushing.

- Make it so that the light blinks the number of times the button has been pushed

- Just have fun and do what you want :)