# UART — PC debug and telemetry

**Role:** interactive console and telemetry between the main controller and PC.

UART defines serial character framing (baud, data bits, parity, stop bits); it does not inherently define application message boundaries. Start with newline-delimited UTF-8 text. Use bounded buffers, reject oversized/malformed lines and define parser recovery.

Illustrative, not finalized:
```text
telemetry,seq=42,temp_c=24.75,imu_rms=0.018,can_ok=1
```

## Experiments
- Verify the board's ST-LINK virtual COM port and USART routing.
- Observe TX/RX using a terminal and logic analyzer.
- Change baud rate at both ends and observe mismatch.
- Send incomplete, malformed and oversized lines.
- Test timeout handling and parser recovery.

Define units, escaping, numeric limits and versioning before treating the example as a wire protocol.
