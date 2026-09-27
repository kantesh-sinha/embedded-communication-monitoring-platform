# UART — PC debug and telemetry

**Project role:** interactive console and telemetry between the main controller and PC.

## Start with the mental model
UART is an asynchronous serial interface. The endpoints agree on baud rate and character format because there is no separate clock line. UART framing describes individual characters; it does not define the structure or meaning of an application message.

## What to understand
- TX and RX directions
- Baud rate, data bits, parity and stop bits
- Start and stop bits; idle state
- Character framing versus application-level framing
- Polling, interrupts, DMA and bounded receive buffers
- Parsing, validation and recovery

## Questions to ask yourself
1. Which side transmits on TX, and where does that signal connect?
2. Do both endpoints agree on baud rate and frame format?
3. Is the PC connection a native UART, USB-UART bridge or ST-LINK virtual COM port?
4. How does the receiver know where one application message ends?
5. What happens if a line is incomplete, malformed or longer than the buffer?
6. Can a slow PC or full transmit buffer block time-critical acquisition?
7. Are numeric values, units, separators and encoding unambiguous?
8. How can I distinguish a UART electrical/framing problem from a parser bug?

## Initial application format
Start with newline-delimited UTF-8 text, for example:

```text
telemetry,seq=42,temp_c=24.75,imu_rms=0.018,can_ok=1
```

This is an illustrative format, not a finalized protocol. Define field names, units, numeric limits, escaping and versioning before depending on it.

## Experiments — in chronological order
1. Verify the board's ST-LINK virtual COM port and USART routing.
2. Send a short known string and confirm it in a terminal.
3. Observe TX with a logic analyzer and verify the configured baud and character format.
4. Implement a bounded line receiver and parser.
5. Send incomplete, malformed and oversized lines; verify rejection and recovery.
6. Compare behaviour at different supported baud rates and under continuous telemetry.
7. Add status/error counters so communication failures are visible to the application.

## What to record
USART mapping, baud/frame settings, buffer size, message format version, firmware commit, test input, terminal log and observed error handling.
