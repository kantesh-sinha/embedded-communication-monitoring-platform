# Design decision log

| ID | Decision | Rationale | Status |
|---|---|---|---|
| D-001 | Two identical NUCLEO-G474RE boards | Simplifies reuse and makes CAN tangible | Proposed; verify revision |
| D-002 | SPI for IMU, I²C for temperature, UART for PC, CAN between nodes | Distinct educational roles | Design baseline |
| D-003 | Simulate motor in first milestone | Avoids motor power/safety complexity during communication bring-up | Design baseline |
| D-004 | USB power for initial bench tests | Avoids unnecessary custom power circuit | Grounding review required |
| D-005 | Defer mechanical mounts | Measure actual hardware before CAD | Design baseline |

## Revision history
- Initial scaffold: architecture and verification plan documented; hardware and firmware remain unvalidated.
