# Preliminary bill of materials

| Qty | Item | Role | Verify before purchase/use |
|---:|---|---|---|
| 2 | STM32 NUCLEO-G474RE | Main + simulated ECU | Board revision, FDCAN/UART routing, pinout |
| 1 | ICM-42688-P breakout | SPI IMU | Breakout schematic, supply, logic level |
| 1 | MCP9808 breakout | I²C temperature | Supply, address straps, pull-ups |
| 2 | CAN transceiver modules | CAN physical layer | Exact IC/module, VCC, logic, standby, termination |
| 2 | USB cables | Power/program/debug | Board documentation |
| 1 set | Jumper wires | Bench connections | Keep short and secure |
| 1 | Twisted pair | CAN bus | Short linear bench bus |
| 2 | 120 Ω resistors | CAN termination | Only if not already provided by modules |
| 1 | Multimeter | Continuity/voltage | Suitable range |
| 1 | Logic analyzer | SPI/I²C/UART observation | Input voltage compatibility |

Do not buy separate TJA1051 ICs if the selected modules already contain them. Do not assume module connector labels guarantee voltage compatibility. Record vendor, part number, revision and datasheet for each actual item.
