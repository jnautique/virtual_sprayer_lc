The virtual sprayer light controller (VSLC) is part of the virtual sprayer project.  The following describes the interfaces for tshis module and how it operates.  Originally, this was not a planned module.  However, the Arduino Uno does not work with the belt source code.  It locks up the Arduino Leonardo board such that it will not stay connected to a computer to be programmed.  A new sketch must be loaded in very quickly during the brief time that the Leonardo will stay connected.  Once a new sketch is loaded (usually the basic blink sketch), the Leonardo board will operate properly.

The Arduino Uno does not seem to have this problem.  It will be used to control the LED strips and monitor the knock sensor.  This will result in a two board solution for now.

Inputs
------
Vibration detector (analog input)
Light Trigger (digital input)

Outputs
-------
x2 - LED strips (serial output)

Day in the Life
----------------
The following details the operation of the virtual sprayer light controller (VSLC).  

1. The VSLC monitors the vibration detector and the light trigger input.
2. When a vibration happens and the light trigger is not asserted, this means that someone hit the board with the bean bag, but it did not go through the hold.  In this case, the lights should be briefly illuminated and then turned off.
3. If during the sequence that a vibration was detected we also see the light trigger asserted, this means that the board was hit.  The LEDs should be turned on for ~7 seconds.
4. If no vibration was detected but the light trigger assertes, this means it was a "swish".  In this case, the lights should be turned on for 7 seconds.