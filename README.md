# Arduino-Joystick-with-4-LEDs-connection
# Arduino Joystick with 4 LEDs

## Overview
This project demonstrates how to control 4 LEDs using a joystick module with an Arduino. The joystick's X and Y axes control the direction, while the push button lights up all LEDs simultaneously when pressed.

---

## Components
| **Component**         | **Quantity** | **Description**                                           |
|------------------------|--------------|-----------------------------------------------------------|
| Arduino Uno            | 1            | Microcontroller board                                     |
| Joystick Module        | 1            | With X, Y axes and a push button                         |
| LEDs                   | 4            | For indicating joystick directions                       |
| Resistors (220Ω)       | 4            | For current limiting for LEDs                            |
| Breadboard             | 1            | For organizing connections                               |
| Jumper Wires           | Several      | For making connections                                   |

---

## Connections
| **Component**          | **Pin**           | **Arduino Pin** |
|-------------------------|-------------------|------------------|
| **Joystick Module**     | VCC              | 5V               |
|                         | GND              | GND              |
|                         | VRx (X-axis)     | A0               |
|                         | VRy (Y-axis)     | A1               |
|                         | SW (Button)      | D7               |
| **LEDs**                | LED 1 Anode (+)  | D8               |
|                         | LED 2 Anode (+)  | D9               |
|                         | LED 3 Anode (+)  | D10              |
|                         | LED 4 Anode (+)  | D11              |
|                         | Cathodes (-)     | GND via 220Ω resistor |

---

## Functionality
1. **Joystick Movement**:
   - Move the joystick **left**: LED 1 turns on.
   - Move the joystick **right**: LED 2 turns on.
   - Move the joystick **up**: LED 3 turns on.
   - Move the joystick **down**: LED 4 turns on.
2. **Joystick Button**:
   - Press the joystick button to light up all LEDs.
   - Release the button to turn all LEDs off.

---

## Arduino Code

Here’s the Arduino code for the project:

```cpp
// Define joystick and LED pins
#define VRx A0
#define VRy A1
#define SW 7
#define LED1 8
#define LED2 9
#define LED3 10
#define LED4 11

void setup() {
  // Initialize LED pins as outputs
  pinMode(LED1, OUTPUT);
  pinMode(LED2, OUTPUT);
  pinMode(LED3, OUTPUT);
  pinMode(LED4, OUTPUT);

  // Initialize joystick button pin as input
  pinMode(SW, INPUT_PULLUP);
}

void loop() {
  int xVal = analogRead(VRx); // Read X-axis value
  int yVal = analogRead(VRy); // Read Y-axis value
  int buttonState = digitalRead(SW); // Read button state

  // Control LEDs based on joystick movement
  if (xVal < 400) digitalWrite(LED1, HIGH); // Left
  else digitalWrite(LED1, LOW);

  if (xVal > 600) digitalWrite(LED2, HIGH); // Right
  else digitalWrite(LED2, LOW);

  if (yVal < 400) digitalWrite(LED3, HIGH); // Up
  else digitalWrite(LED3, LOW);

  if (yVal > 600) digitalWrite(LED4, HIGH); // Down
  else digitalWrite(LED4, LOW);

  // Control all LEDs based on button press
  if (buttonState == LOW) { // Button pressed
    digitalWrite(LED1, HIGH);
    digitalWrite(LED2, HIGH);
    digitalWrite(LED3, HIGH);
    digitalWrite(LED4, HIGH);
  } else { // Button released
    digitalWrite(LED1, LOW);
    digitalWrite(LED2, LOW);
    digitalWrite(LED3, LOW);
    digitalWrite(LED4, LOW);
  }

  delay(50); // Small delay for stability
}

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
