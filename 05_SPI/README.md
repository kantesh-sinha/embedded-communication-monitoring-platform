# SPI — IMU interface

**Role:** local vibration/motion acquisition from the ICM-42688-P breakout.

## Concepts
SCLK, MOSI, MISO, chip select, controller/peripheral roles, full-duplex transfers, CPOL/CPHA, register access and transfer timing.

## Experiments
1. Verify breakout supply and pin labels.
2. Verify MCU SPI instance and pins against the exact Nucleo revision.
3. Read the IMU identification register.
4. Capture SCLK, MOSI, MISO and CS with a logic analyzer.
5. Compare transaction duration at multiple supported clock settings.
6. Record mode, clock, transfer length and observed waveform.

Save firmware revision, board/module revisions, capture and conditions under `../12_Results/`. Do not claim measured performance without a physical capture.
