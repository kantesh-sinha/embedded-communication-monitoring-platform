# Interface selection

| Requirement | Chosen interface | Reason in this demonstrator | Trade-off |
|---|---|---|---|
| Local motion/vibration sensor | SPI | Makes clocked register transfers and timing observable | More signal lines and chip-select handling |
| Low-rate local temperature | I²C | Addressed shared bus suits a low-rate sensor | Pull-ups, capacitance and recovery |
| PC console/telemetry | UART | Simple serial debug path | Requires agreed baud and application framing |
| ECU-to-ECU exchange | Classical CAN | Realistic distributed-control network | Transceivers, bit timing and termination |

| Attribute | SPI | I²C | UART | CAN |
|---|---|---|---|---|
| Clocking | Synchronous | Synchronous | Asynchronous | Bit-timed |
| Topology | Usually controller/peripheral | Shared addressed bus | Usually point-to-point | Multi-node bus |
| Signals | SCLK/MOSI/MISO/CS | SDA/SCL | TX/RX | CANH/CANL |
| Selection | Chip select | Address | Link endpoint | Identifier/filter |
| Common role | Local fast peripheral | Local low-rate peripheral | Debug/module/PC link | Distributed nodes |

This allocation is a learning design, not a claim that these are the only suitable uses. Compare interfaces only under defined, comparable conditions.
