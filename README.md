# Siemens-Simatic-s7-1200-project
This is my final project for the 'Automated Control Systems Based on Simatic S7-1200' course. Our chosen topic is 'Industrial Automation of a Final Assembly and Packaging System using Siemens SIMATIC S7-1200'.


# 📝Project Description & Goal
## 💡 Why This Project? 

Let’s be honest: doing the same repetitive, theoretical university assignments can get a bit uninspiring after a while. I wanted to break away from the classic textbook exercises and build something that felt **real**. 

I asked myself: *“Why not bridge the gap between academia and actual industry by automating and simulating a complex, real-world production line?”* 

That thought led me to this project. I have always been fascinated by innovative industrial processes, and I wanted to see how a top-tier industrial controller like the Siemens SIMATIC S7-1200 handles a dynamic, fast-paced environment. Automating a final assembly and packaging line from scratch allowed me to dive deep into complex algorithms, timing logic, and system synchronization—exactly the kind of challenges that turn an engineering student into a real automation professional.

## Message from the Author

This project represents one of my very first serious milestones as an engineering student diving into the world of industrial automation. 

Since this was developed during my university years, the control logic and architecture might not be 100% perfect, and there is definitely room for optimization. However, every bug encountered and every configuration challenge faced was a massive learning experience. I am sharing this repository openly to document my progress, and I welcome any constructive feedback or suggestions from seasoned automation professionals!

## Project Description

The selected technological process represents a dual-stream automated final assembly and packaging line for electronic modules. Two identical production streams operate in parallel to increase throughput and reduce cycle time variability. Each stream processes one semi-finished module, which is later merged into a single final product.

## 💻 Simulation & Virtual Commissioning (Factory I/O)

It is important to note that this project is implemented as a **full digital simulation** (Virtual Commissioning) rather than being connected to physical industrial machinery. However, the control logic is 100% real: the program runs entirely on a physical **Siemens SIMATIC S7-1200 PLC** and a hardware **HMI panel**.

To bring this simulation to life and make it visually clear, we integrated the system with **Factory I/O**. 

### Why Factory I/O?
* **Real-time 3D Visualization:** It allowed us to build a rich, dynamic 3D smart factory environment that mimics real physical sensors, conveyor belts, and pneumatic actuators.
* **Seamless PLC Integration:** Factory I/O connects directly to our physical S7-1200 PLC via standard Ethernet protocols. This means the PLC "thinks" it is controlling a real factory line, executing our exact ladder/FBD logic.
* **Risk-Free Testing:** It provided a perfect sandbox environment to test complex algorithms, sensor synchronization, and emergency scenarios without the risk of damaging expensive physical hardware.
