# Two-Stage CMOS Operational Amplifier (180 nm CMOS)

Design and simulation of a two-stage CMOS operational amplifier implemented in a 180 nm CMOS process using LTspice.

## Overview

This repository contains the complete design, analysis, and simulation of a two-stage CMOS operational amplifier implemented using a 180 nm CMOS process.

The project demonstrates the complete analog IC design flow, from hand calculations and transistor sizing to simulation and verification.

---
## Design Specifications

| Parameter | Value |
|-----------|-------|
| Technology | 180 nm CMOS |
| Supply Voltage | 1.8 V |
| DC Gain | 60 dB |
| GBW | 30 MHz |
| Phase Margin | ≥60° |
| Slew Rate | 40 V/μs |
| Load Capacitance | 2 pF |
| Power | ≤300 μW |
| ICMR | 0.8 V – 1.6 V |

---

## Architecture

The proposed operational amplifier employs a classical two-stage architecture consisting of:

- Differential input pair
- PMOS current mirror active load
- Common-source second gain stage
- Miller compensation capacitor
- Bias current mirror

## Design Methodology

The amplifier was designed using the following procedure.

1. Define design specifications.
2. Select Miller compensation capacitor.
3. Calculate bias current from slew rate.
4. Calculate transconductance (gm).
5. Determine overdrive voltages.
6. Calculate transistor aspect ratios (W/L).
7. Design current mirrors.
8. Design second gain stage.
9. Verify gain and GBW.
10. Optimize phase margin.
11. Verify ICMR.
12. Verify power dissipation.
13. Perform AC, DC, and transient simulations.

## Final Transistor Dimensions

| MOSFET | L | W | W/L |
|--------|----|----|-----|
| M1, M2 | 500 nm | 3 μm | 6 |
| M3, M4 | 500 nm | 7 μm | 14 |
| M5, M8 | 1 μm | 12 μm | 12 |
| M6 | 500 nm | 87 μm | 174 |
| M7 | 1 μm | 75 μm | 75 |

## Circuit Schematic

<img width="1910" height="877" alt="image" src="https://github.com/user-attachments/assets/4529c4ae-dcc4-434e-9bd0-a17d27cae1c3" />
