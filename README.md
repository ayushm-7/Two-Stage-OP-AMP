# Two-Stage CMOS Operational Amplifier | 180 nm

A transistor-level design and LTspice simulation of a two-stage CMOS operational amplifier using a 180 nm CMOS technology.

## Project Overview

This project focuses on the design and simulation of a two-stage CMOS operational amplifier while analyzing important analog performance parameters such as open-loop gain, gain-bandwidth product, phase margin, slew rate, input common-mode range, and output swing.

The design flow begins with the required specifications and proceeds through analytical calculations, MOSFET sizing, circuit implementation, compensation, and simulation-based verification.

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
| Load Capacitance | 2 pF |
| Maximum Power | 300 μW |
| Input Common-Mode Range | 0.8 V – 1.6 V |

---

## Circuit Configuration

The amplifier is based on a conventional two-stage CMOS topology consisting of:

- NMOS differential input pair
- PMOS active-load current mirror
- Tail-current bias circuit
- Common-source second gain stage
- Output load transistor
- Miller compensation capacitor

The first stage converts the differential input voltage into a single-ended signal while providing the initial voltage gain. The second stage provides additional voltage amplification and drives the output node. Miller compensation is used to improve frequency stability.

---

## Design Flow

The circuit was developed using the following sequence:

1. Define the required performance specifications.
2. Select the Miller compensation capacitor.
3. Determine the required bias current from the slew-rate target.
4. Calculate the required input-stage transconductance.
5. Select suitable MOSFET overdrive voltages.
6. Determine the transistor aspect ratios.
7. Design the current mirrors and bias network.
8. Size the second gain stage.
9. Implement the complete circuit in LTspice.
10. Analyze the AC response.
11. Verify gain, GBW, and phase margin.
12. Evaluate the input common-mode range.
13. Measure the transient slew rate.
14. Evaluate the output voltage swing.

---

## MOSFET Dimensions

The final transistor dimensions used in the LTspice implementation are:

| Transistor | L | W | W/L |
|------------|---|---|-----|
| M1, M2 | 500 nm | 3 μm | 6 |
| M3, M4 | 500 nm | 7 μm | 14 |
| M5, M8 | 1 μm | 12 μm | 12 |
| M6 | 500 nm | 87 μm | 174 |
| M7 | 1 μm | 75 μm | 75 |

---

## Schematic

<img width="1910" height="877" alt="Two-Stage CMOS Op-Amp Schematic" src="https://github.com/user-attachments/assets/4529c4ae-dcc4-434e-9bd0-a17d27cae1c3" />

---

## AC Analysis

The open-loop frequency response was analyzed at two different common-mode input voltages to evaluate the gain and stability of the amplifier across the specified input range.

### Common-Mode Input = 1.6 V

The simulated results are:

- **DC Gain:** 61.25 dB
- **GBW:** 30.23 MHz
- **Phase Margin:** 59.31°

The measured gain is above the 60 dB target, while the GBW is very close to the specified 30 MHz value.

<img width="1919" height="849" alt="AC Response at 1.6 V Common-Mode Input" src="https://github.com/user-attachments/assets/22ee022e-a359-4fee-9e35-a155c5294a0f" />

### Common-Mode Input = 0.8 V

At the lower end of the specified common-mode range, the simulated results are:

- **DC Gain:** 72.1 dB
- **GBW:** 30.24 MHz
- **Phase Margin:** 58.23°

The gain changes with the common-mode input voltage, while the GBW remains approximately 30 MHz.

<img width="1919" height="844" alt="AC Response at 0.8 V Common-Mode Input" src="https://github.com/user-attachments/assets/887180e4-defe-42da-908f-a74e432d8d85" />

---

## Slew Rate Analysis

The slew rate was calculated from the transient response by measuring the output voltage change and the corresponding time interval.

### Rising Edge

From the measured waveform:

**ΔV = 999.21439 mV = 0.99921439 V**

**Δt = 28.586898 ns**

The slew rate is calculated as:

**SR = ΔV / Δt**

Therefore:

**SR ≈ 34.95 V/μs**

Hence, the measured rising-edge slew rate is approximately **34.95 V/μs**.

The measured value is below the original target of 40 V/μs, indicating that the available charging current of the compensation capacitor limits the large-signal response.

<img width="1919" height="849" alt="Rising Edge Slew Rate" src="https://github.com/user-attachments/assets/9b4524cd-9cc2-445e-8158-64decc6eb749" />

---

## ICMR Verification

The input common-mode range was evaluated by varying the common-mode input voltage and observing the operating current of the input stage.

The specified common-mode range is:

**0.8 V ≤ VCM ≤ 1.6 V**

The simulation shows approximately **20 μA** of saturation current over the 0.8 V to 1.6 V range, indicating that the input stage maintains its intended operating condition across this range.

<img width="1918" height="881" alt="ICMR Verification" src="https://github.com/user-attachments/assets/065aab44-ea8b-42d2-a842-4742e0c25164" />

### ICMR Test Circuit

<img width="1912" height="842" alt="ICMR Test Circuit" src="https://github.com/user-attachments/assets/2cb619c9-f228-4a25-9996-f0f757a30be9" />

---

## Output Swing Analysis

The output swing was evaluated using the op-amp in a **unity-gain voltage follower configuration**. The inverting input was connected to the output, while the non-inverting input was swept from 0 V to 1.8 V.

The output voltage was monitored to determine the minimum and maximum output levels over which the amplifier could follow the input.

From the simulation:

- **Minimum output voltage:** ≈ 0.03 V
- **Maximum output voltage:** ≈ 1.70 V

Therefore, the output voltage range is:

**VOUT,range ≈ 0.03 V to 1.70 V**

The measured output swing is:

**ΔVOUT = 1.70 − 0.03**

**ΔVOUT ≈ 1.67 V**

Thus, the amplifier achieves an output swing of approximately **1.67 V** with a 1.8 V supply.

<img width="1918" height="852" alt="image" src="https://github.com/user-attachments/assets/72176451-64a9-447e-907b-f96ffa447cba" />

## Power Dissipation

```markdown
## Power Dissipation Analysis

The power consumption of the op-amp was evaluated from the current drawn from the 1.8 V supply.

The DC power consumption is calculated using:

**P = VDD × IDD**

where VDD = 1.8 V and IDD is the magnitude of the supply current measured from `I(VDD1)` in LTspice.

### At Common-Mode Input = 1.6 V

The simulated supply current is:

**IDD = 172.687 μA**

Therefore:

**P = 1.8 × 172.687 μA**

**P ≈ 310.84 μW**

<img width="447" height="23" alt="image" src="https://github.com/user-attachments/assets/9758889f-0a8a-4712-a73c-2f0e68b4cc84" />


### At Common-Mode Input = 0.8 V

The simulated supply current is:

**IDD = 165.806 μA**

Therefore:

**P = 1.8 × 165.806 μA**

**P ≈ 298.45 μW**

<img width="454" height="41" alt="image" src="https://github.com/user-attachments/assets/d3585549-c3f3-40fc-b465-d6ef6f531fe9" />

### Power Summary

| Common-Mode Input | Supply Current | Power |
|-------------------|----------------|-------|
| 1.6 V | 172.687 μA | 310.84 μW |
| 0.8 V | 165.806 μA | 298.45 μW |

The power consumption is approximately **298.45–310.84 μW** over the two tested common-mode conditions. The circuit is very close to the specified **300 μW** power target, with the 0.8 V condition remaining below the limit.
```
