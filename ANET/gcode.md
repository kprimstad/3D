#START GCODE
M104 S215 ; set extruder temp
M140 S50 ; set bed temp
G28 X0;  home x while extruder is heating
M190 S50 ; wait for bed temp
M109 S200; wait for extruder temp
G28 ; home all axes
;G29;
M420 S1; Enabeling Bed leveling
G1 X0 Y0 Z20 F5000:
M420 S1;

; Purge line
G0 X10 Y15 F9000 ; Go to front
G0 Z0.15 ; Drop to bed
G92 E0 ; zero the extruded length
G1 X40 E50 F1000 ; Extrude 25mm of filament in a 4cm line
G92 E0 ; zero the extruded length
G1 Z5 F5000 ; lift nozzle
G1 Y10 X10 Z10 ; Raise and begin printing.

G1 E-1 F500 ; Retract a little
G1 X80 F4000 ; Quickly wipe away from the filament line
G1 Z0.3 ; Raise and begin printing.


# End-GCODE
M104 S0 ; turn off temperature
M140 S0 ;
G28 X0  ; home X axis 
G0 Y200;  move bed out
G91; 
G0 Z20: Move Z 2 cm
G90;
M84     ; disable motors
