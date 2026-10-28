# 03 · Tuning Method

[← Back to README](../README.md)

1. **Open-loop step test:** fixed output (e.g. 0 → 50 %); record the temperature until steady.
2. **Fit a first-order-plus-dead-time model:** process gain K (°C per %), time constant τ, dead time θ.
3. **Initial PI parameters** from a rule (e.g. SIMC: Kc = τ / (K × (τc + θ)), Ti = min(τ, 4(τc + θ)), with τc ≈ θ for a moderate response).
4. **Compare with ESPHome's PID autotune** (relay-based): agree or explain the difference.
5. **Detune for robustness:** buildings and boilers punish aggressive loops.
6. **Closed-loop verification:** setpoint step and disturbance (fan/lid); check overshoot, settling, output activity.
7. **Record** the model and parameters; the same procedure is reused for the [OpenTherm boiler loop](https://github.com/the-control-cabinet/opentherm-boiler-control-esphome).
