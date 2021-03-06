Aviso
=====
Este es un clon del proyecto original de Adafruit para que directamente funcione el diseño del arcade que hemos realizado en [interzonas](http://interzonas.info)


Adafruit-Retrogame
==================

Raspberry Pi GPIO-to-USB utility for classic game emulators.

How-to: http://learn.adafruit.com/retro-gaming-with-raspberry-pi

Pre-built version supports the default pin/key mapping shown in the tutorial. For other layouts, edit retrogame.c.

### RetroPie 2.0+ Compatibility

Note that by default retrogame won't work with SDL2 applications that depend on evdev for input events.  Specifically this means applications like the latest version of RetroPie and EmulationStation won't be able to see key events generated by retrogame.  However you can fix this issue by adding a small custom udev rule to make retrogame keyboard events visible to SDL2.

Connect to your Raspberry Pi in a terminal/SSH session and execute the following command to create and edit the file /etc/udev/rules.d/10-retrogame.rules:

````
sudo nano /etc/udev/rules.d/10-retrogame.rules
````

Once the nano text editor loads, copy this single line into the file:

````
SUBSYSTEM=="input", ATTRS{name}=="retrogame", ENV{ID_INPUT_KEYBOARD}="1"
````

Save the file by pressing Ctrl-O and enter, then press Ctrl-x to exit.  Restart your Raspberry Pi and run retrogame again, now button presses should register in SDL2 applications like the EmulationStation frontend to RetroPie
