# Two-Stage CMOS Operational Amplifier | 180 nm

A transistor-level implementation and LTspice simulation of a two-stage CMOS operational amplifier designed using a 180 nm CMOS technology.

## Project Overview

This project focuses on designing a CMOS op-amp while considering important analog performance parameters such as gain, bandwidth, stability, slew rate, input common-mode range, and power consumption.

The design process starts with the required specifications and proceeds through analytical calculations, MOSFET sizing, circuit implementation, and simulation-based validation.

---

## Target Specifications

| Parameter | Target |
|-----------|--------|
| CMOS Technology | 180 nm |
| Supply Voltage | 1.8 V |
| Open-Loop Gain | 60 dB |
| Gain Bandwidth | 30 MHz |
| Phase Margin | ≥ 60° |
| Slew Rate | 40 V/μs |
| Load Capacitor | 2 pF |
| Maximum Power | 300 μW |
| Input Common-Mode Range | 0.8 V – 1.6 V |

---

## Circuit Configuration

The op-amp is based on a two-stage CMOS topology. Its main sections are:

- NMOS differential input stage
- PMOS active-load current mirror
- Tail-current bias circuit
- Second-stage common-source amplifier
- Output load transistor
- Miller compensation capacitor

The first stage converts the differential input into a single-ended signal and provides the initial gain. The second stage further amplifies this signal and drives the output.

---

## Design Flow

The circuit was developed through the following sequence:

1. Establish the required op-amp specifications.
2. Choose an appropriate Miller compensation capacitor.
3. Estimate the bias current using the slew-rate requirement.
4. Obtain the required input-stage transconductance.
5. Select suitable MOSFET overdrive voltages.
6. Determine the required transistor W/L values.
7. Size the current mirrors according to the required current ratios.
8. Design and size the second gain stage.
9. Implement the complete circuit in LTspice.
10. Check the simulated gain and bandwidth.
11. Evaluate phase margin and frequency stability.
12. Check the input common-mode range.
13. Measure the total power consumption.
14. Perform AC and transient simulations for final verification.

---

## MOSFET Dimensions

The final device dimensions used in the LTspice schematic are listed below:

| Transistor | L | W | W/L |
|------------|---|---|-----|
| M1, M2 | 500 nm | 3 μm | 6 |
| M3, M4 | 500 nm | 7 μm | 14 |
| M5, M8 | 1 μm | 12 μm | 12 |
| M6 | 500 nm | 87 μm | 174 |
| M7 | 1 μm | 75 μm | 75 |

## Schematic

<img width="1910" height="877" alt="image" src="https://github.com/user-attachments/assets/4529c4ae-dcc4-434e-9bd0-a17d27cae1c3" />

## AC Analysis

### Input common Mode Range=1.6V
Phase Margin=59.31°
GBW=30.23 MHz
DC Gain=61.25 dB

<img width="1919" height="849" alt="image" src="https://github.com/user-attachments/assets/22ee022e-a359-4fee-9e35-a155c5294a0f" />

### Input common Mode Range=0.8V
Phase Margin=58.23°
GBW=30.24 MHz
DC Gain=72.1 dB

<img width="1919" height="844" alt="image" src="https://github.com/user-attachments/assets/887180e4-defe-42da-908f-a74e432d8d85" />


## Slew Rate

### Rising Edge

ΔV=999.21439mV=0.99921439V,Δt=28.586898ns...
SR=34.95 V/µsec
<img width="1919" height="849" alt="image" src="https://github.com/user-attachments/assets/9b4524cd-9cc2-445e-8158-64decc6eb749" />

### ICMR Verification
Calculated:0.8 to 1.6V
<img width="1918" height="881" alt="image" src="https://github.com/user-attachments/assets/065aab44-ea8b-42d2-a842-4742e0c25164" />
From the image,saturation current(≈20 uA) between 0.8 to 1.6V
Schematic:
<img width="1912" height="842" alt="image" src="https://github.com/user-attachments/assets/2cb619c9-f228-4a25-9996-f0f757a30be9" />


