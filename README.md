# Two-Stage CMOS Operational Amplifier

A transistor-level design and simulation of a two-stage CMOS operational amplifier using a 180 nm CMOS technology in LTspice.

The project focuses on transistor sizing, bias-current design, Miller compensation, frequency response, stability, slew-rate, and power verification.

---

## Project Highlights

- 180 nm CMOS technology
- 1.8 V single supply
- Two-stage CMOS op-amp architecture
- PMOS active-load differential input stage
- Common-source second gain stage
- Miller frequency compensation
- Designed for 2 pF load capacitance
- Transistor-level simulation in LTspice
- AC, DC and transient analysis

---

## Design Targets

| Specification | Target |
|---|---:|
| Technology | 180 nm CMOS |
| Supply Voltage | 1.8 V |
| DC Gain | ≥ 60 dB |
| Gain-Bandwidth | 30 MHz |
| Phase Margin | ≥ 60° |
| Slew Rate | 40 V/µs |
| Load Capacitance | 2 pF |
| Power Dissipation | ≤ 300 µW |
| Input Common-Mode Range | 0.8 – 1.6 V |

---

## Circuit Architecture

The amplifier follows the conventional two-stage CMOS operational amplifier topology.

### Main Blocks

1. **Differential Input Stage**
   - Converts the input voltage difference into differential drain currents.
   - Provides the first stage of voltage gain.

2. **PMOS Active Load**
   - Implements current-mirror loading for the differential pair.
   - Converts differential currents into a single-ended output.

3. **Second Gain Stage**
   - Uses a common-source configuration to provide additional voltage gain.
   - Drives the external load through the output node.

4. **Miller Compensation**
   - A compensation capacitor is connected between the first-stage output and the final output.
   - Used to establish dominant-pole compensation and improve closed-loop stability.

5. **Bias Network**
   - Generates the required bias currents for the input and gain stages.

---

## Design Approach

The design was developed by starting from the required performance specifications and then translating them into transistor-level parameters.

The main design sequence was:

```text
Performance Specifications
          ↓
Miller Capacitor Selection
          ↓
Bias Current from Slew-Rate Requirement
          ↓
Required Transconductance
          ↓
Overdrive Voltage Selection
          ↓
MOSFET W/L Calculation
          ↓
Current-Mirror Design
          ↓
Second-Stage Design
          ↓
LTspice Simulation
          ↓
Gain / GBW / PM / SR / Power Verification
          ↓
Transistor Sizing Optimization

---
## Final Transistor Dimensions

| MOSFET | L | W | W/L |
|--------|----|----|-----|
| M1, M2 | 500n | 3u | 6 |
| M3, M4 | 500n | 7u | 14 |
| M5, M8 | 1u | 12u | 12 |
| M6 | 500n | 87u | 174 |
| M7 | 1u | 75u | 75 |

## Circuit Schematic

<img width="1916" height="874" alt="image" src="https://github.com/user-attachments/assets/7fe2feef-21f3-4666-a6ea-8dec50477dd6" />

