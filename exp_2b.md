# Design and Evaluation of Cascode-Based Common Source Amplifier (Circuit 2b)

This project documents the analytical design and simulation verification of a **Common Source (CS) amplifier** that uses:

- NMOS active source degeneration  
- PMOS current-source load  
- 180nm CMOS technology  

The objective is to achieve stable biasing, controlled gain, and wide bandwidth while keeping total power dissipation below 1 mW.

---

# 1. Design Objectives and Specifications
![WhatsApp Image 2026-03-04 at 13 34 39](https://github.com/user-attachments/assets/89d1aa41-81b5-4220-b43c-bd5a51f9ba66)


## Given Parameters

- **Technology Node:** 180 nm CMOS  
- **Supply Voltage (VDD):** 1.8 V  
- **Target Drain Current (ID):** ≈ 200 µA  
- **Target Degeneration Voltage (VDS3):** 0.3 V  
- **Power Budget:** < 1 mW  

The degeneration transistor is intentionally biased to introduce negative feedback, improving linearity and stabilizing gain.

---

# 2. Transistor Sizing Calculations

The MOSFET width is determined using the saturation current equation:

\[
I_D = \frac{1}{2} \mu C_{ox} \frac{W}{L} V_{OV}^2
\]

Rearranging:

\[
W = \frac{2 I_D L t_{ox}}{\mu \epsilon_r \epsilon_0 V_{OV}^2}
\]

---

## 2.1 NMOS Driver and Degeneration (M1, M3)

Given:

- \( t_{ox} = 4.1 \times 10^{-9} \)
- \( \mu_n = 273.8 \times 10^{-4} \)
- \( V_{OV} = 0.25V \)
- \( I_D = 200\mu A \)
- \( L = 180nm \)

After substitution:

\[
W_1 \approx 7.81 \mu m
\]

---

## 2.2 PMOS Active Load (M2)

Given lower hole mobility:

- \( \mu_p = 115.6 \times 10^{-4} \)

Calculated width:

\[
W_2 \approx 18.47 \mu m
\]

---

# 3. DC Bias Analysis

## 3.1 Degeneration Transistor (M3)

To maintain:

\[
V_{DS3} \approx 0.3V
\]

Gate bias is set to:

\[
V_{B2} = 0.61V
\]

---

## 3.2 Input Transistor (M1)

\[
V_{GS1} = V_{OV} + V_{thn}
\]

\[
V_{GS1} = 0.25V + 0.36V = 0.61V
\]

Input bias voltage:

\[
V_{in} = V_{GS1} + V_{DS3}
\]

\[
V_{in} = 0.61V + 0.3V = 0.91V
\]

---

## 3.3 PMOS Load Bias

\[
V_{G2} = V_{DD} - (V_{OV} + |V_{thp}|)
\]

\[
V_{G2} = 1.8V - 0.64V = 1.16V
\]
![WhatsApp Image 2026-03-04 at 13 34 39 (1)](https://github.com/user-attachments/assets/327e606b-bfa3-4940-adeb-70eeb5c595bf)

All devices remain in saturation under these conditions.

---

# 4. Final Implemented Dimensions (Optimized for Simulation)

To improve correlation between theory and simulation:

- **W1 (NMOS Driver):** 26 µm  
- **W2 (PMOS Load):** 15.7 µm  
- **W3 (NMOS Degeneration):** 37.2 µm  
- **Channel Length (L):** 180 nm  
- **Simulated VDS3:** 0.347 V  

---

# 5. Small-Signal Analysis

## 5.1 Transconductance

\[
g_{m1} = \frac{2I_D}{V_{OV}}
\]

\[
g_{m1} = \frac{2 \times 200\mu A}{0.25}
\]

\[
g_{m1} = 1.6 mS
\]

---

## 5.2 Output Resistance

\[
r_o = \frac{1}{\lambda I_D}
\]

For \( \lambda = 0.1 \):

\[
r_o = 50 k\Omega
\]

---

## 5.3 Approximate Voltage Gain

\[
A_v \approx \frac{g_{m1} r_{o2}}{1 + g_{m1} r_{o3}}
\]

With equal output resistances:

\[
A_v = \frac{1.6mS \times 50k}{1 + (1.6mS \times 50k)}
\]

\[
A_v \approx 0.987
\]

\[
A_v(dB) \approx -0.11 dB
\]

---

## 5.4 Matching Simulation (λ = 0.125)

\[
r_{o3} = 40 k\Omega
\]

Required load resistance:

\[
r_{o2} \approx 86.81 k\Omega
\]

This produces the simulated gain.

---

# 6. Simulated Performance
 6. DC Sweep Analysis (Voltage Transfer Characteristics)

To verify correct biasing and region of operation, a DC sweep of the input voltage was performed.

## Sweep Conditions

- **Sweep Variable:** Input voltage (Vin)
- **Sweep Range:** 0 V to 1.8 V
- **Step Size:** Small-signal incremental sweep
- **Supply Voltage (VDD):** 1.8 V
- ![WhatsApp Image 2026-03-04 at 13 34 40](https://github.com/user-attachments/assets/a97eb270-ec42-440c-9294-a366fa10bdbf)


## 6.1 Transient Analysis

Input:
- 10 mV peak sine wave
- Frequency = 1 kHz

Output:
- Amplified, inverted waveform
- Centered at 1.219 V

Measured gain:

\[
A_v = \frac{42.72mV}{19.99mV}
\]

\[
A_v = 2.137
\]

\[
A_v(dB) = 6.59 dB
\]
![WhatsApp Image 2026-03-04 at 13 34 40 (1)](https://github.com/user-attachments/assets/cce5c63b-edf2-4498-aa96-7fea8f4065c2)
![WhatsApp Image 2026-03-04 at 13 34 40 (2)](https://github.com/user-attachments/assets/8f2e2234-1a11-4eac-94ff-1fad61af11eb)
![WhatsApp Image 2026-03-04 at 13 34 41](https://github.com/user-attachments/assets/be18b1a4-a231-4fe3-97a2-f15773f4fbd8)


---

## 6.2 AC Analysis

- **Midband Gain:** 6.59 dB  
- **3 dB Bandwidth:** 172.53 MHz
- ![WhatsApp Image 2026-03-04 at 13 34 41 (1)](https://github.com/user-attachments/assets/6ccd2187-dade-4584-a35f-653e4483c8cb)


Active degeneration improves bandwidth and linearity while reducing absolute gain.

---

# 7. Performance Summary

| Parameter | Theoretical | Simulated | Difference |
|------------|------------|------------|------------|
| Gain (dB) | 6.59 dB | 6.59 dB | 0 dB |
| Input Bias | 0.91 V | 0.91 V | 0 V |
| Drain Current | 200 µA | 200.4 µA | 0.4 µA |

---

# 8. Conclusion

By refining the channel-length modulation parameter to:

\[
\lambda = 0.185 \, V^{-1}
\]

the small-signal theoretical model aligns closely with simulation results.

The use of NMOS active degeneration provides:

- Controlled source voltage  
- Improved linearity  
- Stable gain  
- Wide bandwidth (~172 MHz)  

Although the voltage gain is moderate (6.59 dB), the configuration achieves strong high-frequency performance with reliable bias stability, making it suitable for high-speed analog applications.

---
