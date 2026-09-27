# CAN — inter-node communication

**Project role:** command/status exchange between the main monitoring controller and simulated motor ECU.

## Start with the mental model
CAN is a multi-node, message-oriented data-link protocol. Nodes transmit frames on a shared bus. Identifiers help describe message meaning and participate in arbitration; they are not simply device addresses. The MCU's FDCAN peripheral requires an external transceiver to connect to the differential CANH/CANL bus.

## What to understand
- CAN controller/peripheral versus physical-layer transceiver
- CANH/CANL, differential signalling and reference/ground
- Classical CAN frame, identifier, DLC and payload
- Bit timing and nominal bit rate
- Arbitration and identifier priority
- Acceptance filters, ACK, error states and bus-off
- Bus topology, termination and stubs
- Application-level timeout and safe-state behaviour

## Questions to ask yourself
1. Am I debugging the MCU's CAN controller, the transceiver, wiring or the application message?
2. Is the transceiver compatible with the MCU logic level and its supply?
3. Is the bus a short linear trunk, and are there exactly two end terminations?
4. Do both nodes use compatible nominal bit timing?
5. What does an identifier mean in this system? How is priority assigned?
6. What are the payload byte order, scaling, units and validity rules?
7. What happens if a heartbeat or command stops arriving?
8. How does the ECU report a fault, and what is the defined simulated safe state?
9. How will I distinguish no ACK, wrong bit timing, wiring faults and an application-level rejection?

## Proposed classical CAN message map
Proposal only; freeze byte order, scaling, rates and validity rules before implementation.

| ID (hex) | Direction | DLC | Proposed content |
|---|---|---:|---|
| 0x100 | Main → ECU | 8 | Enable, mode, requested speed, sequence |
| 0x180 | ECU → Main | 8 | State, simulated speed, accepted sequence |
| 0x181 | ECU → Main | 8 | Fault flags and diagnostic code |
| 0x200 | ECU → Main | 4 | Heartbeat counter and state |

Use standard 11-bit identifiers initially. Define every field and update rate in a versioned interface-control document.

## Experiments — in chronological order
1. Verify FDCAN pin mapping and transceiver module documentation for both nodes.
2. Check unpowered wiring and termination before powering the bus.
3. Configure the same nominal bit rate and compatible bit timing on both nodes.
4. Exchange a periodic heartbeat and inspect it with a suitable CAN analyzer.
5. Add command/status exchange and validate payload fields.
6. Study identifier filtering and arbitration with controlled simultaneous traffic.
7. Stop one node and observe heartbeat timeout, diagnostics and simulated safe-state behaviour.
8. Record error counters and recovery after restoring the node.

A generic logic analyzer is not a substitute for a CAN analyzer when examining CAN frames and physical-layer behaviour. Do not add termination blindly; check whether modules already include selectable termination.
