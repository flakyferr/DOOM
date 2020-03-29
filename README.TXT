This is a little project that lets you compile and run the original Doom source code with only minor cleanup for retrocompatibility. (Only tested on Ubuntu 19)
It is also my first project using GitHub so it might look a bit rough.

The program DOES NOT CONTAIN ANY GAME FILES. You need to buy the .wad file from any platform like Steam or GOG etc.

Compiling:

The original X11 code is still in use, and you need 32 bit architecture compatibility. These are the requirements:

sudo apt install libx11-dev:i386 libxext-dev:i386
sudo apt install gcc:i386

-Create a "linux/" directory in linuxdoom-1.10/
-Just run Make inside "linuxdoom-1.10/"

I already set the flags to compile 32 bit on 64 bit systems


Running:
Doom only runs on 8-bit displays, so I suggest you to make a floating x11 display using Xephyr:
sudo apt install xserver-xephyr
Xephyr :3 -screen 960x600x8 -ac & 

Name the wad file "doomu.wad" and put it inside the "linuxdoom-1.10/" folder.
Run:
DISPLAY=:3 ./linux/linuxxdoom
to run the game inside the previously created display.

I'm still working on compatibility with the sound server, so for now SOUND IS NOT WORKING and disabled inside "doomdef.h".


