# ATmega Microcontroller with Sensors and PC Application
**Design Lab Project**

**Project carried out by:**
* Monika Bogdalska
* Wiktor Baran
* Mikołaj Polewka

**Supervisor:** Dr Eng. Jacek Stępień

---

## 1. Project Goal and Topic
The objective of this project was to design and implement an embedded measurement system based on an ATmega328 microcontroller, capable of cooperating with environmental sensors and communicating with a PC application via a wired interface.

**The project aimed to provide practical experience in:**
* Integration of a microcontroller with external sensors.
* Implementation of common communication interfaces (UART, I2C, SPI).
* Data acquisition and transmission to external systems.
* Modular hardware and software system design.

## 2. Functional Assumptions
**General assumptions:**
* System based on an ATmega328 microcontroller.
* Cooperation with environmental sensors (temperature, pressure, humidity).
* Cyclic measurement and transmission of data.
* PC-based monitoring of system operation.
* Stable and safe power supply.

**System functionalities:**
* Initialization of microcontroller peripherals.
* Periodic sensor data acquisition.
* Basic processing of measurement data.
* Transmission of data via USB–UART interface.
* Visual indication of system operating status.

## 3. Used Components
* ATmega328 microcontroller
* USB–UART converter
* Environmental sensors (temperature, pressure, humidity)
* Voltage regulator / DC-DC converter
* LED indicator diodes
* Momentary push buttons
* Passive components (resistors, capacitors)
* Prototyping board
* External power supply

## 4. Block Diagram
The system is divided into functional blocks: Power Supply, Microcontroller (Core), Sensor Array, and Communication Interface (USB-UART).

## 5. System Operation Description
After powering up, the system initializes the microcontroller, sensors, and UART module. Then, in the main loop, cyclic measurements from the sensors are performed. The acquired data is processed by the microcontroller and then transmitted to a master system or user application. Additionally, the system indicates correct operation using LED indicators.

## 6. Project Development Process
**Stage I – Analysis and concept:**
* Defining the project goal.
* Selecting the microcontroller, sensors, and additional components.
* Dividing the system into functional blocks.

## 7. Hardware Design
**Stage II – Hardware Design:**
* Designing the electrical schematic in KiCad.
* Selecting power supply components.
* Designing connections between the microcontroller and sensors.
* Creating the Printed Circuit Board (PCB) layout and 3D visualization.

## 8. Software Implementation
The system software was developed using a modular architecture, ensuring a clear separation between the Graphical User Interface (GUI) and the hardware communication layer.

### 8.1. Presentation and Application Logic Layer
* **mainform.h / mainform.cpp:** Core of the desktop application. Handles GUI events and implements data parsing algorithms using Regular Expressions (Regex) to extract numerical values from sensor text frames.
* **mainform.resX:** XML-based resource file storing metadata regarding the GUI layout.

### 8.2. Communication Layer (Serial Library)
* **serial.h / serial.cc:** Implements the API for serial communication, manages I/O buffers, and configures Baud Rate.
* **win.h / win.cc:** Windows-specific implementations (Win32 API) for low-level control of COM port drivers.
* **list_ports_win.cc:** Algorithm for scanning the system registry to identify active serial ports.

### 8.3. Auxiliary System Modules
* **v8stdint.h:** Ensures standardization of data types (uint8_t, int32_t) for code portability.
* **unix.h / unix.cc:** Provides compatibility for the communication library with Unix-based systems.

**Data Processing Workflow:**
The system operates in an asynchronous mode. Environmental data is transmitted via the USB–UART interface. Upon detecting data in the buffer, the application validates the string, parses the numerical content, and updates dynamic charts in real-time.

## 9. Results and Testing
The system was verified through a series of tests:
* **Initial baseline:** Verification of real-time data acquisition at room temperature.
* **Heating test:** Observation of temperature increase on the application interface.
* **Cooling phase:** Verification of the system's response to decreasing temperature.

## 10. Conclusions
As part of the project, a complete embedded system was developed that enables cooperation between an ATmega microcontroller, sensors, and a PC. The project allowed practical application of knowledge in electronics, microcontroller programming, and communication systems. The use of a Git repository enabled version control and facilitated collaborative development of the implemented solution.
