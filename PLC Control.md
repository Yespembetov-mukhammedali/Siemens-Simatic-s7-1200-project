# 🔧 PLC Control & Software Architecture

The control software for the system is developed within the **Siemens TIA Portal** environment. The program utilizes a hybrid architecture, combining **Ladder Logic (LAD)** for sequential control/interlocking and **Structured Control Language (SCL)** for data handling and numerical calculations.

---

## 📐 1. Process Overview & Hardware Layout

Before detailing the code structure, the physical layout of the automated assembly and packaging lines is organized into two parallel operating streams, synchronized by a central control logic.

### 2.1 Technological Scheme Development

![Technological Scheme](./images/ЖОҒАРЫДАҒЫ_СУРЕТТІҢ_АТЫ.png)

The layout features a dual-stream configuration (`LINE 1 / Stream A` and `LINE 2 / Stream B`) executing simultaneous transport, machining, and material handling tasks.

---

## 💻 2. Program Structure & Functions

The PLC software is modularized into dedicated blocks to ensure clean diagnostic capabilities and routine maintenance:

* **Conveyor Control:** Manages motor start/stop sequences, dynamic speed staging, and index positioning.
* **Robotics Sequencing:** Handles handshake bits (Start, Busy, Done) between the PLC and the robotic manipulators.
* **Sensor Feedback Processing:** Features software debounce filters for `Presence` and `Position` sensors to eliminate physical signal noise.
* **Safety & Interlocks:** Evaluates emergency stop states, execution permissions, and hardware limits.

### 📊 Controller Resource Allocation
The software memory and execution routines are managed through the following block framework:

| Block Type | Identifier | Function Description |
| :--- | :--- | :--- |
| **Organization Block** | OB1 (Main) | Cyclic execution of the main state machine and interlock updates. |
| **Function Block** | FB (Conveyor_Ctrl) | Reusable instance block for indexing and motor state outputs. |
| **Function** | FC (Safety_Evaluate)| Logic matrix evaluating E-Stop inputs and fault conditions. |
| **Data Block** | DB (Global_Status) | Global registers storing real-time system tags and HMI bits. |

---

## ⚙️ 3. Execution Modes

The control logic supports two primary operating states selected via the operator panel:
1. **Automatic Mode:** Full sequential execution governed by the PLC state machine, utilizing sensor flags for automated step transitions.
2. **Manual Mode:** Bypasses sequence steps to allow direct, individual jogging of actuators via the HMI for maintenance and line commissioning.
