This file describes components which were considered but not included.

# Boards:
## Arduino
Arduino boards do not have the horsepower to output to HDMI.

Cloudsto at http://www.cloudsto.com/products/android-mini-pc-s.html
in the UK makes several models of miniPCs for around $100 that has HDMI and a SD card.
Some have Bluetooth as well.

## Tessel
Coming August 2015 is the $35 Tessel 2 from Technical Machines https://tessel.io/
embeds Node.js in a board with WiFi.
a 580MHz Mediatek 7620N MIPS based SoC for most processing and WiFi (802.11b/g/n) communication
2 USB ports. It doesn't have a HDMI port because it's meant to be used wth an LCD suc as this:
http://tessel.hackster.io/sidwarkd/tessel-nokia5110

### Why Node.js?
As noted in https://learn.adafruit.com/node-embedded-development
node.js npm provides ease of library build.

node.js event listeners are defined in a couple of lines.
Event code is called whenever an event happens. 
This is instead of a loop constantly checking the state of a button to see if the state has changed.

node.js uses Unix pipeline 

Lua is the language.

## Play YouTube on Raspberry Pi
https://github.com/spygi/personal/tree/master/raspberry-youtube
is a Python script that runs on XBMC.

## Chromium App Samples
http://www.chromium.org/

https://github.com/GoogleChrome/chrome-app-samples

## Git
http://www.chromium.org/developers/fast-intro-to-git-internals

https://www.kickstarter.com/projects/1895460425/pijuice-a-portable-project-platform-for-every-rasp?ref=category_popular

