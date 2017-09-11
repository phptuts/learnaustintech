---
layout: post
title: Build An Arduino Motion Sensor With Led
excerpt: "Arduino Passive Motion Sensor (PIR)."
modified: 2017-09-11
categories: articles
comments: true
share: true
---

## Project Kit

![step1](/images/2017-09-11-arduino-passive-motion-sensor/kit.jpg)


## Bill of Materials 

- 1 x Arduino Uno
- 1 x led 
- 1 x 220 Ohm Resistor
- 2 x jumper wires (male to male)
- 3 x jumper wires (male to female)
- 1 x passive motion sensor (pir)
- 1 x breadboard
- 1 x usb type b cable

## Steps

Before you begin be sure you have the [arduino ide](https://www.arduino.cc/en/Main/Software) installed.  You might want to review the [class presentation](https://docs.google.com/presentation/d/1NVXJuoGbR-pNWjyHMJpdIDgtxiLFyZJTAl8aILhjp4g/edit?usp=sharing)
if you found this on the internet
### Step 1) Take the led and put the long side (positive) into (5, 3) and short side (negative) into (3, e) of the breadboard.

![step1](/images/2017-09-11-arduino-passive-motion-sensor/step1.jpg)

### Step 2) Take the resistor and plug one end into (5, d) and the other end into (8, b).

![step2](/images/2017-09-11-arduino-passive-motion-sensor/step2.jpg)

### Step 3) Plug one end of the male to male jumper wire into (2, a) and take the other jumper wire into (8, a).

![step3](/images/2017-09-11-arduino-passive-motion-sensor/step3.jpg)

### Step 4) Take the jumper wire plugged into (8, a) into arduino pin 7.

![step4](/images/2017-09-11-arduino-passive-motion-sensor/step4.jpg)

### Step 5) Take the other jumper wire and plug it into ground (gnd) in the arduino.

![step5](/images/2017-09-11-arduino-passive-motion-sensor/step5.jpg)

### Step 6) Take a female to male wire and plug the s into pin 4 of the arduino

![step6](/images/2017-09-11-arduino-passive-motion-sensor/step6.jpg)

### Step 7) Take a female to male wire and plug the - (ground) into the ground (gnd) of the arduino

![step7](/images/2017-09-11-arduino-passive-motion-sensor/step7.jpg)

### Step 8) Take a female to male wire and plug the + (volts) into 3.3 volt of the arduino

![step7](/images/2017-09-11-arduino-passive-motion-sensor/step7.jpg)

It should like this when you are done.

![lookslike](/images/2017-09-11-arduino-passive-motion-sensor/looklike.jpg)

### Step 9) Plug in the arduino into the computer

![lookslike](/images/2017-09-11-arduino-passive-motion-sensor/looklike.jpg)

### Step 10) Open the arduino ide and paste the code in below.

```

int led = 7;
int pirSensor = 4;

void setup() {
  // put your setup code here, to run once:
  pinMode(pirSensor, INPUT_PULLUP);
  pinMode(led, OUTPUT);
  Serial.begin(9200);
}

void loop() {
  // put your main code here, to run repeatedly:
  if (digitalRead(pirSensor)) {
        Serial.println("Sensed Something");
        digitalWrite(led, HIGH);
  }
  else {
      digitalWrite(led, LOW);
      Serial.println("Sensed Nothing");
  }

  delay(500);
}
```

### Step 11) Select the port in the arduino ide that your board is hooked up to

![step12](/images/2017-09-11-arduino-passive-motion-sensor/step11.png)

### Step 12) Upload the arduino sketch

![step12](/images/2017-09-11-arduino-passive-motion-sensor/step12.png)

## Challenge Projects

- Count the number of times that sensor has found something and display that in the serial monitor. 

- Use Serial.readStringUntil to build something that you can use to send commands to the arduino and control the 
delay in the program.

- Do your own thing and build something on top it, aka just have fun. :)
