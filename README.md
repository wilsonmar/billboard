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

# Board choices
There's Arduino, Raspberry Pi, and Tessel.

Arduino boards do not have the horsepower to output to HDMI.

Coming August 2015 is the $35 Tessel 2 from Technical Machines https://tessel.io/
embeds Node.js in a board with WiFi.
a 580MHz Mediatek 7620N MIPS based SoC for most processing and WiFi (802.11b/g/n) communication
2 USB ports.

So for early 2015, the mothboard is Raspberry Pi.

The Raspberry Pi 2 Model B came out in 2014 with a full Gigabyte of RAM.
Prior Pi B+ had 512MB RAM. 
http://www.linux.com/news/embedded-mobile/mobile-linux/813223-performance-testing-the-new-35-raspberry-pi-2-

It's ARM processor (900 Mhz Coretext v7 quadcore) is similar to what Windows Surface tablets use.

Hardware-wise, the Pi 2 keeps the same shape, connectors and mounting holes as the Raspberry Pi B+. 
The same HATs can be plugged in. See http://elinux.org/RPi_Buying_Guide


# Ingredients to buy
There are several editions of the Raspberry Pi.

1. TV.
2. UPS battery for TV.
3. TV mount on wall.
4. HDMI cable

    Don't get the $69.99 kit at http://www.amazon.com/Guide-Clear-Case-Power-Supply-WiFi-Dongle-Kingston-Adapter-HDMI/dp/B00MV6TAJI/ref=wilsonslifenotes because its wifi chip is crap (13 second ping vs 2 on others).

5. $44.99 Raspberry Pi board from http://www.amazon.com/Raspberry-Pi-Model-Project-Board/dp/B00T2U7R7I/ref=wilsonslifenotes
6. 8 GB Class 10 SD card. Pre-installed ones were sold out http://swag.raspberrypi.org/products/noobs-8gb-sd-card

7. Heat sink keep the Pi cool. The one with a fan for $24.99 
at http://www.amazon.com/Raspberry-Forged-Copper-Heatsink-Micro/dp/B00JT1P0I8/ref=wilsonslifenotes
has forged copper that insulates better than aluminium $12.99 version at http://www.amazon.com/Raspberry-Model-Copper-Heatsink-Forged/dp/B00MR14F4W/ref=wilsonslifenotes

    Optional:

8. USB console lead 3.3V cable from Adafruit.

9. A case is not needed if the Pi will be in the back of the TV. But if you do need a case, get a case that comes with heat sinks. To attach to wall (behind TV), ge thte $14.99 Zebra case that allows room for HDMI cable connector. http://www.amazon.com/gp/product/B00M6G9YBM/ref=wilsonslifenotes
Thus, if you use a HDMI cable, don't get the smaller $9.49 case for Pi from http://www.amazon.com/Premium-Clear-Case-Raspberry-Model/dp/B00MQLB1N6/ref=wilsonslifenotes

10. Instead of a power supply (5 volt 2000mA), run off USB on the TV. This would turn off the Pi when the TV is powered down.

11. $9.99 EDIMax Wi-fi for USB adapter is http://www.amazon.com/gp/product/B003MTTJOY/ref=wilsonslifenotes It supports the Realtech RTL8192cu chipset, and an external power supply. 
This is not needed if all media is self-contained in kiosk mode.

12. $29.99 Infrared for MCE (Media Center Edition) (RC6) remotes
http://www.amazon.com/Raspberry-MicroSD-OpenElec-Module-Remote/dp/B00SM4UZIS/ref=wilsonslifenotes


# Setup Raspberry Pi
Unlike a PC or a Mac, one needs to do quite a lot more to configure the hardware and operating system.

https://learn.adafruit.com/adafruit-raspberry-pi-lesson-1-preparing-and-sd-card-for-your-raspberry-pi?view=all

http://elinux.org/R-Pi_Troubleshooting

## Operating System on SD card
1. Download one of several operating system distos (Raspbian, Arch, XBMC, NooBs, etc). 

* Rasbian is the default standard maintained for Raspberry Pi "wheezy" http://www.raspberrypi.org/downloads
* Occidentalis (from the Latin name for the raspberry, Rubus Occidentalis)
is used by people who connect sensors, LEDs, buttons, servos, etc to their Pi http://learn.adafruit.com/adafruit-raspberry-pi-educational-linux-distro/
* NOOBS (Net Out Of the Box)
* Arh

## Media Players

* XBMC (Xbox Media Center) from OpenELEC shows videos, pictures, and music. 

* https://plex.tv/ collects your media and provides DNLA support for showing on various screens on the same wi-fi (which may stutter if the speed is not good).

The premium subscription auto-downloads movie trailers as well as your media, then plays them on XBox and Vizio TVs. First register after getting [http://www.raspberrypi.com/license-keys/] to download the necessary codecs for MPEG-2 and VC1.

* (Open Source Media Center) from https://osmc.tv/download/

http://elinux.org/RPi_Easy_SD_Card_Setup

2. Download the SD card formatter program. On a PC it's fedora-arm-installer.exe from http://fedoraproject.org/wiki/Fedora_ARM_Installer#Windows_Vista_.26_7
On a Mac https://github.com/RayViljoen/Raspberry-PI-SD-Installer-OS-X

3. Format the SD card
4. Label the SD card
5. Make a backup of the SD card.


## Boot-up Configuration
https://learn.adafruit.com/adafruits-raspberry-pi-lesson-2-first-time-configuration?view=all

1. Hook up the TV via HDMI connector.
2. Expand root partition to use all the SD card.
3. Disable TV Overscan
4. Auto login
5. Configure memory for graphics.
6. Configure for SSH

## SSH for Headless Mode
http://elinux.org/RPi_A_Method_for_ssh_blind_login
https://learn.adafruit.com/adafruits-raspberry-pi-lesson-6-using-ssh?view=all

1. Open LX Terminal on your Pi
2. sudo raspi-config
3. Enable SSH
4. On mac terminal: sudo ifconfig to find ip address
4. ssh 192.168.1.13 -l pi

http://elinux.org/RPi_Wheezy_VNC

The default password is pi and raspberry.

## Console cable
https://learn.adafruit.com/adafruits-raspberry-pi-lesson-5-using-a-console-cable?view=all
To supply the power for your Pi so you do not need keyboard, mouse or display attached to the Pi to log into it.

Pressing Alt-F1 through Alt-F12 will switch you one of them. If X11 has already started, you’ll often need to press Ctrl-Alt-F1 to ‘break out’, and just Alt-F2 etc thereafter. X11 will take the next available slot, since the default Raspbian defines six consoles, this is usually at Alt-F7.

## Chromium OS
https://lokir.wordpress.com/2012/09/16/raspberry-pi-kiosk-mode-with-chromium/

http://blogs.wcode.org/2013/09/howto-boot-your-raspberry-pi-into-a-fullscreen-browser-kiosk/

http://www.chromium.org/chromium-os

```
sudo apt-get update && apt-get upgrade -y
sudo apt-get install chromium x11-xserver-utils unclutter
```

To prevent screen from going blank and disable screen saver.
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

## USB hard drive to hold terabytes of movies
omxplayer command 

## GPIO for other sensors
REMEMBER: The Raspberry Pi runs 3.3V rather than th 5V on Arduino.

https://learn.adafruit.com/adafruits-raspberry-pi-lesson-4-gpio-setup
1. sudo apt-get update
2. Git
3. git Python
3. GPIO (General Purpose Input Output) 

http://www.modern-industry.com/articles/7-super-simple-raspberry-pi-video-kiosk


# Not reinventing the wheel
The above is the collective wisdom from several others who have written about similar quest than mine.



https://github.com/MobilityLab/TransitScreen/wiki/Raspberry-Pi
Kiosk Mode


https://learn.adafruit.com/raspberry-pi-video-looper

OMX player of H264 video format

HelloVideo plays raw H264 with no sound


