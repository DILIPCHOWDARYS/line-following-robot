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

## Code

Here is the complete Arduino sketch:

```cpp
#include <AFMotor.h>

// Defining pins for sensors
#define lefts A0
#define rights A1

// Defining motors
AF_DCMotor motor1(1, MOTOR12_1KHZ);
AF_DCMotor motor2(2, MOTOR12_1KHZ);
AF_DCMotor motor3(3, MOTOR34_1KHZ);
AF_DCMotor motor4(4, MOTOR34_1KHZ);

void setup() {
    // Setting motor speeds
    motor1.setSpeed(180);
    motor2.setSpeed(180);
    motor3.setSpeed(180);
    motor4.setSpeed(180);

    // Declaring input pins for sensors
    pinMode(lefts, INPUT);
    pinMode(rights, INPUT);

    // Begin serial communication for debugging
    Serial.begin(9600);
}

void loop() {
    // Read and print sensor values
    int leftVal = analogRead(lefts);
    int rightVal = analogRead(rights);
    Serial.println(leftVal);
    Serial.println(rightVal);

    // Line detected by both sensors
    if (leftVal <= 350 && rightVal <= 350) {
        motor1.run(FORWARD);
        motor2.run(FORWARD);
        motor3.run(FORWARD);
        motor4.run(FORWARD);
    }
    // Line detected by the left sensor
    else if (leftVal <= 350 && rightVal > 350) {
        motor1.run(FORWARD);
        motor2.run(FORWARD);
        motor3.run(BACKWARD);
        motor4.run(BACKWARD);
    }
    // Line detected by the right sensor
    else if (leftVal > 350 && rightVal <= 350) {
        motor1.run(BACKWARD);
        motor2.run(BACKWARD);
        motor3.run(FORWARD);
        motor4.run(FORWARD);
    }
    // Line not detected by either sensor
    else {
        motor1.run(RELEASE);
        motor2.run(RELEASE);
        motor3.run(RELEASE);
        motor4.run(RELEASE);
    }
}
