# Laboratory Activity #1: Digital Signal Processing - Sequential LED Circuit

### Overview: The "Running Light"

This exercise serves as an introduction to the Internet of Things (IoT). It demonstrates how to manipulate physical hardware (LEDs) using software instructions. Rather than relying on manual mechanical switches, you will write a program that automatically manages the switching process for you.

### What This Project Does

The system generates a basic light sequence utilizing five distinct LEDs.

**The Wave On:** The LEDs illuminate one after another in a linear path (from pin 12 to 8), creating a flowing wave effect.

**The Wave Off:** Once fully lit, the lights extinguish one by one following the same sequence.

**The Speed:** The program pauses for exactly one second between each transition, resulting in a steady, rhythmic animation.

### How It Works

The mechanism functions by bridging your programmed logic with an actual electrical circuit.

**The Hardware:** You will wire five LEDs to the Arduino interface. Resistors are integrated into the circuit to limit current, protecting the LEDs from burning out due to excessive power.

**The Signal:** The Arduino functions as the central controller. It transmits a "High" state (Voltage On) or a "Low" state (Voltage Off) to the specific pins associated with the LEDs.

**The Result:** The hardware illuminates immediately in response to the signals sent by the software.

### Code Explanation

The script is designed for efficiency, eliminating the need to write repetitive commands for each individual light.

**The List (Arrays):** Rather than assigning a unique variable to every light, the code collects them into a unified list known as `ledPins`. This allows the computer to locate and manage them easily.

**The Setup:** Upon startup, the system scans this list and configures the Arduino to treat those specific pins as power outputs.

**The Loop:** The primary logic executes an endless loop:

* It iterates through the list to **activate** the lights, pausing for one second at each step.
* It iterates through the list again to **deactivate** them, maintaining the same one-second interval.

### Key Concepts Learned

**Digital Control:** Understanding how to toggle electrical voltage on and off using programming.

**Automation:** Utilizing loops to automate tasks rather than coding every action manually.

**Timing:** Implementing "delay" functions to dictate the pace of the system's response.

**Efficiency:** Leveraging arrays to manage hardware connections in a clean, organized manner.
