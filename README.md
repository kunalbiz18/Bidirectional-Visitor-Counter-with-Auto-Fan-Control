🚶↔️ Bidirectional Visitor Counter with Automatic Fan Control

A Smart Energy Management System built on the Arduino platform to accurately track occupancy and automate appliance control, specifically a fan, to conserve energy and enhance comfort.

✨ Project Overview

This project solves the common problem of energy wastage caused by electrical appliances (like fans) running unnecessarily in unoccupied rooms. By using a bidirectional visitor counter, the system maintains a real-time count of people inside a space. When the count is zero, the fan is automatically switched off. When the count is one or more, the fan is switched on.

🎯 Key Objectives

Accurate Counting: Implement a reliable bidirectional counting mechanism to track people entering and exiting a room.

Real-time Monitoring: Display the current occupancy count on an LCD screen.

Smart Automation: Automatically control an appliance (Fan) based on the calculated occupancy status.

Energy Conservation: Reduce electricity consumption by eliminating unnecessary fan operation.

🧰 Components and Circuit Mechanism

The system is built around the Arduino microcontroller, utilizing two primary sensors for direction detection and a relay module for fan control.

Hardware Components

ComponentFunctionNotes

Arduino UNO/NanoMicrocontrollerThe brain of the system, runs the counting logic and controls the fan.

IR Sensor Module (x2)Entry/Exit DetectionTwo sensors placed in a sequence to determine the direction of movement.

16x2 LCD DisplayOutput/MonitoringDisplays the current, real-time visitor count.

Relay Module (1-Channel)Fan ControlActs as an electromagnetic switch to turn the high-voltage fan ON/OFF based on the Arduino signal.

DC Fan / AC Fan with adapterControlled ApplianceThe target appliance for automatic control.

Power SupplySystem PowerRequired for powering the Arduino and sensors.

Breadboard & WiresPrototypingFor connecting all the components.

Sensor Mechanism: Bidirectional Counting

Dual Sensor Setup: Two IR (Infrared) sensors, let's call them Sensor 1 (IN) and Sensor 2 (OUT), are placed close together at the doorway.

Entry Logic: When a person enters, they first trigger Sensor 1 and then Sensor 2.

Sequence: S1 High $\rightarrow$ S2 High

Action: Visitor_Count++

Exit Logic: When a person exits, they first trigger Sensor 2 and then Sensor 1.

Sequence: S2 High $\rightarrow$ S1 High

Action: Visitor_Count--

Display Update: The Visitor_Count is immediately updated on the LCD.

⚙️ Project Workflow

The entire system operates in a continuous loop managed by the Arduino program.

Initialization:Arduino powers on.

LCD is initialized, displaying a welcome message and the initial count (0).

IR sensors and Relay pins are set up.

Fan is initially OFF.

Detection Phase:Arduino continuously monitors the state of Sensor 1 and Sensor 2.

When one sensor is triggered, the program checks the state of the other sensor to determine the direction.

Counting Phase:Based on the sequence of activation (S1 then S2 for IN, or S2 then S1 for OUT), the Visitor_Count is incremented or decremented.

The new count is immediately sent to the LCD.

Control Phase (Automation):The program checks the Visitor_Count:

If Visitor_Count > 0: The system sends a HIGH signal to the Relay, closing the circuit and turning the Fan ON.

If Visitor_Count == 0: The system sends a LOW signal to the Relay, opening the circuit and turning the Fan OFF.

Loop: The system returns to the Detection Phase, waiting for the next movement.

💻 Arduino Code Snippet

This is a simplified example of the core logic. Actual implementation requires careful debounce logic and state management for reliable counting.