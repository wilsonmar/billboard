# billboard
Here are my notes on how I went about creating a low-cost TV kiosk on a Raspberry Pi,
starting from a Minimum Viable Product, then adding more capabilities:

1. Display single photo stored on SD card. No sound. No wi-fi (SSH in)
2. Display photos stored on USB stick.
3. Display photos updated over wi-fi from a PC/Mac.
4. Computer turns itself on and off automatially.
5. Turn TV on and off automatically.
6. Interact with what is playing via the web server on the Pi running an HTML5 jQuery app.
7. Videos using https://flowplayer.org/player/

# Ingredients to buy
There are several editions of the Raspberry Pi.

1. TV.
2. UPS battery for TV.
3. HDMI cable.
4. The Raspberry Pi 2 Model B came out in 2014 with an upgraded ARMv7 quadcore processor, and a full Gigabyte of RAM.
Prior Pis had 512MB RAM. Software needs to be recompiled.
Hardware-wise, the Pi 2 keeps the same shape, connectors and mounting holes as the Raspberry Pi B+. 
The same HATs can be plugged in. See http://elinux.org/RPi_Buying_Guide

5. SD card. Usually 4GB. Pre-installed ones were sold out http://swag.raspberrypi.org/products/noobs-8gb-sd-card
6. USB console lead 3.3V cable from Adafruit.
7. Case for Pi to attach to wall (behind TV)
8. TV mount on wall.
9. Optional: Wi-Fi adapter that supports the RTL8192cu chipset, and an external power supply.


# Setup Raspberry Pi
Unlike a PC or a Mac, one needs to do quite a bit more to configure the hardware, operating system.

https://learn.adafruit.com/adafruit-raspberry-pi-lesson-1-preparing-and-sd-card-for-your-raspberry-pi?view=all

http://elinux.org/R-Pi_Troubleshooting

## Operating System on SD card
1. Download one of several operating system distos (Raspbian, Arch, XBMC, NooBs, etc). 

* Rasbian is the default standard maintained for Raspberry Pi "wheezy" http://www.raspberrypi.org/downloads
* Occidentalis (from the Latin name for the raspberry, Rubus Occidentalis)
is used by people who connect sensors, LEDs, buttons, servos, etc to their Pi http://learn.adafruit.com/adafruit-raspberry-pi-educational-linux-distro/
* NOOBS (Net Out Of the Box)
* Arh
* XBMC

http://elinux.org/RPi_Easy_SD_Card_Setup

2. Download the SD card formatter program. On a PC it's fedora-arm-installer.exe from http://fedoraproject.org/wiki/Fedora_ARM_Installer#Windows_Vista_.26_7
On a Mac https://github.com/RayViljoen/Raspberry-PI-SD-Installer-OS-X

3. Format the SD card
4. Label the SD card
5. Make a backup of the SD card.

## First-time Configuration
https://learn.adafruit.com/adafruits-raspberry-pi-lesson-2-first-time-configuration?view=all

1. Hook up the TV via HDMI connector.
2. Expand root partition to use all the SD card.
3. Disable TV Overscan
4. Auto login
5. Configure memory for graphics.
6. Configure for SSH

## SSH
http://elinux.org/RPi_A_Method_for_ssh_blind_login
https://learn.adafruit.com/adafruits-raspberry-pi-lesson-6-using-ssh?view=all
1. Open LX Terminal on your Pi
2. sudo raspi-config
3. Enable SSH
4. On mac terminal: sudo ifconfig to find ip address
4. ssh 192.168.1.13 -l pi

http://elinux.org/RPi_Wheezy_VNC

## Console cable
https://learn.adafruit.com/adafruits-raspberry-pi-lesson-5-using-a-console-cable?view=all
To supply the power for your Pi so you do not need keyboard, mouse or display attached to the Pi to log into it.

## Chromium OS
https://lokir.wordpress.com/2012/09/16/raspberry-pi-kiosk-mode-with-chromium/

http://www.chromium.org/chromium-os

```
sudo apt-get update && apt-get upgrade -y
sudo apt-get install chromium x11-xserver-utils unclutter
```

2. We need to prevent screen from going blank and disable screen saver.
– edit /etc/xdg/lxsession/LXDE/autostart and comment # screen saver line and add those lines:

```
@xset s off
@xset -dpms
@xset s noblank
@chromium --kiosk --incognito http://some.web.
```

## Wireless Control via Wi-Fi
https://learn.adafruit.com/adafruits-raspberry-pi-lesson-3-network-setup?view=all
configure Wi-Fi

## GPIO for other sensors
https://learn.adafruit.com/adafruits-raspberry-pi-lesson-4-gpio-setup
1. sudo apt-get update
2. Git
3. git Python
3. GPIO (General Purpose Input Output) 

 
# Not reinventing the wheel
The above is the collective wisdom from several others who have written about similar quest than mine.

https://github.com/MobilityLab/TransitScreen/wiki/Raspberry-Pi
Kiosk Mode


https://learn.adafruit.com/raspberry-pi-video-looper

OMX player of H264 video format

HelloVideo plays raw H264 with no sound


