# ATmega Microcontroller with Sensors and PC Application
### My Contribution

I was responsible for the end-to-end development of the system, which included:

* **Hardware Integration**: I designed and implemented the physical connections between the ATmega328 microcontroller and the sensor array (temperature, pressure, humidity). I ensured proper electrical integration and sensor configuration for accurate data acquisition.
* **Firmware Development**: I wrote the complete firmware for the microcontroller in C. This included initializing peripherals, implementing periodic sensor sampling, and developing the logic for data transmission via the UART interface.
* **Desktop Application**: I designed and implemented the PC-side monitoring application. This involved creating a Graphical User Interface (GUI) and implementing data parsing algorithms using Regular Expressions (Regex) to extract numerical values from sensor text frames and visualize them on dynamic charts in real-time.

**Project carried out by:**
* Monika Bogdalska - KiCAD schematic and docummentation 
* Wiktor Baran - end-to-end development of the system
* Mikołaj Polewka - KiCAD PCB design

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
<img width="602" height="357" alt="image" src="https://github.com/user-attachments/assets/0164e6d3-68de-45cd-8928-9955764ddd76" />

## 5. System Operation Description
After powering up, the system initializes the microcontroller, sensors, and UART module. Then, in the main loop, cyclic measurements from the sensors are performed. The acquired data is processed by the microcontroller and then transmitted to a master system or user application. Additionally, the system indicates correct operation using LED indicators.

## 6. Project Development Process
**Stage I – Analysis and concept:**
* Defining the project goal.
* Selecting the microcontroller, sensors, and additional components.
* Dividing the system into functional blocks.

## 7. Hardware Design
**Stage II – Hardware Design:**
* Designing the schematic diagram,
* Selecting power supply components,
* Designing connections between the microcontroller, sensors
   <img width="604" height="357" alt="image" src="https://github.com/user-attachments/assets/e6858b6b-fa45-4716-8403-6609801d4e58" />
   
* Figure 1. Electrical schematic of the embedded system based on the ATmega328 microcontroller designed in KiCad.
   <img width="1085" height="592" alt="image" src="https://github.com/user-attachments/assets/ed2b3db2-ec09-4ecb-bba5-ea5557f37127" />
   
* Figure 2. Printed Circuit Board (PCB) layout of the system designed in KiCad.
   <img width="1089" height="630" alt="image" src="https://github.com/user-attachments/assets/c1070c4d-fd30-4733-8d76-98105ca54b27" />
   
* Figure 3. 3D visualization of the PCB with mounted components generated in KiCad.

## 8. SOFTWARE IMPLEMENTATION
**Stage III – Implementation and Testing**
* writing the microcontroller software,
* testing communication with sensors,
* testing data transmission,
* verifying correct system operation.

The system software was developed using a modular architecture, ensuring a clear separation between the Graphical User Interface (GUI) and the hardware communication layer. The following sections describe the technical roles of the specific source files:

### 8.1. Presentation and Application Logic Layer
* **mainform.h / mainform.cpp:** These files constitute the core of the desktop application. They define the form class, initialize GUI controls, and handle system events. These files implement the data parsing algorithms that utilize **Regular Expressions (Regex)** to extract numerical values from the text frames sent by the sensors.
* **mainform.resX:** An XML-based resource file that stores metadata regarding the GUI layout, ensuring visual consistency of the application's interface.

### 8.2. Communication Layer (Serial Library)
A stable data exchange channel between the ATmega328 microcontroller and the PC is maintained by the following modules:
* **serial.h / serial.cc:** These files implement the Application Programming Interface (API) for serial communication. They manage input/output buffers and configure transmission parameters, such as the Baud Rate.
* **win.h / win.cc:** These contain Windows-specific implementations of system calls (Win32 API) necessary for low-level control of COM port drivers.
* **list_ports_win.cc:** This module implements the algorithm for scanning the system registry to identify active serial ports and provide their parameters to the user.

### 8.3. Auxiliary System Modules
* **v8stdint.h:** This header ensures the standardization of data types (e.g., uint8_t, int32_t), guaranteeing code portability and correct interpretation of binary data across different processor architectures.
* **unix.h / unix.cc:** These files provide compatibility for the communication library with Unix-based systems, demonstrating the versatility of the software design.

**Data Processing Workflow**
The system operates in an asynchronous mode. Environmental data generated by the sensors is cyclically transmitted via the USB–UART interface. Upon detecting data in the buffer (via `serial.cc`), the application validates the string, parses the numerical content, and updates the dynamic chart objects in real-time within the `mainform.cpp` logic.

## 9. RESULTS AND TESTING

   <img width="956" height="538" alt="image" src="https://github.com/user-attachments/assets/adb2452b-cd60-455d-9083-449df4f88afc" />

* **Figure 4.** Application interface displaying real-time sensor data acquisition: initial baseline measurements.
 
   <img width="954" height="540" alt="image" src="https://github.com/user-attachments/assets/328094c3-7078-418e-9916-50eb7ffbf9e7" />

* **Figure 5.** Application interface displaying real-time sensor data acquisition: temperature increase during the heating test.
 
   <img width="966" height="545" alt="image" src="https://github.com/user-attachments/assets/5a971bad-6772-42cd-8930-eee4243e9882" />

* **Figure 6.** Application interface displaying real-time sensor data acquisition: temperature decrease during the cooling phase.

## 10. CONCLUSIONS
As part of the project, a complete embedded system was developed that enables cooperation between an ATmega microcontroller, sensors, and a PC. The project allowed practical application of knowledge in electronics, microcontroller programming, and communication systems. Additionally, the project was published in a Git repository, which enabled version control, collaborative development, and facilitated better understanding and analysis of the implemented solution.
