# Laboratory Activity #7: Web-Controlled IoT System with FastAPI

### Project Summary: Web-Controlled LED System

This project constructs a functional prototype of a "Smart Home" device. Moving away from command-line interfaces, this system enables control of physical hardware (LED arrays) via a modern, interactive web dashboard. It establishes a bridge between a standard web browser and the Arduino microcontroller using Python.

### What It Does

The system effectively creates a virtual remote control accessible through your web browser.

**The Interface (Remote):** A stylized webpage featuring interactive buttons for Red, Green, and Blue LEDs, alongside master controls for "All On" and "All Off."

**The Bridge (Translator):** A Python application running on the host machine that monitors button clicks and converts them into serialized signals.

**The Hardware (Actuator):** The Arduino processes these signals instantaneously, physically toggling the specific LED circuits on or off.

### How It Works (The Chain of Command)

The operation follows a three-step pipeline, mirroring the architecture of commercial IoT devices.

**The User Input:** You trigger an event (e.g., clicking "Red LED") on the dashboard. The browser transmits this request to the local server.

**The Server Translation:** The Python backend intercepts the request. It maps the user's intent to a specific control byte (e.g., mapping "red" to the integer `1`) and transmits it via the USB serial connection.

**The Hardware Execution:** The Arduino, constantly polling the serial port, detects the incoming byte. Upon recognizing the identifier (e.g., `1`), it executes the corresponding command to energize the Red Light.

### The Code Breakdown

The codebase is segmented into three specific layers to ensure separation of concerns:

**The Frontend (web.html):** This layer manages the user experience. It generates the "Dark Mode" dashboard and utilizes background scripts (JavaScript/AJAX) to transmit commands asynchronously, ensuring the page does not need to reload with every click.

**The Backend (main.py):** This serves as the "Middleware." It utilizes **FastAPI** to establish a local web server accessible by the browser. It also manages the serial communication protocol, handling the actual data transfer to the Arduino.

**The Firmware (LabAct7.ino):** This is the embedded logic on the microcontroller. It is designed for simplicity: it waits for specific character inputs (such as 1, 2, or 9) and triggers the associated digital pins (Red, Green, or Blue) based on the received character.

### Key Concepts Learned

**Web-Based Control:** The capability to trigger physical world actions via a URL or web interface.

**Middleware Implementation:** Utilizing a server-side script to facilitate communication between two disparate systems (a web browser and a microcontroller).

**Asynchronous Interaction:** Developing an interface that allows for rapid user interaction without the latency or interruption of full-page refreshes.

---

**Would you like me to explain how "FastAPI" specifically handles the request between the HTML button and the Python code?**
