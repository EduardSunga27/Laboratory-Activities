# Laboratory Activity #6: Bi-Directional Serial Communication

### Overview: Two-Way Data Exchange

This project marks a significant architectural upgrade from previous exercises. While prior activities utilized simplex (one-way) communication—either the PC commanding the Arduino or the Arduino streaming data to the console—this system establishes a **Bi-Directional** interface. The Arduino and the Python script engage in simultaneous transmission and reception, creating a complete, closed-loop feedback system.

### What This Project Does

The system establishes a digital "Round Trip" trajectory for data, translating physical inputs into digital logic and back into physical output.

**The Trigger:** A physical button on the circuit board is actuated.

**The Uplink:** The Arduino detects the input and transmits a status code (e.g., "Button 1 Actuated") to the host computer.

**The Logic Engine (Python):** The computer receives the signal, processes the logic, and determines the appropriate response (e.g., "Toggle Red LED state").

**The Downlink:** The computer transmits the corresponding control command back to the Arduino.

**The Actuation:** The Arduino interprets the command and energizes the specific LED.

*Note:* Despite the physical proximity of the button and the LED on the breadboard, the control signal traverses the entire serial path to the computer and back to execute the action.

### How It Works

The operational load is distributed between the embedded hardware and the high-level software.

**Hardware Configuration:** The circuit includes three tactile buttons (Inputs) and three LEDs (Outputs) interfaced with the Arduino.

**The Data Flow:**

1. **Button 1 Press** → Arduino transmits character **'R'** to the PC.
2. **PC Receives 'R'** → Processes logic and sends character **'1'** back to Arduino.
3. **Arduino Receives '1'** → Activates the **Red LED**.

### Code Explanation

The software architecture is segmented into three distinct functional roles:

**The Automated Host (Python):** Unlike the previous CLI that required manual typing, this script operates autonomously. It enters a persistent listening loop. Upon receiving a specific trigger (e.g., "Button Pressed"), it immediately calculates and transmits the appropriate response, effectively functioning as an automated logic server.

**The Multi-Tasking Controller (Arduino):** The firmware manages simultaneous operations:

* **The Receiver:** It constantly checks for incoming commands from the PC to toggle outputs.
* **The Monitor (Edge Detection):** It scans the button states. It utilizes a logic technique called **Edge Detection** (or State Change Detection) to register the exact moment of the click, preventing the system from spamming repeated messages while the button is held down.

**The Configuration (Header .h):** This file manages the pin setup. It leverages the **"Input Pull-Up"** feature, which activates the internal resistors within the ATmega chip. This internalizes the circuit resistance, eliminating the need for external resistors on the breadboard and simplifying the physical wiring.

### Key Concepts Learned

**Bi-Directional Communication:** The capability of a system to transmit and receive data packets simultaneously across a single interface.

**Edge Detection:** Programming logic that triggers actions based on the *transition* of a signal (the moment of change), rather than the continuous state of the input.

**System Latency:** observing the "Round Trip Time" (RTT)—the milliseconds it takes for a signal to travel from the sensor, to the PC, and back to the actuator.

**Hardware Optimization:** Utilizing the microcontroller's internal features (Internal Pull-up Resistors) to reduce component count and circuit complexity.
