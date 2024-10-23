# Arduino-Joystick-with-4-LEDs-connection
Arduino UNO Board with a joystick and 4 LEDs, control the movement of the joystick (up, down, left, right) to light up corresponding LEDs. The project code that includes the optional joystick button pin. The button will be used to turn all LEDs on simultaneously when pressed and turn them off when released.
To connect an Arduino joystick with 4 LEDs and write the code to control them, you can follow these steps. The joystick module typically has two analog outputs (X and Y axes) and a digital output for the button press. You can use the joystick's movement to control the LEDs in various patterns.

Components Needed:
Arduino (e.g., Uno, Nano)
Joystick module (with X, Y axis, and a push-button)
4 LEDs
4 resistors (220 ohms each)
Breadboard and jumper wires
Wiring:
Joystick Module:

VCC to Arduino 5V
GND to Arduino GND
VRx (X-axis output) to Arduino A0
VRy (Y-axis output) to Arduino A1
SW (Joystick button) to Arduino pin 7 (or any digital pin)
LED Connections:

Connect the positive (long leg) of each LED to the following pins:
LED 1: Arduino pin 8
LED 2: Arduino pin 9
LED 3: Arduino pin 10
LED 4: Arduino pin 11
The negative (short leg) of each LED should connect to GND through a 220-ohm resistor.
