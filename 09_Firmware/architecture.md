# Firmware architecture

## Proposed modules
```text
Core/
  Inc/ app_state.h app_config.h app_messages.h
  Src/ main.c app.c app_state.c sensor_manager.c diagnostics.c
       uart_console.c can_transport.c can_messages.c
       spi_imu.c i2c_temperature.c
```

- `spi_imu`: sensor register access and acquisition.
- `i2c_temperature`: MCP9808 register access and conversion.
- `uart_console`: bounded RX buffering, parsing and telemetry.
- `can_transport`: frame I/O and transport error counters.
- `can_messages`: encode/decode and application-field validation.
- `sensor_manager`: sampling, timestamps and validity.
- `diagnostics`: link/sensor health and counters.
- `app_state`: modes and safe simulated ECU behaviour.

Start with polling or interrupt-driven transfers that are easy to inspect. Add DMA only when there is a measurable reason. Keep callbacks short and buffers bounded. This is a design scaffold, not a claim that firmware compiles or has run. Generate board-specific initialization only after verifying exact pins and revisions.
