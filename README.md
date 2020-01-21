# myfenjalinuxcnc
This repository holds the latest stable version of my LinuxCNC configuration for my CNC Router. It follows LinuxCNC Master (at the time of creation 2.9pre).

The CNC router's design is based on "Fenja" created by A. Koch of [fraeserbruch.de](https://fraeserbruch.de/ "Fenja's home"). Plans and parts are available through him. The design offers various sizes to choose from and requires the owner to chose drives, spindle and control. Furthermore, it is supported by a great community. I highly recommend this work.

All of the config options presented here are applicable to any CNC router design.
Many thanks to Oliver (https://github.com/GuiHue/myfenjalinuxcnc/) who is one of my masters in configutation linunxcnc!

The purpose of this GIT is to have a repo for my own changes to the config. However, as the same questions pop up time and again in various communities, I have chosen to make this public. Note, that LinuxCNC HAL and INI files are very specific to each machines. While the deployed concepts can be transfered easily, specific values and hardware pins are to be analyzed carefully. Do not ever run a foreign config on your machine without checking every detail before hand. I strongly recommend taking ideas from other configs and integrating those into to your own. I will not take responsibility for any damages to your hardware or person.

A word on licensing: I have chosen GPL3.0, hoping it does not interfer with any other licenses the used components are subject to. Please contact me asap if this is the case so that this can be resolved.

## Features
* Based on BENEZAN Triple Beast driver
* Runs on LinuxCNC 2.9 with Debian 9 (actually operates on master branch)
* Uses GMOCCAPY GUI in version 3.x with a touch screen
* Connects to an Hitachi WJ-200 VFD to control a CHINA spindle with 2.2kW without toolholders

* Uses NC inductive limit switches on each axis and furthermore uses these for homing
* Connects LinuxCNC to a PILZ safety relais using the relais' semi conductor output. This triggers estop in linuxcnc when a hardware based button is pushed and cuts power to various drives.  
* Uses an XHC-WHB04B-4 wireless pendant with modifications done by TALLA83 (http://www.talla83.de/)

* Uses probe_screen_v2 (see [probe_screen_v2](https://github.com/verser-git/probe_screen_v2)) together with a wireless touch probe by [vers.by](https://vers.by/en) and a wire based tool length sensor at a fixed location on the machine table

* Includes fixed macros and probe_screen.py for use with LinuxCNC 2.8/ 2.9 (dealing with joint/axis changes and changes to command.jog in LinuxCNC Python interface; seperate fork can be found on [github](https://github.com/GuiHue/probe_screen_v2))

## Notes
* Common errors with probe_screen:
  * Funny offset issues will arise, when gmoccapy tool change functions are still activated in gmoccapy settings while using probe_screen. Gmoccapy settings can be changed at the approriate place in the menu
  
## Known Issues
* At this point, "on abort" functions ar enot working correctly. When a running program is interrupted, a G53 G0 Z0 move may crash into the limit switches. I haven't come around to fixing that yet...

## Hardware
* The machine consists of an aluminum extrusion design with some milled components made from plate material. (https://fraeserbruch.de/ mill FENJA L1200)
* Working envelope roughly X/Y/Z 635/1240/165 mm

## Useful links
### LinuxCNC General
* http://linuxcnc.org/docs/html/gcode/m-code.html
* http://linuxcnc.org/docs/html/gcode/g-code.html
* http://linuxcnc.org/docs/html/gcode/o-code.html
* http://linuxcnc.org/docs/devel/html/hal/basic-hal.html
* http://linuxcnc.org/docs/html/man/man1/halui.1.html
* http://linuxcnc.org/docs/html/config/ini_config.html
* http://linuxcnc.org/docs/html/config/core-components.html#_iocontrol
* http://linuxcnc.org/docs/devel/html/config/python-interface.html
* http://gnipsel.com/linuxcnc/uspace/index.html

### Remapping & Tool change 
* http://linuxcnc.org/docs/devel/html/remap/remap.html#remap:interpreter-action-on-m6
* https://forum.linuxcnc.org/10-advanced-configuration/36810-implementing-a-tool-changer-is-classicladder-the-way-to-go?start=10
* https://forum.linuxcnc.org/10-advanced-configuration/4733-rack-tool-changer

### XHC-WHB04B-4
* http://linuxcnc.org/docs/html/man/man1/xhc-hb04.1.html
* https://github.com/LinuxCNC/linuxcnc/ (sources)
* https://youtu.be/HNXv5c4iXjo (http://www.talla83.de/)

### Python / GUI / QTpyVCP / GLADE
* http://linuxcnc.org/docs/2.6/html/common/python-interface.html
* https://qtpyvcp.kcjengr.com/
* http://linuxcnc.org/docs/html/gui/gladevcp.html

### New QTPYVCP based GUI (Which may well be the future GUI to use!)
* https://github.com/kcjengr/probe_basic
* https://kcjengr.github.io/probe_basic/dev_install.html
