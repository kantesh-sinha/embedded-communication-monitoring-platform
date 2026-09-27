# Bench bring-up sequence

Proceed one interface at a time. Record revisions and instrument setup.

| Step | Activity | Evidence | Status |
|---|---|---|---|
| 1 | Inspect boards/modules, pinouts and voltage limits | Photos, revisions, datasheets | PLANNED |
| 2 | Check for shorts while unpowered | Meter readings | PLANNED |
| 3 | Power main Nucleo over USB and check rails | Voltage readings | PLANNED |
| 4 | Flash minimal firmware and test UART | Firmware revision, terminal log | PLANNED |
| 5 | Read IMU identity over SPI | Register response, waveform | PLANNED |
| 6 | Read MCP9808 over I²C | Address/register response, waveform | PLANNED |
| 7 | Bring up second Nucleo and transceiver | Configuration notes | PLANNED |
| 8 | Check CAN termination with power removed | CANH–CANL resistance | PLANNED |
| 9 | Exchange heartbeat and command/status frames | CAN capture and logs | PLANNED |
| 10 | Run integrated monitoring and fault tests | Timestamped logs and counters | PLANNED |

Stop after any failed power or wiring check. Resolve and document the cause before continuing.
