# Final Laboratory Exam: IoT API Trigger

### Overview: The "Running Light" Mechanism

This examination serves as a foundational entry into the Internet of Things (IoT). It focuses on the software-driven manipulation of physical hardware. Rather than relying on manual toggles, you will engineer a script to autonomously manage the switching logic of the components.

### What This Project Does

The system generates a sequential visual animation utilizing a set of five LEDs.

**The Activation Wave:** The LEDs illuminate progressively in a linear sequence (descending from pin 12 to pin 8), simulating a cascading wave.

**The Deactivation Wave:** Upon reaching full illumination, the sequence reverses, extinguishing the lights one by one in the same order.

**The Timing:** The program incorporates a precise one-second pause between every transition, ensuring the animation is steady, deliberate, and rhythmic.

### How It Works

The system functions by bridging your programmed logic with the electrical circuit.

**The Circuitry:** Five LEDs are wired to the Arduino interface. Resistors are integrated as safety components to limit current, preventing the LEDs from being damaged by excessive power.

**The Control Signal:** The Arduino operates as the central processor. It outputs a digital "High" (5V) or "Low" (0V) signal to the designated pins to control the state of the LEDs.

**The Outcome:** The physical components respond instantly to the electronic commands issued by the software.

### Code Explanation

The code is optimized to avoid redundancy and improve scalability.

**Data Structures (Arrays):** Rather than declaring individual variables for each light, the code aggregates them into a single array named `ledPins`. This allows the processor to index and locate them efficiently.

**Initialization:** During the startup phase, the system iterates through this array to configure the specified pins as output channels.

**The Main Cycle:** The primary logic executes an infinite loop:

* It traverses the array to power **ON** the LEDs, inserting a 1-second delay at each step.
* It traverses the array again to power **OFF** the LEDs, maintaining the same timing interval.

### Key Concepts Learned

**Digital I/O Control:** Understanding the manipulation of voltage states via software commands.

**Programmatic Automation:** Leveraging loops to execute repetitive tasks without writing redundant lines of code.

**Temporal Management:** Utilizing `delay()` functions to regulate the execution speed and pacing of the system.

**Code Optimization:** Employing arrays to structure hardware definitions efficiently and cleanly.
