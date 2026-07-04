# PLC Logic 

The control logic for the Automated Final Module Assembly & Packaging System was developed using Siemens TIA Portal (Totally Integrated Automation Portal) V19. The PLC program was implemented using Structured Control Language (SCL) and Ladder Logic (LAD), enabling modular, readable, and maintainable code. Key functions—including conveyor control, robotic sequencing, sensor feedback handling, interlocks, and mode selection (automatic/manual)— were structured into networks with clear naming conventions and memory bit management. Timers, set/reset coils, and safety conditions (e.g., emergency stop, start authorization) were integrated to ensure reliable and safe operation. The TIA Portal environment facilitated seamless simulation, online monitoring, and HMI, PLC integration, allowing full validation of the system logic without physical hardware.

![Суреттің сипаттамасы](./images/diagram.jpg)

### 🔄 System Operation & Process Flow

The interaction between the process units is governed by a sequential control state machine implemented in the S7-1200 PLC. The material flow follows a precise automated cycle:

1. **Material Transport Phase:** The `8 x Conveyors` operate synchronously in indexed mode. `Presence sensors` placed along the tracks continuously monitor the line, sending digital signals to the PLC to run or pause the conveyor motors, preventing any component collisions.

2. **Processing Phase:** Once a component arrives at a designated workstation, the `Position sensor` triggers a halt signal for that conveyor section. The PLC then initiates the `2 x Machining Centers` by sending a *Start* signal. The system monitors the *Busy* feedback line during execution and waits for the *Done* handshake signal before proceeding.

3. **Handling & Sorting Phase:**
   After secondary processing, the `3 x Robotic Manipulators` receive execution commands from the PLC. Utilizing position and status feedback loops, the manipulators safely perform pick-and-place operations, transferring completed components to the final packaging stage or sorting out defective units based on sensor criteria.

---

### 🛡️ Safety & Diagnostic Interlocks

To ensure safe operation across all process units, the following software interlocks are active within the TIA Portal logic:
* **Emergency Halt:** If the Emergency Stop is pressed, all digital outputs driving the conveyors and robotic arms are instantly de-energized.
* **Sensor Timeout Fault:** If a conveyor operates for more than 10 seconds without a `Presence sensor` detecting a material transition, the system triggers a "Stalled Material" alarm and pauses the sequence.
* **Robot Collision Avoidance:** The PLC monitors the status feedback of the `Robotic Manipulators`. A robot cannot enter the conveyor workspace unless the corresponding conveyor section is confirmed completely stationary by the `Position sensor`.
