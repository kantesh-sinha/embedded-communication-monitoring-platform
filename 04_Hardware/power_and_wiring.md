# Power and wiring plan

## Initial bench power
Power each NUCLEO board through its documented USB input for initial bring-up. Power breakouts only from a suitable rail after checking their voltage and current requirements. Never tie regulated outputs together. Consider common-ground paths when both boards are USB-connected to the same PC.

## SPI — main MCU to IMU
| Signal | Main MCU direction | Breakout |
|---|---|---|
| SCLK | Output | SCLK |
| MOSI | Output | SDI/MOSI |
| MISO | Input | SDO/MISO |
| CS | Output | CS |
| Supply/GND | — | Only as supported by module |

Exact Nucleo pins and SPI instance: **TBD; verify board revision and CubeMX pin mapping.**

## I²C — main MCU to MCP9808
| Signal | Destination |
|---|---|
| SDA | Sensor SDA |
| SCL | Sensor SCL |
| Supply/GND | Per breakout documentation |

Check onboard pull-ups and address straps before adding resistors. Exact MCU pins: **TBD**.

## UART — main MCU to PC
Prefer the onboard ST-LINK virtual COM port if the board routes a USART to it. Verify exact USART/pins in the board manual/schematic. Do not add a second USB-UART adapter in parallel without checking the circuit.

## CAN — between nodes
Connect each MCU FDCAN_TX/RX to its own compatible transceiver TXD/RXD. Connect CANH-to-CANH and CANL-to-CANL over short twisted pair. For the initial non-isolated bench setup, establish a suitable ground reference. Fit 120 Ω at each physical end; with power removed, a correctly terminated bus typically measures about 60 Ω between CANH and CANL, assuming no additional circuitry affects the reading.

Verify transceiver module pinouts, logic compatibility, standby pins and built-in termination before wiring.

## Pre-power checklist
- Check supply-to-ground for shorts while unpowered.
- Verify polarity and voltage limits.
- Confirm no regulated outputs are tied together.
- Confirm intended CAN termination.
- Power one subsystem at a time.
