# 01 · Rig and Process

[← Back to README](../README.md) · Config: [config/esp32-pid-rig.yaml](../config/esp32-pid-rig.yaml)

## Rig (existing)
DIN-rail enclosure with PSU, MCB, an ESP32 and a 4-channel relay module (shared with #7 duty/standby and #9 interlocks). The relay slot is reused here.

## Process (to build)
| Item | Choice | Notes |
|---|---|---|
| Heater | 12 V power resistor (e.g. 10 Ω, 25 W aluminium-clad, so about 14 W at 12 V) ⟨to buy⟩ | Safe extra-low voltage; mounted on a small heat-spreader |
| Enclosure | Small insulated box (e.g. a food container with foam lining) | Sets the time constant: aim for minutes, not seconds |
| Sensor | DS18B20 (or a 10k NTC) on the heat-spreader or in the air | Moving the sensor changes the dead time: itself an experiment |
| Actuator A | **Relay**, time-proportioned (cycle time adjustable) | How BMS often drives on/off plant |
| Actuator B | **Logic-level MOSFET module**, PWM | True modulation |
| Disturbance | A small 12 V fan, or opening the lid | For disturbance-rejection tests |

## Safety
- 12 V only on the process side; a fuse in the heater feed (e.g. 2 A).
- **Hard over-temperature cut-out** in firmware (e.g. 70 °C) **and** a thermal fuse on the resistor.
- The heater never powered without the sensor reading valid.
