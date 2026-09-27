# SPI — IMU interface

**Project role:** local vibration/motion acquisition from the ICM-42688-P breakout.

## Start with the mental model
SPI is a synchronous serial interface. The controller supplies SCLK and selects a peripheral, commonly with a dedicated chip-select line. MOSI carries controller-to-peripheral data and MISO carries peripheral-to-controller data. A transfer can shift bits in both directions at once.

## What to understand
- SCLK, MOSI, MISO and chip select
- Controller/peripheral roles
- CPOL and CPHA (the SPI mode)
- Bit order, word length and transfer length
- Register addressing and read/write conventions defined by the device
- Clock frequency versus actual transaction duration

## Questions to ask yourself
1. Who is generating the clock, and which device controls the transfer?
2. Which SPI mode does the sensor require? What happens if CPOL or CPHA is wrong?
3. Is chip select active high or low, and when must it change?
4. Does the sensor require a command byte, dummy bytes or a delay before data?
5. What does the datasheet say about maximum clock rate and supply/logic levels?
6. Am I measuring clock frequency, transfer duration or useful payload throughput? They are different quantities.
7. Can I recognize a valid register read in a logic-analyzer capture?
8. What should the firmware do if the returned ID or data is invalid?

## Experiments — in chronological order
1. Inspect the breakout schematic and verify supply, logic level and pin labels.
2. Confirm the exact Nucleo revision, SPI instance and pin mapping.
3. Read the IMU identification register and compare it with the device documentation.
4. Capture SCLK, MOSI, MISO and CS with a logic analyzer; annotate one transaction.
5. Change the supported SPI clock setting and compare transaction duration for the same transfer.
6. Try a controlled incorrect configuration (for example, an unsupported SPI mode) and document the observed failure; restore the valid configuration.
7. Add the sensor to the application acquisition path and record timestamps and error counters.

## What to record
Sensor and board revisions, SPI mode, clock setting, transfer length, firmware commit, capture, measured duration, expected/observed response and any limitations.

Do not claim measured performance without a physical capture. See `../12_Results/README.md` for the result template.
