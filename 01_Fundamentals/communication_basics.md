# Communication fundamentals

## Think in layers
- **Electrical/physical layer:** voltage levels, wires, reference, termination and electrical limits.
- **Interface/data-link behaviour:** clocks, framing, addressing, chip select and arbitration.
- **Application messages:** meaning, units, scaling, sequence, validity and error handling.

SPI and I²C describe bus signalling conventions. UART commonly refers to an asynchronous serial peripheral and its character framing; an application message format is a separate design. CAN defines a data-link protocol and is normally paired with a separate physical-layer transceiver.

## SPI
Synchronous interface commonly using SCLK, MOSI, MISO and chip select. The controller supplies the clock. Full-duplex transfers are possible. Learn CPOL/CPHA, transfer length, clock rate and register access.

## I²C
Two-wire synchronous bus using SDA/SCL. Devices are addressed; transfers use start/stop conditions and ACK/NACK. The lines are typically open-drain and require pull-ups. Learn addressing, bus capacitance, pull-up sizing and recovery.

## UART
Asynchronous serial interface, commonly TX/RX. Both ends agree on baud rate and frame format. UART framing does not define application message boundaries. Learn baud mismatch, buffering, delimiters and parser recovery.

## CAN
Multi-node, message-oriented data-link protocol. Identifiers participate in arbitration and can be used for filtering. An MCU CAN peripheral needs a transceiver to drive/sense CANH/CANL. Learn bit timing, arbitration, termination and error handling.

## Selection
Choose from payload rate, latency, topology, cable length, noise, fault handling, pin count, peripheral availability, cost and maintainability. No interface is universally best.
