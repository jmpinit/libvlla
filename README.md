# libvlla

Shared library for controlling the Very Large LED Array ([videos of it here](https://vimeo.com/album/3318776)).

![sound reactive](http://i.imgur.com/p98LX7s.gif)

![credit panda to fairlight](http://i.imgur.com/o1HWVAY.gif)

## Compilation

Just run `make`.

## Installation

1. Put it somewhere that the system can find it, like /usr/lib.
2. Run `sudo ldconfig` to configure the dynamic linker run-time bindings.

## API

Look at vlla.h. An example usage:

```C
int width = 60;
int x = 4;
int y = 3;

VLLA* vlla = vlla_init("/dev/ttyACM0", "/dev/ttyACM1"); // connect to the display hardware
vlla->pixels[y*width+x] = 0xFFFFFF; // __RRGGBB format
vlla_update(vlla); // send pixel data to the display
vlla_close(vlla); // dispose of resources like the serial ports
```
