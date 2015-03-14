This file describes components which were considered but not included.

# Boards:
## Arduino
Arduino boards do not have the horsepower to output to HDMI.

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

