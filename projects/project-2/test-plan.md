# Project 2 — Functional Test Plan

This procedure was added during portfolio documentation to guide future measurements. It records the reported circuit behavior separately from measurements that still need to be collected.

## Expected behavior

- LED activation responds to ambient room light.
- When the light sensor is fully covered, two LEDs blink at a reported **8 Hz**.
- An 8 Hz signal has a period of **125 ms**, calculated from `T = 1 / f`.

The LED thresholds, duty cycle, and whether the two LEDs blink together or alternately have not yet been documented.

## Record the setup

Before testing, record the supply voltage, sensor type, test date, instrument details, and lighting arrangement. Use the same supply setting and board orientation when comparing lighting conditions.

## Test cases

| Case | Procedure | Record |
| --- | --- | --- |
| Ambient-light response | Observe the board under steady room lighting, then progressively shade the sensor | Which LEDs are active and how their state changes |
| Fully covered sensor | Completely cover the sensor and observe both blinking LEDs | Blink pattern, each LED's frequency, period, and duty cycle |
| Recovery | Uncover the sensor after the blinking condition | Whether the board returns to its ambient-light response and any delay |
| Repeatability | Repeat the cover/uncover cycle several times under the same conditions | Whether transitions and blink timing remain consistent |
| Power demand | Measure steady-state supply current in normal and fully covered conditions | Supply voltage and current for each condition |

## Measuring the 8 Hz behavior

Use an oscilloscope on an appropriate LED-drive node, or a photodetector to observe the optical output. Record the instrument and measurement point. Measure each LED independently; the relationship between the LEDs should be observed rather than assumed.

1. Capture several complete cycles after the behavior has settled.
2. Measure the time from one rising edge to a later rising edge spanning `N` complete cycles.
3. Calculate `f = N / elapsed_seconds` and `T = elapsed_seconds / N`.
4. Compare the result with the reported **8 Hz / 125 ms** behavior.
5. Record high time and calculate `duty_cycle_percent = 100 × high_time / period`.

For example, **10 cycles over 1.25 seconds corresponds to 8 Hz**. This is a calculation example, not a test result. No acceptable frequency tolerance has been specified yet.

## Measurement log

Use [measurements.csv](measurements.csv) to record results. It currently contains column headings only. Leave unavailable measurements blank and describe the LED pattern and setup in the notes field.

Add waveform screenshots or a demonstration video alongside the log, then summarize the observed behavior, discrepancies, and any revisions in the project README.
