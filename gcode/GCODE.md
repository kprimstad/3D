# GCODE - tips

### START
```gcode
M502;
G28 ;
G29 ;
M500 ;
M420 S1;

G21 ;metric values
G90 ;absolute positioning
M82 ;set extruder to absolute mode
M107 ;start with the fan off

G0 X0 Y15 F9000 ; Go to front
G0 Z0.15 ; Drop to bed
G92 E0 ; zero the extruded length
G1 X40 E25 F500 ; Extrude 25mm of filament in a 4cm line
G92 E0 ; zero the extruded length
G1 E-1 F500 ; Retract a little
G1 X80 F4000 ; Quickly wipe away from the filament line
G1 Z0.3 ; Raise and begin printing.
```



### DIV

```gcode
G28    ; Home all
G29   ; Auto level
M420 V1; Show leveling grid
M420 S1; Enable bed leveling
M500 ; Save to EEPROM
M502 ; reset to default
M503; Display

M501; Load settings from EEPROM
M48;   Probe Accuracy Test
M851 ; Show z offset
M851 z-0.4 ; Set z offset

M18  Disable steppers
M17 Enable steppers
```

### Z-Offset

1. Heat your printer up to your printing temperature and allow a few minutes for it to expand and settle
2. Reset the existing Z-offset to zero
M851 Z0
3. Home all axes
G28
4. Move the nozzle to the middle of the bed
G1 X110 Y110
5. Turn off the software endstops with
M211 S0
6. Move the nozzle down so it is just gripping a piece of standard printer paper
6. Set the Z-offset to the displayed value. E.g. if the printer displays a Z-Value of -1.23 enter
M851 Z-1.23
8. Store it to the EEPROM
M500
9. Important notice! Enable the endstops again with
M211 S1
or the printer head will collide with the bed on the next
G28

