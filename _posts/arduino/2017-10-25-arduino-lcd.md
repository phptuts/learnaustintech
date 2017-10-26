---
layout: post
title: Arduino LCD Screen Workbook
excerpt: "Arduino LCD Screen Workbook Work Book."
modified: 2017-10-25
categories: arduino
comments: true
share: true
sort_order: 3
---

## Project Kit

![Project Kit Coming Soon](/images/arduino/2017-10-25-arduino-lcd/kit.jpg)


## Bill of Materials 

- 1 x Arduino Uno
- 4 x jumper wires (male to female)
- 1 x usb type b cable

## Steps

Before you begin be sure you have the [arduino ide](https://www.arduino.cc/en/Main/Software) installed.  You might want to review the [class presentation](https://docs.google.com/presentation/d/1NVXJuoGbR-pNWjyHMJpdIDgtxiLFyZJTAl8aILhjp4g/edit?usp=sharing)
if you found this on the internet.

1) Turn the lcd screen on it's back side and notice that it 4 pins connected to it.  You can read more about it [here](http://i2c.info/i2c-bus-specification)

- ground (gnd)
- vcc (volts / +)
- sda (Serial Data Line)
- slc ( Serial Clock Line)
    
![step1](/images/arduino/2017-10-25-arduino-lcd/step1.jpg)

2) Take one of the wires and plug it into ground of the lcd screen and ground of the arduino.

![step2](/images/arduino/2017-10-25-arduino-lcd/step2.jpg)

3) Take one of the wires and plug it into vcc of the lcd screen and 5v of the arduino.

![step3](/images/arduino/2017-10-25-arduino-lcd/step3.jpg)

4) Take one of the wires and plug it into sda of the lcd screen and A4 of the arduino.

![step4](/images/arduino/2017-10-25-arduino-lcd/step4.jpg)

5) Take one of the wires and plug it into scl of the lcd screen and A5 of the arduino.

![step5](/images/arduino/2017-10-25-arduino-lcd/step5.jpg)

6) Take the arduino and plug it into the computer.

![step5](/images/arduino/2017-10-25-arduino-lcd/step6.jpg)
