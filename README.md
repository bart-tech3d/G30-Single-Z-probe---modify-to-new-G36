# G30-Single-Z-probe---modify-to-new-G36
Based on Marlin2.0.x

G36: Do a single Z probe at the current XY and sets Z PROBE OFFSET (with negative value)
..\\Marlin\src\gcode\probe\G36.cpp
need to declare in: 
..\\Marlin\src\gcode\gcode.cpp and gcode.h

/**
* this G36 function was added by BART-TECH 3D
* This is a modification of the original G30 and add automatic change from the Z probe offset after the end of this process 
* This is useful to add to the Gcode autoleveling for easy finding of the distance between the probe and the nozzle (bed), 
* especially if you still use Z-endstops for homing at the same time.
*/

for a complete leveling including automatic setting of Z-probe offset I use compiled gcode below:

M851 Z0 ; offset to zero
G28 ; homing all axes
M428 ; reset offset
G36 ; find and automatic setting Z probe offset
G28 ; homing
M428 ; reset offset
G29 ; ABL bilinear
M500 ; store to EEPROM

optional can you bed heat up to 60°C (recommended for higher accuracy)
