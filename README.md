# PID Control with Anti-Hunt on a DIN-Rail Training Rig: Flow Loop and Thermal Loop (Design Stage)

**Learning loop tuning where mistakes are cheap, on two processes with very different dynamics: a fast hydraulic loop (pump speed controlling flow rate, using the rig's 24 V pumps) and a slow thermal loop (a heater in an insulated box). Both work through the behaviours a BMS engineer must recognise and fix (on/off differential, proportional band and offset, integral action, windup, hunting, time-proportioning) with step-test tuning, before the methods are applied to real plant.**

[![YouTube](https://img.shields.io/badge/YouTube-The%20Control%20Cabinet-red?logo=youtube)](https://www.youtube.com/channel/UC5Cupmz7vlfcodpCX7k8iuQ)
[![Portfolio](https://img.shields.io/badge/Portfolio-the--control--cabinet-24292f?logo=github)](https://github.com/the-control-cabinet/the-control-cabinet)
![Domain](https://img.shields.io/badge/BMS-PID%20tuning-blue)
![Status](https://img.shields.io/badge/Status-Design%20stage-yellow)

> **The short version:**
> - **Loop 1: flow rate (primary).** A 24 V brushless pump's speed is driven by MOSFET PWM; a flow sensor is the process variable. Fast (seconds), noisy, with little dead time, like a pump or damper loop.
> - **Loop 2: temperature (secondary).** A 24 V heater in an insulated box, with a temperature sensor. Slow (minutes) with real dead time, like a room or heat exchanger.
> - **Two actuators:** relay **time-proportioning** (how BMS often drives on/off plant) and **PWM** (true modulation).
> - **Eight experiments** run on both loops: the same rules give very different behaviour, which is the core lesson of loop tuning.
> - **Scope note:** the house boiler only allows flow-*temperature* modulation (OpenTherm), not flow-*rate* control, so flow-rate PID is proven here on the rig instead.

**Portfolio position:** Automation level · control loops (portfolio #8, delivery step D). Rig companions: [duty/standby + interlocks](https://github.com/the-control-cabinet/din-rail-rig-duty-standby-interlocks) (#7/#9, same pumps) · [Trend IQ411](https://github.com/the-control-cabinet/trend-iq411-commissioning) (#12). Method carried to: [OpenTherm boiler control](https://github.com/the-control-cabinet/opentherm-boiler-control-esphome) (step E)

---

## Documents

| Doc | Contents |
|---|---|
| [01 Rig and processes](docs/01-rig-and-processes.md) | Hardware, both processes, safety |
| [02 Experiments](docs/02-experiments.md) | Run on both loops; compare |
| [03 Tuning method](docs/03-tuning-method.md) | Step test, model, rule, detune |
| [04 Results and lessons (template)](docs/04-results.md) | Models, parameters, conclusions |

## Roadmap
- [ ] Source the flow sensor, MOSFET module, heater and fuses; check the PSU load budget
- [ ] Flow loop: step test, then experiments 1-8
- [ ] Thermal loop: step test, then experiments 1-8
- [ ] Compare loops; write up lessons
- [ ] Re-implement both loops on the Trend IQ411 (#12) and in CODESYS (#13)

## Skills demonstrated (as built)
| Skill | Evidence |
|---|---|
| Control fundamentals | Differential, proportional band, offset, integral, derivative |
| Loop dynamics | Fast hydraulic vs slow thermal behaviour compared |
| Hunting diagnosis | Causes demonstrated and cured on both loops |
| Anti-windup | Saturation demo, then clamping |
| Tuning | Step test → FOPDT model → tuning rule → detune |

📺 [The Control Cabinet on YouTube](https://www.youtube.com/channel/UC5Cupmz7vlfcodpCX7k8iuQ)

*Built and documented by James · part of [The Control Cabinet BMS portfolio](https://github.com/the-control-cabinet/the-control-cabinet). MIT Licence.*
