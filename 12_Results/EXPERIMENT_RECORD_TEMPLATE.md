# Experiment Record Template

Copy this file for each experiment and rename it with a unique ID (for example, `EXP-001-uart-parser.md`). Keep measured results separate from expected behaviour.

## Experiment identification

- Experiment ID:
- Title:
- Date / time:
- Protocol / subsystem:
- Requirement or question:
- Status: PLANNED / RUN / PASS / FAIL / BLOCKED
- Hardware revision(s):
- Firmware commit / build configuration:

## Hypothesis

What do you expect to observe, and why?

## Setup

- Node(s) and peripherals:
- Wiring / topology:
- Configured bus rate / UART baud:
- Payload and update rate:
- Instrument(s) and settings:
- PC tools / scripts:
- Power and environmental conditions:

## Procedure

1.
2.
3.

## Acceptance criteria

Define what would confirm or reject the hypothesis before running the experiment.

- Expected behaviour:
- Pass criteria:
- Failure criteria:

## Results

| Measurement | Expected | Observed | Units / method | Notes |
|---|---|---|---|---|
| TBD | TBD | NOT MEASURED | TBD | NOT RUN |

## Evidence

- Build output:
- Terminal transcript:
- Logic-analyzer / oscilloscope capture:
- CAN capture / error counters:
- Raw logs / data:
- Reproduction command or script:

Link the original evidence and note the firmware commit and instrument configuration.

## Interpretation

- What does the evidence support?
- What does it not establish?
- Unexpected behaviour:
- Measurement uncertainty / limitations:
- Next experiment or corrective action:

## Review rule

Do not infer physical bus behaviour from source code alone. Record what was configured, where and how it was measured, and the limits of the observation.
