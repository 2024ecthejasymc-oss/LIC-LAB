# Design and Analysis of a Common Source Amplifier with PMOS Active Load

This project demonstrates the complete hand design and simulation verification of a **Common Source (CS) amplifier** implemented in **180nm CMOS technology**. The circuit consists of:

- An NMOS amplifying transistor  
- A PMOS active load  
- A source degeneration resistor for stability and linearity  

The design is validated using DC, AC, and Transient analysis.

---

# 1. Design Requirements

## Given Specifications

- **Technology Node:** 180 nm CMOS  
- **Supply Voltage (VDD):** 1.8 V  
- **Maximum Power Dissipation:** 1 mW  
- **Load Capacitance (CL):** 10 pF  
- **Channel Length (L):** 180 nm
  ![WhatsApp Image 2026-03-04 at 12 48 52](https://github.com/user-attachments/assets/7095d99e-ddd1-46ff-af49-8525b135d9a4)


---

## Current Selection

From power constraint:

\[
I_D \leq \frac{P}{V_{DD}} = \frac{1mW}{1.8V} \approx 555\mu A
\]

To maintain design margin:

\[
I_D = 200\mu A
\]

---

# 2. Assumptions Used for Hand Calculations

- Overdrive Voltage:  
  \[
  V_{OV} = 0.25V
  \]

- Threshold Voltages:  
  \[
  V_{thn} = 0.36V
  \]
  \[
  V_{thp} = -0.39V
  \]

- Source Degeneration Voltage:  
  \[
  V_{RS} = 0.2V
  \]

---

# 3. NMOS Driver Design

## 3.1 Gate-Source Voltage

\[
V_{GS1} = V_{thn} + V_{OV}
\]

\[
V_{GS1} = 0.36 + 0.25 = 0.61V
\]

---

## 3.2 Source Resistor Calculation

\[
R_S = \frac{V_{RS}}{I_D}
\]

\[
R_S = \frac{0.2}{200\mu A}
\]

\[
R_S = 1k\Omega
\]

---

## 3.3 Gate Bias Voltage

\[
V_{G1} = V_{GS1} + V_{RS}
\]

\[
V_{G1} = 0.61 + 0.2
\]

\[
V_{G1} = 0.81V
\]

---

## 3.4 Output Bias Voltage

To allow maximum signal swing:

\[
V_{out} \approx 1.1V
\]

---

## 3.5 Saturation Check

\[
V_{DS1} \geq V_{OV}
\]

\[
V_{DS1} \geq 0.25V
\]

This condition is satisfied in simulation.

---

# 4. PMOS Active Load Design

## 4.1 Required Source-Gate Voltage

\[
V_{SG2} = |V_{thp}| + V_{OV}
\]

\[
V_{SG2} = 0.39 + 0.25
\]

\[
V_{SG2} = 0.64V
\]

---

## 4.2 PMOS Gate Bias

\[
V_{G2} = V_{DD} - V_{SG2}
\]

\[
V_{G2} = 1.8 - 0.64
\]

\[
V_{G2} = 1.16V
\]
![WhatsApp Image 2026-03-04 at 12 48 52 (1)](https://github.com/user-attachments/assets/42a72794-e18c-4545-b3cd-a74659b4075b)


---

# 5. Small Signal Analysis

## 5.1 Transconductance

\[
g_m = \frac{2I_D}{V_{OV}}
\]

\[
g_m = \frac{2 \times 200\mu A}{0.25}
\]

\[
g_m = 1.6mS
\]

---

## 5.2 Voltage Gain Calculation

Approximate gain expression:

\[
A_v = \frac{-g_m r_{out}}{1 + g_m R_S}
\]

Assuming:

\[
r_{out} = 25k\Omega
\]

---

### Open Loop Gain

\[
g_m r_{out} = 1.6mS \times 25k\Omega
\]

\[
= 40
\]

---

### Degeneration Factor

\[
1 + g_m R_S = 1 + (1.6mS \times 1000)
\]

\[
= 2.6
\]

---

### Final Gain (Voltage Ratio)

\[
A_v = \frac{40}{2.6}
\]

\[
A_v = 15.38
\]

---

### Gain in dB

\[
A_v(dB) = 20\log_{10}(15.38)
\]

\[
A_v(dB) = 23.74dB
\]

---

# 6. Simulation Results (LTspice)
Transient Analysis

Transient simulation shows an inverted output sine wave, consistent with the 180° phase shift of a Common Source stage The simulated gain is derived from the AC analysis output

magnitudes:

Output Voltage Magnitude (Vout): 246.399

Input Voltage Magnitude (Vin): 19.99

Simulated Voltage Ratio: Av(sim) = 249.999 ≈ 12.326

Simulated Gain (dB): 20log10 (12.326) = 21.82, dB

3dB Frequency: The bandwidth cutoff frequency is 275.829 MHz.
![WhatsApp Image 2026-03-04 at 12 48 53](https://github.com/user-attachments/assets/e5b6454e-d7b6-4862-8138-7e2a71468776)
![WhatsApp Image 2026-03-04 at 12 48 53 (1)](https://github.com/user-attachments/assets/54bf9860-541a-44a3-a6c1-0ceccabec9bd)
![WhatsApp Image 2026-03-04 at 12 48 53 (2)](https://github.com/user-attachments/assets/1675e6c8-0095-4711-8f54-322922d298f1)

## 6.1 DC Operating Point

- Vin = 0.81V  
- Vout = 1.118V  
- ID = 199.8µA  

The simulated current closely matches theoretical calculations.
![WhatsApp Image 2026-03-04 at 12 48 54](https://github.com/user-attachments/assets/4093aa46-93e8-4e6d-bd07-9e04837028d5)


---

## 6.2 AC Analysis

Measured from AC plot:

- Vout = 246.399  
- Vin = 19.99  

\[
A_v = \frac{246.399}{19.99}
\]

\[
A_v = 12.33
\]

\[
A_v(dB) = 20\log_{10}(12.33)
\]

\[
A_v(dB) = 21.82dB
\]

---

## 6.3 Bandwidth

- 3dB Frequency:
  \[
  f_{3dB} = 275.829MHz
  \]
  ![WhatsApp Image 2026-03-04 at 12 48 54 (1)](https://github.com/user-attachments/assets/b1df8202-408b-4e10-8e3f-1cc3aeb5e211)


---

# 7. Theoretical vs Simulated Comparison

| Parameter | Theoretical | Simulated | Difference |
|------------|------------|------------|------------|
| Gain (dB) | 23.74 dB | 21.82 dB | 1.92 dB |
| Gain (V/V) | 15.38 | 12.33 | 3.05 |
| Drain Current | 200 µA | 199.8 µA | 0.2 µA |

---

# 8. Reason for Gain Difference

## Body Effect

Since the source is elevated at 0.2V:

- Threshold voltage increases  
- Body transconductance (gmb) appears  
- Effective gain reduces  

Modified gain equation:

\[
A_v = \frac{-g_m r_{out}}{1 + (g_m + g_{mb})R_S}
\]

---

## Channel Length Modulation

The real 180nm model uses a bias-dependent output resistance, slightly reducing:

\[
r_o
\]

This lowers gain compared to ideal hand calculations.

---

## Effect of Source Degeneration

Without Rs:

\[
A_v = -g_m r_{out}
\]

\[
= -40 \approx 32dB
\]

With Rs:

- Gain reduces  
- Linearity improves  
- Bias stability improves  
- Process sensitivity reduces  

---

# 9. Conclusion

The amplifier:

- Meets the power constraint (<1mW)  
- Achieves gain >20 dB  
- Provides bandwidth ≈275 MHz  
- Maintains correct bias conditions  

The small difference between theory and simulation is due to second-order MOS effects included in the 180nm device model.

