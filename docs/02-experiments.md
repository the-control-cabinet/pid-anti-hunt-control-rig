# 02 Experiments

[← Back to README](../README.md)

| # | Experiment | Expected on the **flow** loop | Expected on the **thermal** loop |
|---|---|---|---|
| 1 | **On/off with differential** | Rapid cycling; a differential is essential | Slow swings; overshoot from the stored heat |
| 2 | **Proportional only** | Offset; a narrow band chatters with sensor noise | Offset; a narrow band oscillates slowly |
| 3 | **PI** | Offset removed quickly | Offset removed slowly; too much integral, slow oscillation |
| 4 | **Windup** (unreachable setpoint, then reduced) | Short overshoot | Large, long overshoot |
| 5 | **Anti-windup** | Small improvement | Large improvement |
| 6 | **Derivative (filtered)** | Amplifies flow-sensor noise: usually leave off | Helps against overshoot |
| 7 | **Time-proportioning cycle time** (relay) | Unsuitable: shows why fast loops need modulation | Works with a long cycle; ripple vs relay wear |
| 8 | **Hunting clinic** | Hunting from excessive gain or noise; cures: lower gain, filtering, deadband | Hunting from sensor lag (sensor moved away); cures: retune, move the sensor |

Each run: hypothesis → trend → conclusion, logged in [data/experiment-log.csv](../data/experiment-log.csv).
