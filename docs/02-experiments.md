# 02 · Experiments

[← Back to README](../README.md) · Log: [data/experiment-log.csv](../data/experiment-log.csv)

| # | Experiment | Hypothesis | Record |
|---|---|---|---|
| 1 | **On/off with differential** (hysteresis 0.5, 1, 2 °C) | Wider differential: fewer switches, bigger swings | Swing amplitude, switches/hour |
| 2 | **Proportional only** (proportional band 2, 5, 10 °C) | P-only settles with an **offset**; a narrower band gives less offset but hunts | Offset, overshoot, oscillation |
| 3 | **PI** | Integral removes the offset; too much causes slow oscillation | Settling time, overshoot |
| 4 | **Windup** (setpoint unreachable, then reduced) | Integral winds up, then overshoots badly when it becomes reachable | Overshoot size and duration |
| 5 | **Anti-windup** (clamping; back-calculation) | Overshoot from experiment 4 largely removed | Same metrics vs 4 |
| 6 | **Derivative** (with filtering) | Damps overshoot; amplifies sensor noise if unfiltered | Noise on the output |
| 7 | **Time-proportioning cycle time** (relay: 30 s, 2 min, 5 min) | Long cycles cause ripple; short cycles wear the relay | Ripple, switches/hour |
| 8 | **Hunting clinic** | Hunting can be **caused** by: excessive gain, a long sensor lag (sensor moved away), a deadband too small for the noise. Each is cured by the matching fix | Before/after trends for each cause |

Each experiment gets a **hypothesis → trend screenshot → conclusion** entry in doc 04.
