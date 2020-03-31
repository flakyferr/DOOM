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

I'm still working on compatibility with the sound server.
-> The soundserver now works, but still uses /dev/dsp to output sounds, which hasn't supported in linux since 2011.
-> To fix this you can use "padsp", a wrapper that redirects the program's access from /dev/dsp to a PulseAudio sound server.
-> You need the 32 bit version of padsp: sudo apt install padsp:i386
-> To enable it just run "export LD_PRELOAD=/usr/lib/i386-linux-gnu/pulseaudio/libpulsedsp.so" before starting the game. 
-> Compile the soundserver: "cd sndserv; make"
-> Put the compiled "sndserver" file in the same folder of the "linuxxdoom" executable.
-> Run the game and enjoy some low quality gunshots
!! Background music doesn't work, as the original code for music playback is or seems to be incomplete. Maybe I'll try to work something out.



