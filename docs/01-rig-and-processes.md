# 01 Rig and processes

[← Back to README](../README.md)

## Rig (existing)
DIN-rail enclosure: row 1 has a 24 V DC PSU (HDR-60-24), MCB and the Trend IQ411; row 2 has an ESP32-S3, opto-isolated 24 V relays and a 2N7000 buffer stage, shared with [duty/standby and interlocks](https://github.com/the-control-cabinet/din-rail-rig-duty-standby-interlocks).

## Loop 1: flow rate (primary)
| Item | Choice | Notes |
|---|---|---|
| Pump | Existing **brushless 24 V submersible pump** | Same pumps as #7 |
| Actuator | **Logic-level MOSFET** (PWM from the ESP32) ⟨to buy if needed⟩ | Check the pump tolerates PWM speed control; if not, a pump with a speed input |
| Flow sensor | Hall-effect pulse flow sensor sized for the pump's range ⟨to buy⟩ | Pulse counter on the ESP32 |
| Hydraulics | Tank → pump → flow sensor → **a manual valve (the disturbance)** → back to the tank | Closing the valve partly is the load change |
| Character | Fast, noisy (pulse quantisation), little dead time | Filtering and derivative matter here |

## Loop 2: temperature (secondary)
| Item | Choice | Notes |
|---|---|---|
| Heater | **24 V** power resistor (e.g. 33 Ω, 50 W aluminium-clad, so about 17 W at 24 V) ⟨to buy⟩ | Within the HDR-60-24's 60 W alongside the pumps ⟨check the total load⟩ |
| Enclosure | Small insulated box | Sets the time constant (aim for minutes) |
| Sensor | DS18B20 (already in stock) | Moving it changes the dead time: itself an experiment |
| Actuators | Relay (time-proportioned) **and** MOSFET PWM | Compare both |
| Disturbance | A small 24 V fan, or opening the lid | |

## Safety
- 24 V DC only on both processes; a fuse per load.
- Heater: firmware over-temperature cut-out (70 °C) **and** a thermal fuse on the resistor.
- Pump: never runs dry (a low-level permissive shared with #9).
