# Line Following Robot Using AFMotor Library

This is an Arduino-based project for a line-following robot that uses two analog sensors to detect a black line on a surface and controls four DC motors via the Adafruit Motor Shield. The robot adjusts its movement (forward, left turn, right turn, or stop) based on the sensor inputs.

---

## Prerequisites

### Hardware:
1. **Arduino Board** (e.g., Uno, Mega)
2. **Two Analog Line Sensors**
   - Left sensor connected to A0
   - Right sensor connected to A1
3. **Four DC Motors**
4. **Adafruit Motor Shield**
5. **Connecting Wires and Chassis**

### Software:
1. **Arduino IDE** (latest version recommended)
2. **AFMotor Library**
   - **Installation**:
     1. Download the AFMotor library ZIP file.
     2. Open the Arduino IDE.
     3. Go to `Sketch` > `Include Library` > `Add .ZIP Library`.
     4. Select the downloaded ZIP file.

---

## Setup Instructions

1. Connect the left and right sensors to analog pins A0 and A1, respectively.
2. Attach the motors to the appropriate terminals on the motor shield:
   - Motor 1: Left front
   - Motor 2: Left rear
   - Motor 3: Right front
   - Motor 4: Right rear
3. Place the robot on a surface with a clear black line for testing.
4. Upload the provided code to the Arduino board.

---

