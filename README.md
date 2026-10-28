# PID Control with Anti-Hunt on a DIN-Rail Training Rig (Design Stage)

**Learning loop tuning where mistakes are cheap: a small, safe thermal process on a DIN-rail BMS training rig, controlled by an ESP32 running ESPHome. It works through the control behaviours a BMS engineer has to recognise and fix (on/off differential, proportional band and offset, integral action, windup, hunting, time-proportioning) with step-test tuning and logged results, before the same methods are applied to a real boiler.**

[![YouTube](https://img.shields.io/badge/YouTube-The%20Control%20Cabinet-red?logo=youtube)](https://www.youtube.com/channel/UC5Cupmz7vlfcodpCX7k8iuQ)
[![Portfolio](https://img.shields.io/badge/Portfolio-the--control--cabinet-24292f?logo=github)](https://github.com/the-control-cabinet)
![Domain](https://img.shields.io/badge/BMS-PID%20tuning-blue)
![Status](https://img.shields.io/badge/Status-Design%20stage-yellow)

> **The short version:**
> - **The process:** a low-voltage heater in a small insulated box, measured by a temperature sensor. It's slow enough to behave like a room or a heat exchanger, and fast enough to test in an evening.
> - **Two actuators:** a **relay with time-proportioning** (how much BMS plant is actually driven) and a **MOSFET PWM** output (true modulation).
> - **Eight experiments** from on/off to tuned PI with anti-windup, each with a hypothesis, a logged trend and a conclusion.
> - **Why first:** this is step **D** in the delivery sequence (in parallel with A-C), so tuning skills are proven on the rig before the [OpenTherm boiler control](https://github.com/the-control-cabinet/opentherm-boiler-control-esphome) (step E).

**Portfolio position:** Automation level · control loops (portfolio #8). Rig companions: duty/standby pump rotation (#7), state machine and interlocks (#9), Trend IQ411 (#12).

---

## Documents
| Doc | Contents |
|---|---|
| [01 Rig and process](docs/01-rig-and-process.md) | Hardware, wiring, safety, process characteristics |
| [02 Experiments](docs/02-experiments.md) | The eight experiments, hypotheses and what to record |
| [03 Tuning method](docs/03-tuning-method.md) | Step test, model fit, tuning rules, detuning |
| [04 Results and lessons](docs/04-results.md) | Template: trends, parameters, conclusions |

## Roadmap
- [ ] Source the heater, MOSFET module and sensor; wire into the rig
- [ ] Experiments 1-8 with logged trends
- [ ] Transfer the method to the OpenTherm stage (doc 08 of that repo)
- [ ] Re-implement the tuned loop on the Trend IQ411 (#12) and in a PLC (#13)

## Skills demonstrated (as built)
| Skill | Evidence |
|---|---|
| Control fundamentals | On/off differential, proportional band, offset, integral, derivative |
| Hunting diagnosis | Causes demonstrated and cured (gain, cycle time, deadband) |
| Anti-windup | Saturation demo, then clamping and back-calculation |
| Tuning | Step test → first-order-plus-dead-time model → tuning rule → detune |
| Documentation | Hypothesis, trend, conclusion per experiment |

📺 [The Control Cabinet on YouTube](https://www.youtube.com/channel/UC5Cupmz7vlfcodpCX7k8iuQ)

*Built and documented by James · part of [The Control Cabinet BMS portfolio](https://github.com/the-control-cabinet). MIT Licence.*
