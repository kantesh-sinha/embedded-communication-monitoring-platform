# Project review and next development steps

This page turns the design into a sequence of implementable firmware and bench milestones. The project is currently in design/prototype planning; no hardware or firmware test is claimed complete.

## Current baseline

- Two-node STM32 architecture: designed.
- SPI IMU, I²C temperature sensor, UART console and CAN ECU roles: defined.
- Hardware BOM and wiring: provisional; exact board/module revisions and pin mapping remain to be verified.
- Firmware: placeholder only; no complete buildable application or measured protocol results yet.

## Development milestones

| Milestone | Implementation | Evidence | Exit condition |
|---|---|---|---|
| M0 — Hardware freeze | Record board/module part numbers, revisions, schematics and pin mapping | Revision-controlled BOM and wiring | Voltage and pin compatibility checked |
| M1 — UART foundation | Generate STM32 project; implement bounded RX and nonblocking TX | Build log, terminal transcript, parser tests | Valid, malformed and oversized lines handled |
| M2 — SPI sensor | Implement ICM-42688-P identity/configuration/data reads | Register log and logic-analyzer capture | Identity and configured data path verified |
| M3 — I²C sensor | Implement MCP9808 address and temperature reads | Bus capture and plausibility check | Valid readings and absent-device handling |
| M4 — CAN link | Configure FDCAN and transceivers; implement heartbeat | Two-node CAN capture and error counters | Both nodes exchange defined frames |
| M5 — Integrated application | Timestamp acquisition; combine telemetry, status and diagnostics | Timestamped logs and CPU/loop timing | Concurrent operation meets declared criteria |
| M6 — Fault campaigns | Inject sensor, UART and CAN faults | Reproducible fault logs | Detection, reporting and recovery match requirements |

## Firmware improvements

- Replace the placeholder main.c with a reproducible STM32CubeIDE/CMake project after freezing the exact board and pin mapping.
- Keep hardware drivers, protocol framing, application logic and diagnostics in separate modules.
- Use bounded buffers and nonblocking or timeout-bounded operations; avoid indefinite waits in the main loop.
- Define a versioned interface-control document for CAN identifiers, DLC, byte order, scaling, units, update rate, validity and timeout behavior.
- Define a versioned UART message format with parser limits and error responses.
- Add build instructions, toolchain versions, board configuration and a known-good configuration export.
- Add host-side unit tests for parsers, scaling, state transitions and CAN payload encode/decode where practical.

## Measurement discipline

For protocol comparisons, state the payload, configured rate, measurement point and instrument. Distinguish bus bit rate, transaction duration, application latency and useful payload throughput. Compare only equivalent workloads; do not claim a universal speed or robustness winner.

For every experiment, record hardware revision, firmware commit, configuration, setup, expected result, observed result, raw evidence and limitations.

## Definition of done

The first meaningful release is a reproducible two-node demonstration in which all four interfaces work in their intended roles, telemetry remains responsive during concurrent acquisition, and defined communication faults produce observable, bounded behavior. Until that evidence exists, keep the status at planning or implementation.
