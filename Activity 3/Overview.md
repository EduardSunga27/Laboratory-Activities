# Laboratory Activity #3: Fire Sensor Simulation

### Overview: The Fire Detector

This exercise reverses the approach of the previous activities. Rather than simply issuing commands to the hardware (like illuminating a bulb), we are programming the Arduino to perceive its surroundings. It emulates a fire alarm system by monitoring environmental variables to identify potential hazards.

### What This Project Does

The system functions as an intelligent monitoring unit that safeguards the area.

**Surveillance:** It continuously tracks both the ambient temperature and the intensity of light in the room.

**Logic Validation:** It utilizes a "Verification" protocol to prevent false positives. The alarm is triggered *only* if the environment is **Hot** (exceeding 50°C) **AND** **Bright** (Light reading above 220) simultaneously. This logic ensures the alarm ignores scenarios like a hot but safe afternoon, or a bright but cool room.

**The Response:** If both specific criteria are met, the system enters an emergency state: flashing a red LED and activating a buzzer to signal danger.

### How It Works

The device employs a dual-sensor approach to verify conditions, much like a human using both sight and touch to confirm a fire.

**The Sensors (The Inputs):**

* **Heat Sensor (Thermistor):** A variable resistor that alters its electrical resistance in response to temperature changes.
* **Light Sensor (Photoresistor):** A component that increases its conductivity when exposed to light.
* **The Alarm (The Outputs):** A Red LED and a piezoelectric Buzzer serve as the alert mechanism.

### Code Explanation

The software handles the interpretation of raw electrical signals into meaningful data.

**Signal Conversion:** The sensors do not transmit a temperature reading like "50°C" to the Arduino; they transmit raw voltage. The code applies a specific mathematical formula to convert that raw voltage into a readable temperature value.

**Conditional Evaluation:** The core of the program relies on a compound "If" statement:
*"Is the temperature above the limit AND is the light level above the limit?"*

**The Reaction:**

* **True:** Initiate rapid blinking of the LED and sounding of the buzzer.
* **False:** Maintain a silent and inactive state.

### Key Concepts Learned

**Analog Input Processing:** Understanding how to read continuous data ranges (like a thermometer's sliding scale) rather than simple binary (On/Off) inputs.

**Data Calibration:** Applying mathematical adjustments to align the code's interpretation with physical reality (e.g., ensuring the software reads 25°C when the room is actually 25°C).

**Compound Logic (AND Operator):** Constructing conditional statements where multiple requirements must be satisfied simultaneously for an event to trigger.

**Thresholding:** Establishing a specific "Cut-off Point" (such as 50 degrees) that instructs the software when to transition from a "Safe" status to a "Warning" status.
