# Verification plan

Define acceptance thresholds from requirements and hardware documentation before running tests. Do not retrofit limits to fit results.

| ID | Feature | Method | Evidence | Acceptance |
|---|---|---|---|---|
| PWR-01 | No unintended supply short | Unpowered resistance/continuity check | Meter record | No short; threshold per circuit |
| UART-01 | PC link exchanges valid lines | Send/receive tests | Terminal log | All defined messages parsed correctly |
| SPI-01 | IMU register access | Read identity register | Register log + logic capture | Matches documented device value |
| I2C-01 | Sensor responds | Address/register read | Capture + firmware log | Expected ACK and valid register |
| CAN-01 | Nodes exchange frames | Periodic heartbeat | CAN capture | Valid frames at configured rate |
| CAN-02 | ECU handles timeout | Stop command source | Timestamped log | Simulated safe state within specified timeout |
| INT-01 | Concurrent operation | Integrated run | Logs, timings, counters | Meets predeclared criteria |
| ERR-01 | Sensor disconnect detected | Controlled disconnect | Error/status log | Fault reported; defined state maintained |

For every run record date, operator, hardware revisions, firmware commit, configuration, instruments, procedure, raw evidence, result and deviations.
