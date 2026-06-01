# Multi-LED IR Remote Control System 🚥

Tinkercad Link for Simulation : https://www.tinkercad.com/things/2XsYCW42fXA-controlling-led-using-ir-sensor-

An Arduino-based project simulating infrared remote control of a multi-LED system via Tinkercad. Using the `IRremote.h` library, it maps remote inputs (buttons 1-6) to independently toggle Red, Yellow, and White LEDs. Includes precise breadboard routing, proper forward-biased diode configurations, and optimized C++ switch-case decoding logic.

## 🛠️ Components Used
* 1x Arduino Uno R3
* 1x IR Sensor (Infrared Receiver)
* 1x IR Remote Control
* 3x LEDs (Red, Yellow, White)
* 3x 1 kΩ Resistors (Color Code: Brown-Black-Red)
* 1x Breadboard
* Jumper Wires

## 🔌 Circuit Wiring & Pin Mapping

### IR Sensor Setup
| Sensor Pin | Connection |
| :--- | :--- |
| **OUT (Left)** | Arduino Digital Pin **11** |
| **GND (Middle)** | Breadboard Ground (`-`) Rail |
| **VCC (Right)** | Breadboard Power (`+`) Rail (5V) |

### LED Setup
*Ensure LEDs are forward-biased (Arduino signal connects to the bent Anode leg).*

| LED Color | Arduino Pin (Anode/+) | Resistor to Ground (Cathode/-) |
| :--- | :--- | :--- |
| **Red** | Digital Pin **7** | 1 kΩ |
| **Yellow** | Digital Pin **6** | 1 kΩ |
| **White** | Digital Pin **5** | 1 kΩ |

## 🕹️ Controls & Logic
The system decodes incoming infrared signals and uses a `switch-case` structure to execute the following commands:

* **Button `1`** ➔ Turns Red LED **ON**
* **Button `2`** ➔ Turns Red LED **OFF**
* **Button `3`** ➔ Turns Yellow LED **ON**
* **Button `4`** ➔ Turns Yellow LED **OFF**
* **Button `5`** ➔ Turns White LED **ON**
* **Button `6`** ➔ Turns White LED **OFF**

## 🚀 How to Run the Simulation
1. Open the [Tinkercad](https://www.tinkercad.com/) platform.
2. Recreate the circuit using the wiring guide above.
3. Import the `main.ino` code into the code editor.
4. Open the **Serial Monitor** at the bottom of the code window.
5. Click **Start Simulation**.
6. Point the mouse at the IR remote and press buttons 1 through 6 to control the lights. The raw decoded signal values will print to the Serial Monitor.

## ⚠️ Troubleshooting & Hardware Notes
* **Reverse Polarity:** If the LEDs do not light up, check the polarity. The positive 5V signal must enter the bent Anode leg. If it enters the straight Cathode leg, the diode will be reverse-biased and block the current.
* **Thermal Runaway (Sparks):** If an LED sparks or breaks in the simulation, check the current-limiting resistor. Without adequate resistance (e.g., using 22 Ω instead of 1 kΩ), the applied voltage will exceed the diode's forward voltage drop, causing an exponential spike in current that destroys the semiconductor.
* **Unresponsive Sensor:** Ensure the IR sensor's VCC and GND pins are not reversed. Reversing power to the sensor will prevent it from waking up and sending data out to Pin 11.
