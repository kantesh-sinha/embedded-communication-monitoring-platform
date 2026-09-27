# CAN — inter-node communication

**Role:** command/status exchange between the main monitoring controller and simulated motor ECU.

Each STM32 FDCAN peripheral needs a compatible external transceiver. Use a short linear CANH/CANL bus with 120 Ω termination at each physical end. Check whether modules include selectable termination before adding resistors.

## Proposed classical CAN message map
Proposal only; freeze byte order, scaling, rates and validity rules before implementation.

| ID (hex) | Direction | DLC | Proposed content |
|---|---|---:|---|
| 0x100 | Main → ECU | 8 | Enable, mode, requested speed, sequence |
| 0x180 | ECU → Main | 8 | State, simulated speed, accepted sequence |
| 0x181 | ECU → Main | 8 | Fault flags and diagnostic code |
| 0x200 | ECU → Main | 4 | Heartbeat counter and state |

Use standard 11-bit identifiers initially. Define byte order, signedness, scaling, reserved values and update rates in a versioned interface-control document.

## Experiments
1. Confirm common nominal bit rate and compatible timing.
2. Check wiring and termination.
3. Exchange periodic heartbeat.
4. Send command and verify simulated response.
5. Study filtering and identifier priority with multiple IDs.
6. Stop a node and observe timeout/error behaviour.
7. Capture traffic with a suitable CAN analyzer. A generic logic analyzer is not a substitute for a CAN physical-layer analyzer.
