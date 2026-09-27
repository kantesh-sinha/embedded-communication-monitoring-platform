# I²C — temperature sensor interface

**Role:** low-rate temperature acquisition from the MCP9808 breakout.

## Concepts
SDA/SCL, open-drain signalling, pull-ups, start/repeated-start/stop, 7-bit addressing, ACK/NACK and register access.

## Experiments
1. Inspect breakout schematic for pull-ups and address straps.
2. Verify supply and MCU I²C pins.
3. Scan for the configured address.
4. Read identification and temperature registers.
5. Capture SDA/SCL and identify address, R/W and ACK/NACK.
6. Perform a controlled, power-safe disconnect test and record the software response.

Record bus speed, address, pull-up configuration, module revision, capture and observed error handling.
