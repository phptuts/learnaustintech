---
layout: post
title: Wifi Controlled Christmas Lights Using Node and ESP8266 Chip
excerpt: "Wifi Controlled Christmas Lights Using Node Js and ESP8266 Chip"
modified: 2017-09-13
categories: articles
comments: true
share: true
---

## Project Kit 

![kit1](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/kit1.jpg)

## Bill of Materials 

- 1 x ESP8266
- 1 x led addressable light strip 5v   
- 2 x jumper wires (male to male)
- 3 x jumper wires (male to female)
- 1 x 5 volt / 3 amp dc power cord
- 1 x Female DC Power Jack Adapter Plug
- 1 x breadboard
- 1 x micro usb cord

## Project Setup

### Step 1) Put the ESP8266 Chip in the breadboard.

![step1a](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step1a.jpg)

![step1b](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step1b.jpg)

### Step 2) Insert the DC Power Jack Adapter into the power cord.

![step2](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step2.jpg)

### Step 3) Take male to male jumper wire and put one side into the positive end of the power adapter and the other end the red wire of led light strip.  Screw the wire down on the power adapter side.

![step3a](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step3a.jpg)

![step3b](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step3b.jpg)

![step3c](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step3c.jpg)

![step3c](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step3d.jpg)

### Step 4) Hook in the male to male wire to ground of the power adapter.

![step4a](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step4a.jpg)

![step4b](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step4b.jpg)

### Step 5) Hook the other end of the male to male wire into the breadboard (28, d).

![step5](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step5.jpg)

### Step 6) Take the other male to male jumper wire put into the breadboard (28, c) and ground (gnd) on the ESP 8266 Chip.  For me the that is (22, i).  But you should be able to (gnd) port on the board.

![step6](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step6.jpg)

### Step 7) Take the male to female jumper wire and hook it into the middle wire of the led light strip.

![step7](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step7.jpg)

### Step 8) Take the other end of the male to female wire and put that into D6 of the ESP8266. 

![step8](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step8.jpg)

### Step 9) Take the other end of the male to female wire and put it into ground (white) wire of the led light strip.

![step9](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step9.jpg)

### Step 10) Take the other end of that wire and place it in (28, b) of the breadboard.  (Notice that the esp8266 and led stripe share the same ground).


![step10](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step10.jpg)

## Code Setup

### Step 1) Open the arduino IDE and go to setting / preferences.

![step1-code](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step1-code.png)

### Step 2) Add this http://arduino.esp8266.com/stable/package_esp8266com_index.json to the board manager in the setting.

![step2-code](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step2-code.png)

### Step 3) Go to Tools -> Boards -> Board Manager and search for esp8266.  Then install the latest esp8266 board.

![step3-code](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step3-code.png)

### Step 4) Install the latest version esp8266 library.

![step4-code](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step4-code.png)

### Step 5) Install the [ada fruit neo pixel library](https://github.com/adafruit/Adafruit_NeoPixel).  Download the zip file. Then go to tools -> include library -> add zip and that zip file.  

![step5-code](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step5-code.png)

### Step 6) Create a new sketch in your arduino ide.

![step5-code](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step6-code.png)

### Step 7) Paste this code into your arduino ide.

```
#include <Adafruit_NeoPixel.h>
#include <ESP8266WiFi.h>
#include <WiFiClient.h>
#include <ArduinoJson.h>

#ifdef __AVR__
  #include <avr/power.h>
#endif

/**
 * The number lights in your led strip
 */
#define NUMPIXELS      30

/**
 * The default time before request another pattern.  It's in milliseconds so it would be 10 seconds
 */
int intervalToCheckTime = 10000;

/** 
 *  The time in the future to check the web for a new pattern.  We set it to zero, it will be set correctly in the web request
 */
int checkTimeInNumberOfSeconds = 0;

// When we setup the NeoPixel library, we tell it how many pixels, and which pin to use to send signals.
// Note that for older NeoPixel strips you might need to change the third parameter--see the strandtest
// example for more information on possible values.
Adafruit_NeoPixel pixels = Adafruit_NeoPixel(NUMPIXELS, D6, NEO_GRB + NEO_KHZ800);

WiFiClient client;

/** 
 *  WIFI STUFF
 */
const char* ssid = "ATXHackerspace";//type your ssid
const char* password = "hackon!!";//type your password
const char* host = "christmaslights.noahglaser.net";
const uint16_t port = 80;

/**
 * The number represents the max frame / lights a pattern can affect
 */
const int MAX_FRAMES = 250;

/**
 * This represents a frame.
 */
struct RGB_LIGHT {
  int red;
  int green;
  int blue;
  int lightPosition;
  int delayTime;
  /**
   * If skip is true we break 
   */
  boolean skip;
};

/**
 * The pattern / frames used to turn on and off the lights
 */
RGB_LIGHT lights[MAX_FRAMES];

void setup() {
  // This is for Trinket 5V 16MHz, you can remove these three lines if you are not using a Trinket
#if defined (__AVR_ATtiny85__)
  if (F_CPU == 16000000) clock_prescale_set(clock_div_1);
#endif
  // End of trinket special code

  pixels.begin(); // This initializes the NeoPixel library.
  Serial.begin(115200);
  delay(10);

  // We start by connecting to a WiFi network

  Serial.println();
  Serial.println();
  Serial.print("Connecting to ");
  Serial.println(ssid);
  
  /* Explicitly set the ESP8266 to be a WiFi-client, otherwise, it by default,
     would try to act as both a client and an access-point and could cause
     network-issues with your other WiFi-devices on your WiFi-network. */
  WiFi.mode(WIFI_STA);
  WiFi.begin(ssid, password);
  
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }

  Serial.println("");
  Serial.println("WiFi connected");  
  Serial.println("IP address: ");
  Serial.println(WiFi.localIP());
  
  clearLights();
  webRequest();
  checkTimeInNumberOfSeconds = millis() + intervalToCheckTime;

}

void loop() {
  
  if (checkTimeInNumberOfSeconds > millis()) {
     for(int frameNumbers=0; frameNumbers < MAX_FRAMES; frameNumbers++){
        if (lights[frameNumbers].skip == false) {
            pixels.setPixelColor(lights[frameNumbers].lightPosition, pixels.Color(lights[frameNumbers].red,lights[frameNumbers].green,lights[frameNumbers].blue)); 
            pixels.show(); 
            delay(lights[frameNumbers].delayTime);
        }
        else {
           break;
        }
    }
  }
  else {
       webRequest();
       Serial.println("NEW PATTERN");
       // Sets the time to check the web for a new pattern
       checkTimeInNumberOfSeconds = millis() + intervalToCheckTime;
  }
}

/**
 * Clears all the lights 
 */
void clearLights() {
      for (int i = 0; i < NUMPIXELS; i += 1) {
         pixels.setPixelColor(i, pixels.Color(0,0,0)); 
         pixels.show();
      }
}

/** 
 *  Clears the array of RGB_LIGHTS
 */
void clearArrayOfLights() {
  for(int i=0; i < MAX_FRAMES; i++){
      lights[i] = {0,0,0, 0, 0, true};
  }
}

/**
 * Makes the web request to get the light pattern
 */
void webRequest() {
    String jsonString = "";
    if (client.connect(host, port)) {
          String url =  "/leds";
          client.println("GET " + url + " HTTP/1.1");
          client.println("Host: "+ (String)host);
          client.println("User-Agent: Arduino/1.0");
          client.println("Connection: close");
          client.println();
          client.println();
          while (client.connected()) {
         
            client.readStringUntil('|');
            jsonString = client.readStringUntil('\n');
      
          }
          parseJSONFromServer(jsonString);
    }
    else {
      Serial.println("NOT CONNECTED");
    }
}


/** 
 *  Parses the json string
 */
void parseJSONFromServer(String jsonString)
{
     DynamicJsonBuffer  jsonBuffer;
    // Root of the object tree.
    //
    // It's a reference to the JsonObject, the actual bytes are inside the
    // JsonBuffer with all the other nodes of the object tree.
    // Memory is freed when jsonBuffer goes out of scope.
    JsonObject& root = jsonBuffer.parseObject(jsonString);

 
  
    // Test if parsing succeeds.
    if (!root.success()) {
      Serial.println("parseObject() failed JSON STRING");
      Serial.println(jsonString);
      return;
    }

  JsonArray& reds = root["reds"].asArray();
  JsonArray& greens = root["greens"].asArray();
  JsonArray& blues = root["blues"].asArray();
  JsonArray& lightPositions = root["lightPositions"].asArray();
  JsonArray& delayTimes = root["delayTimes"].asArray();
  intervalToCheckTime = root["requestTime"];
  clearArrayOfLights();
  for (int i = 0; i < reds.size(); i += 1) {
       lights[i] = { 
                reds.get<int>(i),
                greens.get<int>(i),
                blues.get<int>(i), 
                lightPositions.get<int>(i), 
                delayTimes.get<int>(i),
                false
       };
  }
}


/** 
 *  A debuggin function for seeing the light pattern
 */
void printLights() {
  Serial.println("LIGHT PATTERN");
  for (int frameNumbers = 0; frameNumbers < MAX_FRAMES; frameNumbers += 1) {
         if (lights[frameNumbers].skip) {
             break;
         }
         Serial.print("FRAME  " + String(frameNumbers, 10));
         Serial.print(" RED " + String(lights[frameNumbers].red, 10));
         Serial.print(" GREEN " + String(lights[frameNumbers].green, 10));
         Serial.print(" BLUE " + String(lights[frameNumbers].blue, 10));
         Serial.print(" LIGHT POSITION " + String(lights[frameNumbers].lightPosition, 10));
         Serial.print(" DELAY TIME " + String(lights[frameNumbers].delayTime, 10));
         Serial.println();
  }
}  
```

### Step 8) SignUp For a free [cloud9](https://c9.io/) account.  I would recommend you use your github account for authentication.

### Step 9) Create a new workspace in your cloud 9 dashboard.  At the time of this writing it's in the top right corner of the page.

![step9-code](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step9-code.png)

### Step 10) Next fill in the name of the work space and put in this in the git clone project url.  (https://github.com/phptuts/arduinochristmaslights.git)  Then select the node template.  Then click create workspace.

![step10-code](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step10-code.png)

### Step 11) Then click on app.js and click run on cloud 9 interface.  This will run start the server.
 
![step11-code](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step11-code.png)

### Step 12) Then copy the url in the console.  In my case its "https://arduino-christmas-lighting-nglaser.c9users.io".

![step12-code](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step12-code.png)

### Step 13) Change the host variable to use the host you url copied from the cloud 9 terminal.  Also change the wifi password and ssid variables. The ssid is the name of your wifi network.

![step13-code](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step13-code.png)

### Step 14) Hook the micro usb cord into the esp8266 chip.  Then select the port that it is on.

![step14-code](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step14-code.png)

### Step 15) Select the esp8266 board.  In our case it's ESP-12 E model.

![step15-code](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step15-code.png)

### Step 16) Upload the sketch to the esp8266 chip.

![step16-code](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step16-code.png)

### Step 17) Go to website you copied into the arduino ide and play around with the user interface.  You can do default patterns or use the pipe system to create your own.  If u are using kit one select 30 leds for the default pattern.  If you are using kit 3 use 60 leds.

![step16-code](/images/2017-09-13-esp8266-wifi-controlled-christmas-lights/step17-code.png)


### Step 18) Hook the tree and have fun. :) You can see the demo here.

<iframe src="https://www.facebook.com/plugins/video.php?href=https%3A%2F%2Fwww.facebook.com%2Fnoah.glaser.75%2Fvideos%2F1437675766280514%2F&show_text=1&width=560" width="560" height="464" style="border:none;overflow:hidden" scrolling="no" frameborder="0" allowTransparency="true" allowFullScreen="true"></iframe>

## Resources

- [https://github.com/adafruit/Adafruit_NeoPixel](https://github.com/adafruit/Adafruit_NeoPixel)
- [https://github.com/esp8266/Arduino](https://github.com/esp8266/Arduino)
- [Arduino JSON Library](https://github.com/bblanchon/ArduinoJson)
- [Arduino Http Library](https://www.arduino.cc/en/Tutorial/HttpClient)