\# 14-Channel QTR Sensor Array PCB

Custom 14-channel infrared sensor array PCB designed in KiCad for high-speed line follower robots and embedded robotics applications.



\---



\## Preview



\### PCB Layout

!\[PCB Layout](pcb\_editor\_view.png)



\### 3D View

!\[PCB 3D](3d\_view.png)



\---



\## Features



\- 14x TCRT5000 IR sensors

\- Custom U-shaped curved PCB design for wide-angle coverage

\- Compact sensor placement for precise line detection

\- Angled wing sensors for improved curve and intersection detection

\- Mounting holes for robot chassis integration

\- Dedicated resistor network per channel (200Ω LED series + 10kΩ pull-down)

\- 16-pin single-row header output (GND, Vin, Sensor 1–14)

\- Analog output per channel — compatible with any ADC-equipped MCU

\- Onboard decoupling capacitor for power stability

\- Designed using KiCad 9.0

\- Gerber files included for fabrication



\---



\## Hardware Specifications



| Parameter | Value |

|---|---|

| Sensor Type | TCRT5000 |

| Sensor Count | 14 |

| LED Series Resistor | 200 Ω (per channel) |

| Pull-down Resistor | 10 kΩ (per channel) |

| Decoupling Capacitor | 100 nF |

| Supply Voltage | 5V |

| Output Type | Analog (per channel) |

| Header | 16-pin 2.54mm single-row |

| PCB Software | KiCad 9.0 |

| Board Type | Custom 2-Layer PCB |

| Application | Line Follower Robotics |



\---



\## Bill of Materials



| Ref | Component | Value | Qty |

|---|---|---|---|

| U1–U14 | IR Reflectance Sensor | TCRT5000 | 14 |

| R1, R3, R5 ... R27 (odd) | LED Series Resistor | 200 Ω (0805 SMD) | 14 |

| R2, R4, R6 ... R28 (even) | Pull-down Resistor | 10 kΩ (0805 SMD) | 14 |

| C1 | Decoupling Capacitor | 100 nF (0805 SMD) | 1 |

| J1 | Pin Header | 2.54mm 16-pin | 1 |

| — | Power Header (GND) | Screw terminal / header | 1 |

| — | Power Header (Vin) | Screw terminal / header | 1 |



\---



\## Pinout



| Pin | Signal | Description |

|---|---|---|

| 1 | GND | Ground |

| 2 | Vin | 5V Supply |

| 3–16 | CH1–CH14 | Sensor analog outputs (left to right) |



\---



\## Project Structure



```text

.

├── Gerber new/

├── 14QRT\_Custom\_IR\_Sensor\_Improved.kicad\_pcb

├── 14QRT\_Custom\_IR\_Sensor\_Improved.kicad\_pro

├── 14QRT\_Custom\_IR\_Sensor\_Improved.kicad\_prl

├── fp-info-cache

├── 3d\_view.png

├── pcb\_editor\_view.png

└── README.md

```



\---



\## Circuit Description



Each of the 14 channels follows the same schematic:



```

5V ──\[200Ω]──► TCRT5000 IR LED (Anode → Cathode → GND)



Phototransistor:

&#x20; Collector → 5V

&#x20; Emitter → \[10kΩ] → GND

&#x20;         └──────────► Analog Output (Header Pin)

```



\- \*\*White / reflective surface\*\* → phototransistor conducts → output \*\*LOW\*\*

\- \*\*Black / non-reflective surface\*\* → phototransistor cuts off → output \*\*HIGH\*\*



\---



\## Current Status



\- ✅ PCB routing completed

\- ✅ Gerber files generated

\- ✅ Design uploaded as open-source project

\- 🔄 Future improvements planned (see below)



\---



\## Future Improvements



\### Hardware

\- Add comparator ICs (e.g. LM393) for digital output per channel, reducing ADC pin usage

\- Add onboard op-amp with adjustable threshold potentiometer for easy sensitivity tuning

\- Add I2C ADC (e.g. ADS1115) for MCUs with limited ADC pins

\- Add LED status indicators per channel for visual debugging

\- Increase bulk decoupling capacitance (10–47 µF) near Vin for noise immunity

\- Add reverse polarity protection on Vin



\### PCB Layout

\- Cleaner routing paths and power trace optimization

\- Improved silkscreen labeling (sensor numbers visible from bottom)

\- Expose test points per channel for easier debugging

\- Experiment with sensor wing angles for better curve detection



\### Firmware

\- Weighted centroid algorithm for smooth line position estimate

\- Auto-calibration routine (sweep over line, record min/max per sensor)

\- PID controller integration example for Arduino / STM32



\---



\## Applications



\- Line follower robots

\- Embedded robotics systems

\- PID-based navigation robots

\- Autonomous path tracking systems



\---



\*Designed with KiCad 9.0 — Open Source Hardware\*

