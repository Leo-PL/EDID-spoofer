# EDID Spoofer

A simple board, that helps tinkering with VESA DDC
- Override EDID on a display for custom resolutions
- Provide a EDID to the PC for sinks which lack EDID, like with BNC inputs
- Act as a dummy plug for servers for Intel AMT
- Sniff or interfere with DDC communication between the graphics card and the display

## Parts used:

- 1x DE-15HD THT plug (towards graphics card).
- 1x DE-15HD THT receptacle (towards display).
- [24LCS22A](https://www.microchip.com/en-us/product/24LCS22A), [24LC21A](https://www.microchip.com/en-us/product/24LC21A), or compatible VESA DDC1/DDC2 EEPROM. A generic 24C02 should work too.
- 1 3x 10k 0805 SMD resistors.
- 1x 100nF 0805 SMD capacitor.
- Generic 4-pin header for programming or external bus access.

## Programming

First programming can be done even if write protection is enabled, which is set by default using JP1 jumper.
Chip locks itself when address 0x7F (the EDID checksum) is written.
For programming, you can use SNANDer, i2c-tools or any other tool compatible with I²C EEPROMs.
If using ordinary 24C02, be sure to keep WP pin low, as this is A2 pin on that part, otherwise chip address won't match.
DDC1 and write protection also won't work in this case.

## Redistribution

Project contents are freely redistributable in any form. Please see the [license](LICENSE).
