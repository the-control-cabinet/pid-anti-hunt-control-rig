# 03 Tuning method

[← Back to README](../README.md)

1. **Open-loop step test** on each loop: record the response to an output step.
2. **Fit first-order-plus-dead-time:** gain K, time constant τ, dead time θ. Expect a τ of seconds for flow and minutes for thermal.
3. **Initial PI** from a rule (e.g. SIMC: Kc = τ / (K × (τc + θ)), Ti = min(τ, 4(τc + θ))).
4. **Compare with ESPHome's PID autotune** on each loop.
5. **Detune for robustness**, then verify with setpoint and disturbance steps (the valve for flow, the fan or lid for thermal).
6. **Carry forward:** the thermal-loop method is the one used for the [OpenTherm boiler loop](https://github.com/the-control-cabinet/opentherm-boiler-control-esphome).
