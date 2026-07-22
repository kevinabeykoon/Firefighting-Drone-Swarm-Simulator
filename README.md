# Firefighting Drone Swarm Simulation
<img width="800" height="450" alt="firedronegif1" src="https://github.com/user-attachments/assets/c0e3bed4-1478-4425-bb20-065236e3ce6c" />

A distributed simulation platform that models how autonomous firefighting drones coordinate, communicate, and respond to wildfire incidents in real time across a fault-tolerant network.

---

## Overview

This project simulates a **firefighting drone swarm system** capable of coordinating multiple autonomous drones across large wildfire zones. The platform demonstrates how distributed autonomous agents can dynamically respond to emergencies, balance workloads, recover from failures, and communicate over a network.

The simulation is built around **three independently running subsystems**:

- 🧠 **Scheduler**
- 🚁 **Drone Control System**
- 🔥 **Fire Incident Simulator**

Each subsystem runs as its own process and communicates using **UDP networking**, closely mirroring how real-world distributed systems exchange information under time-sensitive conditions. The simulation can even be executed across **multiple physical devices** on the same network.

---

## Features

- Real-time drone scheduling
- Distributed multi-process architecture
- Configurable simulation engine
- Autonomous drone finite state machines
- Fault injection and recovery simulation
- Performance instrumentation and monitoring
- Dynamic mission reassignment
- Battery and water capacity management
- Configurable wildfire scenarios

---

## System Architecture

The platform follows a **distributed concurrent systems architecture**. Rather than running as a single application, each subsystem operates independently and exchanges information using **UDP packets**.

### 🧠 Scheduler

The Scheduler serves as the central coordination engine and is responsible for:

- Receiving incoming fire incidents
- Tracking drone availability
- Calculating dispatch priorities
- Assigning missions
- Monitoring drone health
- Reassigning abandoned missions

### 🚁 Drone Control System

Each drone behaves as an independent autonomous agent with its own state machine, tracking:

- Current location
- Remaining water supply
- Battery level
- Travel status
- Hardware condition
- Assigned mission

### 🔥 Fire Incident Simulator

The simulator continuously generates wildfire events from configurable scenario files.

Incidents include:

- Fire timestamps
- Severity levels
- Target zones
- Resource requirements

This separation of responsibilities closely reflects real-world distributed infrastructure, where systems communicate over networks rather than sharing memory.

---

## Real-Time Drone Coordination

One of the project's primary engineering challenges was designing a scheduler capable of coordinating multiple drones simultaneously while minimizing emergency response times.

The Scheduler continuously evaluates:

- Drone availability
- Water and foam capacity
- Battery level
- Travel distance
- Current mission status
- Fire severity

Based on this information, drones are dynamically dispatched throughout the simulation.

### Intelligent Dispatching

- Idle drones immediately respond to nearby fires
- In-flight drones can be rerouted to higher-priority emergencies
- Multiple drones cooperate on large fires
- Drones automatically return to base when resources are depleted
- Mission queues prevent incidents from being ignored during heavy activity

Unlike many simulations, drone movement occurs in **real time**—travel, extinguishing fires, and refilling resources all consume simulated time. The overall simulation speed can also be adjusted.

---

## Fault Detection & Recovery

Fault tolerance was a major focus of the project.

The simulation models a variety of real-world failures, including:

- Communication packet loss
- Mid-flight drone failures
- Sensor malfunctions
- Nozzle failures
- Hardware damage

When failures occur, the system automatically detects and responds without interrupting the simulation.

### Recovery Features

- Timeout-based failure detection
- Automatic mission reassignment
- Offline drone isolation
- Permanent fault handling
- Live fault indicators in the monitoring interface

The Scheduler continuously updates its internal state and redistributes missions across the remaining operational fleet.

---

## Drone State Machines

Each drone operates independently using a **finite state machine (FSM)**, allowing autonomous behavior while remaining synchronized with the Scheduler.

### Drone States

- Idle
- En Route
- Extinguishing Fire
- Refilling / Recharging
- Returning to Base
- Faulted
- Decommissioned

This architecture enables highly concurrent execution while maintaining coordinated swarm behavior.

---

## Simulation & Configuration Engine

The simulation is entirely driven by configurable scenario files, making it easy to test different wildfire conditions and scheduling strategies.

Configurable parameters include:

- Fire event timing
- Fire severity
- Zone layouts
- Travel distances
- Drone capacities
- Extinguishing times
- Simulation speed

Using lightweight text-based configuration files allowed for rapid testing and iteration throughout development.

---

## 🛠️ Technologies Used

| Technology | Purpose |
|------------|---------|
| **Java** | Core application and simulation engine |
| **UDP DatagramSockets** | Distributed subsystem communication |
| **Java Threads** | Concurrent drone execution |
| **Java Concurrency** | Real-time synchronization and scheduling |
| **Java Swing** | Live monitoring and visualization interface |

---

## Key Challenges

One of the most difficult aspects of the project was balancing **distributed communication** with **real-time synchronization**.

Because every subsystem runs independently, maintaining consistent state across drones, fire incidents, and scheduling queues required careful coordination.

Additional challenges included:

- Network communication between independent processes
- Designing scalable scheduling algorithms
- Handling communication delays versus genuine failures
- Maintaining synchronized system state
- Building comprehensive tests for distributed behavior

Extensive testing was implemented to validate networking, scheduling, concurrency, and fault recovery across the system.

---

## Example System Workflow

```text
Fire Incident Generated
            │
            ▼
      Scheduler Receives Event
            │
            ▼
Evaluate Drone Availability
            │
            ▼
Calculate Dispatch Priority
            │
            ▼
 Assign Drone(s) via UDP
            │
            ▼
 Drone Travels to Fire
            │
            ▼
Extinguish Fire / Monitor Status
            │
            ▼
 Detect Faults (if any)
            │
            ▼
 Reassign Mission if Needed
            │
            ▼
Return to Base & Refill
```

---

## Learning Outcomes

This project explores several core computer science concepts, including:

- Distributed systems
- Concurrent programming
- Network communication
- Autonomous agent coordination
- Fault-tolerant system design
- Scheduling algorithms
- Real-time simulation
- Finite state machines (FSMs)

---

## Final Thoughts

This project demonstrates how **distributed systems**, **concurrent programming**, and **fault-tolerant architecture** can be combined to coordinate autonomous agents operating in real time.

By simulating large-scale wildfire response with autonomous drones, the platform showcases many of the same engineering challenges found in modern emergency response systems, distributed robotics, and autonomous infrastructure.

---

## License

This project is licensed under the MIT License.<img width="800" height="450" alt="firedronegif1" src="https://github.com/user-attachments/assets/9789c026-7f9c-44c9-8717-6c55690e2f9a" />
