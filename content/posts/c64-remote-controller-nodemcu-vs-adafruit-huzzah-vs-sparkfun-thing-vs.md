---
author: ricardoquesada
category:
  - commodore-64
  - programming
date: "2016-03-27T21:21:04+00:00"
guid: http://retro.moe/?p=1260
summary: |-
  ### Requirements for the c64 controller

  - A micro-controller. I doesn't need to be very powerful, just powerful enough to handle some UDP connections and configuring some GPIOs.
  - Flash-able firmware: If possible with support for [Arduino IDE](https://www.arduino.cc/en/Main/Software) (or similar). C++ preferred. [Micropython](http://micropython.org/) could be a nice backup plan.
  - WiFi
  - Some GPIOs

  ### Which module to choose

  There many alternatives, and these are the ones that I evaluated:

  - [Arduino](http://www.arduino.cc/en/Main/ArduinoBoardUno) \+ [WiFi shield](http://www.arduino.cc/en/Main/ArduinoWiFiShield101) or [ESP8266](http://espressif.com/en/products/hardware/esp8266ex/overview): This is the first option that I evaluated thanks to [different](http://www.lemon64.com/forum/viewtopic.php?t=60046) [suggestions](http://retroinvaders.com/commodoremania/foro/index.php/topic,1525.0.html). But since the ESP8266 already comes with a flash-able firmware, there was no need to use the Arduino part. I discarded this option, but I liked the ESP8266 part.
  - [Adafruit Huzzah](https://www.adafruit.com/products/2471) breakout ($9.95) / [Adafruit Feather Huzzah](https://www.adafruit.com/products/2821) ($15.95): An ESP8266 based module. I like Adafruit products since they are very well tested, they give you support, have very good documentation. But they are usually on the pricy side. All ESP8266 boards are supported by the [Arduino IDE](https://github.com/esp8266/Arduino) which is a very good thing.  (I ordered one Feather Huzzah).
  - [SparkFun ESP8266 Thing](https://www.sparkfun.com/products/13231) ($15.95): Similar to the Feather Huzzah.
  - [NodeMCU](http://www.aliexpress.com/af/nodemcu.html) (~$4.00): Very similar too Adafruit Huzzah and SparkFun ESP8266 Thing. I'm not sure who built the first module (Adafruit, SparkFun or NodeMCU), although I wouldn't be surprised if NodeMCU was the first one. There is a lot of innovation in China in this area. NodeMCU comes with a firmware that supports Lua, which is nice for faster development. You should know that the Lua firmware could be installed in the other modules as well, and you can run C++ firmwares on NodeMCU as well. There are three different NodeMCU brands:

    - Amica: Which seems to be the official one, although I didn't know this when I decided to buy the LoLin.
    - LoLin: It seems that it is no longer produced by WeMos. (I ordered one of this too).
    - DOIT: I know nothing about it.
  - [Mini D1](http://www.wemos.cc/Products/d1_mini.html) (~$4.00): Another ESP8266-based module similar to the previous ones. It is produced by [WeMos](http://www.wemos.cc/), the same as the NodeMCU LoLin. My theory is that WeMos realized that there was more money in trying to create [their own ecosystem](http://www.wemos.cc/Products/mini_shields.html) rather than just cloning NodeMCU. It has 11 GPIOs, instead of the 9 offered by Adafruit Huzzah, which is good (I ordered a few of this one too).
  - There were other alternatives, [like the SparkFun Particle Photon](https://www.sparkfun.com/products/13774) ($19.00), based on non-ESP8266 micro-controllers. They were a bit more powerful, but also more expensive. And don't support the Arduino IDE. So, for the moment I discarded them.
tag:
  - c64
  - esp8266
  - nodemcu
title: 'C64 Remote Controller: NodeMCU vs. Adafruit Huzzah vs. SparkFun Thing vs...'
url: /2016/03/27/c64-remote-controller-nodemcu-vs-adafruit-huzzah-vs-sparkfun-thing-vs/

---
### Requirements for the c64 controller

- A micro-controller. I doesn't need to be very powerful, just powerful enough to handle some UDP connections and configuring some GPIOs.
- Flash-able firmware: If possible with support for [Arduino IDE](https://www.arduino.cc/en/Main/Software) (or similar). C++ preferred. [Micropython](http://micropython.org/) could be a nice backup plan.
- WiFi
- Some GPIOs

### Which module to choose

There many alternatives, and these are the ones that I evaluated:

- [Arduino](http://www.arduino.cc/en/Main/ArduinoBoardUno) \+ [WiFi shield](http://www.arduino.cc/en/Main/ArduinoWiFiShield101) or [ESP8266](http://espressif.com/en/products/hardware/esp8266ex/overview): This is the first option that I evaluated thanks to [different](http://www.lemon64.com/forum/viewtopic.php?t=60046) [suggestions](http://retroinvaders.com/commodoremania/foro/index.php/topic,1525.0.html). But since the ESP8266 already comes with a flash-able firmware, there was no need to use the Arduino part. I discarded this option, but I liked the ESP8266 part.
- [Adafruit Huzzah](https://www.adafruit.com/products/2471) breakout ($9.95) / [Adafruit Feather Huzzah](https://www.adafruit.com/products/2821) ($15.95): An ESP8266 based module. I like Adafruit products since they are very well tested, they give you support, have very good documentation. But they are usually on the pricy side. All ESP8266 boards are supported by the [Arduino IDE](https://github.com/esp8266/Arduino) which is a very good thing.  (I ordered one Feather Huzzah).
- [SparkFun ESP8266 Thing](https://www.sparkfun.com/products/13231) ($15.95): Similar to the Feather Huzzah.
- [NodeMCU](http://www.aliexpress.com/af/nodemcu.html) (~$4.00): Very similar too Adafruit Huzzah and SparkFun ESP8266 Thing. I'm not sure who built the first module (Adafruit, SparkFun or NodeMCU), although I wouldn't be surprised if NodeMCU was the first one. There is a lot of innovation in China in this area. NodeMCU comes with a firmware that supports Lua, which is nice for faster development. You should know that the Lua firmware could be installed in the other modules as well, and you can run C++ firmwares on NodeMCU as well. There are three different NodeMCU brands:

  - Amica: Which seems to be the official one, although I didn't know this when I decided to buy the LoLin.
  - LoLin: It seems that it is no longer produced by WeMos. (I ordered one of this too).
  - DOIT: I know nothing about it.
- [Mini D1](http://www.wemos.cc/Products/d1_mini.html) (~$4.00): Another ESP8266-based module similar to the previous ones. It is produced by [WeMos](http://www.wemos.cc/), the same as the NodeMCU LoLin. My theory is that WeMos realized that there was more money in trying to create [their own ecosystem](http://www.wemos.cc/Products/mini_shields.html) rather than just cloning NodeMCU. It has 11 GPIOs, instead of the 9 offered by Adafruit Huzzah, which is good (I ordered a few of this one too).
- There were other alternatives, [like the SparkFun Particle Photon](https://www.sparkfun.com/products/13774) ($19.00), based on non-ESP8266 micro-controllers. They were a bit more powerful, but also more expensive. And don't support the Arduino IDE. So, for the moment I discarded them.

### Setting up LoLin NodeMCU

{{< figure align=alignnone width=379 src="/wp-content/uploads/2016/03/img%5F4002.jpg?w=576" alt="" >}}

#### CH340G drivers

The first one to arrive was the LoLin NodeMCU (the Adafruit Feather Huzzah and the Mini D1 will arrive later this week), so I started playing with the NodeMCU.

LoLin NodeMCU comes with a CH340G serial-to-USB interface (cheaper than than the other serial-to-USB alternatives?). And its drivers are not preinstalled on Mac, so:

- [Download and install the CH340G Mac drivers](http://kig.re/2014/12/31/how-to-use-arduino-nano-mini-pro-with-CH340G-on-mac-osx-yosemite.html) (direct link: [CH34x\_Install.zip](http://kig.re/downloads/CH34x_Install.zip))

#### esptool

This tool allows you to upload a firmware to the ESP8266 bootloader. I think it is not needed if you use the Arduino IDE, but it is a handy tool. To install it do:

```
$ git clone https://github.com/themadinventor/esptool
$ cd esptool
$ python setup.py install
```

#### Arduino IDE + esp8266 board

Download [Arduino IDE](https://www.arduino.cc/en/Main/Software) and then install the ESP8266 boards. The detailed instructions are [here](https://github.com/esp8266/Arduino), but I'm copying & pasting them in case you are too lazy to follow the link:

- Install Arduino 1.6.8 from the [Arduino website](http://www.arduino.cc/en/main/software).
- Start Arduino and open Preferences window.
- Enter `http://arduino.esp8266.com/stable/package_esp8266com_index.json` into _Additional Board Manager URLs_ field. You can add multiple URLs, separating them with commas.
- Open Boards Manager from Tools > Board menu and install _esp8266_ platform (and don't forget to select your ESP8266 board from Tools > Board menu after installation).

[![Screen Shot 2016-03-27 at 11.44.24 AM](/wp-content/uploads/2016/03/screen-shot-2016-03-27-at-11-44-24-am.png)](/wp-content/uploads/2016/03/screen-shot-2016-03-27-at-11-44-24-am.png)

#### New Arduino Sketch

Start a new Arduino Sketch (Command + N) and select, in Arduino -> Tools:

- Board: NodeMCU 1.0 (ESP12-E Module)
- Upload Using: Serial
- CPU Frequency: 80Mhz
- Flash Size: 4M (1M SPIFFS)
- Upload Speed: 57600 (Try slower if it fails. The recommended one 9600 but it is toooo slow)
- Port: /dev/cu.wchusbserial1410

[![Screen Shot 2016-03-27 at 1.40.35 PM](/wp-content/uploads/2016/03/screen-shot-2016-03-27-at-1-40-35-pm.png)](/wp-content/uploads/2016/03/screen-shot-2016-03-27-at-1-40-35-pm.png)

And just edit the `setup(void)` and `loop(void)` and you are ready to go. It is easier to start by copying & pasting some sample code so...

#### Simple web server

...here you have a simple Web Server in C++: [HelloServer.ino](https://github.com/platformio/platformio/blob/develop/examples/espressif/esp8266-webserver/src/HelloServer.ino)

\[code language="cpp"\]
#include &amp;lt;ESP8266WiFi.h&amp;gt;
#include &amp;lt;WiFiClient.h&amp;gt;
#include &amp;lt;ESP8266WebServer.h&amp;gt;
#include &amp;lt;ESP8266mDNS.h&amp;gt;

const char\* ssid = &amp;quot;\*\*\*\*\*\*&amp;quot;;
const char\* password = &amp;quot;\*\*\*\*\*\*&amp;quot;;
MDNSResponder mdns;

ESP8266WebServer server(80);

const int led = 13;

void handleRoot() {
 digitalWrite(led, 1);
 server.send(200, &amp;quot;text/plain&amp;quot;, &amp;quot;hello from esp8266!&amp;quot;);
 digitalWrite(led, 0);
}

void handleNotFound(){
 digitalWrite(led, 1);
 String message = &amp;quot;File Not Found\\n\\n&amp;quot;;
 message += &amp;quot;URI: &amp;quot;;
 message += server.uri();
 message += &amp;quot;\\nMethod: &amp;quot;;
 message += (server.method() == HTTP\_GET)?&amp;quot;GET&amp;quot;:&amp;quot;POST&amp;quot;;
 message += &amp;quot;\\nArguments: &amp;quot;;
 message += server.args();
 message += &amp;quot;\\n&amp;quot;;
 for (uint8\_t i=0; i&amp;lt;server.args(); i++){
 message += &amp;quot; &amp;quot; + server.argName(i) + &amp;quot;: &amp;quot; + server.arg(i) + &amp;quot;\\n&amp;quot;;
 }
 server.send(404, &amp;quot;text/plain&amp;quot;, message);
 digitalWrite(led, 0);
}

void setup(void){
 pinMode(led, OUTPUT);
 digitalWrite(led, 0);
 Serial.begin(115200);
 WiFi.begin(ssid, password);
 Serial.println(&amp;quot;&amp;quot;);

 // Wait for connection
 while (WiFi.status() != WL\_CONNECTED) {
 delay(500);
 Serial.print(&amp;quot;.&amp;quot;);
 }
 Serial.println(&amp;quot;&amp;quot;);
 Serial.print(&amp;quot;Connected to &amp;quot;);
 Serial.println(ssid);
 Serial.print(&amp;quot;IP address: &amp;quot;);
 Serial.println(WiFi.localIP());

 if (mdns.begin(&amp;quot;esp8266&amp;quot;, WiFi.localIP())) {
 Serial.println(&amp;quot;MDNS responder started&amp;quot;);
 }

 server.on(&amp;quot;/&amp;quot;, handleRoot);

 server.on(&amp;quot;/inline&amp;quot;, \[\](){
 server.send(200, &amp;quot;text/plain&amp;quot;, &amp;quot;this works as well&amp;quot;);
 });

 server.onNotFound(handleNotFound);

 server.begin();
 Serial.println(&amp;quot;HTTP server started&amp;quot;);
}

void loop(void){
 server.handleClient();
}
\[/code\]

### ![Screen Shot 2016-03-27 at 2.45.10 PM.png](/wp-content/uploads/2016/03/screen-shot-2016-03-27-at-2-45-10-pm.png)

### What's next

- Create the UDP server + GPIO management firmware.
- Create the circuit that controls the joysticks from the GPIOs
- Create the client for iOS and Android

### Further reading

- [Mise en route d’une carte _WeMos-LoLin_ avec le firmware NodeMCU et un module WiFi ESP8266](http://ouilogique.com/NodeMCU_esp8266/) (although in French, it is a must read. Use Google Translate)
- [How To Use Cheap Chinese Arduinos That Come With With CH340G / CH341G Serial/USB Chip (Windows & Mac OS-X)](http://kig.re/2014/12/31/how-to-use-arduino-nano-mini-pro-with-CH340G-on-mac-osx-yosemite.html)
- [Comparison of ESP8266 NodeMCU development boards](http://frightanic.com/iot/comparison-of-esp8266-nodemcu-development-boards/)
- [ESP8266 Node MCU Setup](http://www.averagemanvsraspberrypi.com/2015/11/esp8266-node-mcu-setup.html)
