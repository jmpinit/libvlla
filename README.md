# libvlla

Shared library for controlling the Very Large LED Array.

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
