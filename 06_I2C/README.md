# I²C — temperature sensor interface

**Project role:** low-rate temperature acquisition from the MCP9808 breakout.

## Start with the mental model
I²C uses two shared signal lines: SDA for data and SCL for clock. Devices use addresses, and the receiver acknowledges bytes. The lines are typically open-drain, so pull-up resistors establish the high level. Exact device register operations come from the sensor datasheet.

## What to understand
- SDA and SCL; open-drain versus push-pull
- Start, repeated-start and stop conditions
- 7-bit address and read/write bit
- ACK and NACK
- Pull-up resistance, bus capacitance and rise time
- Register access and error handling

## Questions to ask yourself
1. What is the sensor's 7-bit address, and how is it configured on the breakout?
2. Are any other devices using the same address?
3. Who provides the pull-ups? Are there already resistors on the breakout?
4. Are the pull-ups connected to a voltage safe for both devices?
5. What does an ACK confirm, and what does it not confirm?
6. Does this register read need a repeated-start or a stop between phases?
7. What does the bus look like when a device is missing or holds a line low?
8. Can firmware recover or report the fault without hanging the application?

## Experiments — in chronological order
1. Inspect the breakout schematic, supply limits, address straps and pull-ups.
2. Verify MCU I²C pins and configured bus speed against the board documentation.
3. Scan for the configured address and record the response.
4. Read the documented identification and temperature registers.
5. Capture SDA/SCL and identify address, R/W, ACK/NACK and start/stop conditions.
6. Perform a controlled, power-safe disconnect test and record software behaviour.
7. Reconnect and verify that normal acquisition resumes, if recovery is part of the implementation.

## What to record
Address, bus speed, pull-up configuration, module revision, waveform, returned register values, error code and recovery behaviour.

Do not assume that a responding address means the sensor data is valid. See `../12_Results/README.md` for the result template.
