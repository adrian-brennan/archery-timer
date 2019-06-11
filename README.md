# archery-timer

Copyright (c) 2019 Stephen Williams <steve@icarus.com>


This program implements timing functions for archery tournaments. It supports
the call to the line, times ends, and supports multiple lines. The program displays
the main window on a screen that the archers of a tournament can see (and hear)
so that it handles line timing.

The aspects of
a shooting cycle are the callup (archers to the line), the "end" (the shooting
time), and "clear" (shooting is done). When there is only one line shooting, the
order of events is:

* Callup (2 whistles) - The archers are called to the line. The callup timer starts counting.

* Line's Hot (1 whistle) - The archers are clear to shoot. They have until the end
timer runs out to shoot the arrows of the end.

* Clear (3 whistles) - The end is done. The program for the end stops until it is
manually started for the next end.

If there are 2 lines shooting, the sequence is a little different:

* Callup line 1 (2 whistles) - Archers from the first shooting line are called up.

* Line's Hot (1 whistle) - The archers of the first line shoot their arrows for the
end.

* Callup line 2 (2 whistles) - Archers from the second shooting line are called up.

* Line's hot (1 whistle) - The archers of the second line shoot their arrows.

* Clear (3 whistles) - The end is done.

The program counts ends, and displays the end number, and also displays the line that
is currently called up or shooting. Note that the A-B and C-D lines alternate which is
shooting first. This follows the process used by World Archery.

The timer can be controlled on screen with a control panel window, or remotely by
a supplied Android app that sends network commands. The idea is to run the program
on a small computer (i.e. Raspberry pi) displaying on a monitor downrange, with a
range manager controlling it behind the line.

## Keyboard Shortcuts

The main timer window responds to these keyboard commands:

* Esc - Toggle fullscreen mode

* Space - Toggle the control box visibility

* n - Next End button
* Down (down arrow) - Skip button
* Enter or Return - Start timer

## Build

The program was originally implemented on Linux using QT5, but should build on
any system that supports QT5, including Linux, MacOSX, and Windows. The instructions
below are linux specific.

First, start with the source directory, which contains the archery-timer.pro file.
This file is the input to the "qmake" program. Run "qmake" to generate the Makefile.
If the archery-timer.pro file is changed, run qmake again to remake the Makefile.

Next, type "make" to build the archery-timer program using the Makefile that was
generated by qmake.
