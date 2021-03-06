﻿# Twitter Mentions on ESP8266 MAX7219 Dot Matrix

Let’s say that you don’t have your smartphone around and someone mentions you on twitter. Wouldn’t it be nice to have a display that automatically reads your twitter mentions and show it on a scrolling display? So let’s build a internet controlled (IoT) dot-matrix display that does this for us using an ESP8266.

[![ESP8266 Twitter Mentions Display](https://img.youtube.com/vi/JTxpx9XMpjU/0.jpg)](http://www.youtube.com/watch?v=JTxpx9XMpjU)

The plan to accomplish this is as follows:

1. Someone mentions us on twitter (in my case @debsahu)
2. IF This Then That (IFTTT) tracks these mentions and posts this data on Adafruit.io (MQTT Broker)
3. An ESP8266 connects to Adafruit.io and shows this data on a Dot-Matrix display

![](https://github.com/debsahu/Twitter_ESPDotMatrix/raw/master/IOTDisplay.png)

We can’t control who mentions us on twitter, so we move to the second step in our plan to configure IFTTT and Adafruit.io.

To setup a data feed (MQTT topic) on Adafruit.io,
* Goto “feed” and “Create New Feed”
* Provide a unique name for the feed like “twitter-calls”, this means the MQTT topic that we need to subscribe to is “feed/twitter-calls”

To setup IFTTT to connect to twitter and Adafruit.io,
* Connect your twitter and Adafruit.io account to IFTTT by logging in and giving proper permissions
* Create a new applet
* For “this“: Select “twitter” and “New mention of you”
* For “that“: Select “Adafruit” and “Send data to Adafruit.io”. Remember to select the correct topic created above and a message template using ingredients that suits your need.
As a part of the third step in our plan, we need to subscribe to our MQTT topic and display this data on a Dot-Matrix display.

Hardware

1. Wemos D1 mini (ESP8266)
2. Max7219 Dot Matrix Display

Software

* Setup Arduino IDE to be able to program an ESP8266 (Instructions on how to do this is here: https://github.com/esp8266/Arduino as well as in the video below).
* Install Adafruit_MQTT (https://github.com/adafruit/Adafruit_MQTT_Library) and MAX7219 Dot-Matrix Display (https://github.com/SensorsIot/MAX7219-4-digit-display-Library-for-ESP8266-) libraries
* Upload the code found here on your ESP8266

Make these following connections between Max 7219 display and Wemos D1:
* VCC -> 5V
* GND -> GND
* DIN -> D7
* CS -> D8
* CLK -> D5

That’s it, now you should be able to see your latest twitter mentions on your Dot-Matrix displays.
