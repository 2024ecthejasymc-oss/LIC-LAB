# Analysis of MOSFET Differential Amplifier Configurations

## Aim
To design and simulate a MOSFET differential amplifier using LTspice and evaluate its performance through DC, Transient, and AC analysis.

---

## Specifications

| Parameter | Symbol | Value |
| :--- | :--- | :--- |
| Positive Supply Voltage | $V_{DD}$ | 0.9 V |
| Negative Supply Voltage | $V_{SS}$ | -0.9 V |
| Input Common-Mode Voltage | $V_{ICM}$ | 0 V |
| Output Common-Mode Voltage | $V_{OCM}$ | 0 V |
| Tail Node Voltage | $V_P$ | -0.7 V |
| Channel Length | $L$ | 480 nm |
| Maximum Power | $P_{max}$ | 1.8 mW |

---

## Introduction
The MOSFET differential amplifier is a fundamental analog circuit used to amplify the difference between two input signals while rejecting common-mode noise.

Applications include:
- Operational Amplifiers  
- Comparators  
- Analog Signal Processing  

---

## Theoretical Background

### Differential Input
$$
V_{id} = V_{in1} - V_{in2}
$$

---

### Small-Signal Gain
$$
A_v = g_m R_{out}
$$

$$
g_m = \frac{2I_D}{V_{ov}}
$$

---

### Linear Operation Condition
$$
|V_{id}| \le \sqrt{2}V_{ov}
$$

---

## Circuit Description (Resistive Load)

### Components
- NMOS Transistors: $M_1$, $M_2$  
- Tail Current Source: $I_{SS}$  
- Load Resistors: $R_D$  

### Terminals

| Terminal | Description |
| :--- | :--- |
| $V_{in1}$ | Gate of $M_1$ |
| $V_{in2}$ | Gate of $M_2$ |
| $V_{out1}$ | Drain of $M_1$ |
| $V_{out2}$ | Drain of $M_2$ |

---

### Gain Expression
$$
A_v = -g_m (R_D \parallel r_o)
$$

---

## Working Principle

### Balanced Condition
- $I_{D1} = I_{D2} = I_{SS}/2$  
- Output voltages equal  

---

### Differential Input
- Current is steered between transistors  
- One increases, the other decreases  

---

### Output Equation
$$
V_{out} = V_{DD} - I_D R_D
$$

---

### Saturation Condition
$$
V_{DS} \ge V_{GS} - V_T
$$

---

## Tail Current Source Analysis

The tail current source ensures:
- Constant current ($I_{SS}$)  
- High output resistance  

### Importance
- Improves gain  
- Improves CMRR  
- Stabilizes biasing  

---

## Output Resistance

$$
r_o = \frac{1}{\lambda I_D}
$$

Higher $r_o$ leads to higher gain.

---

## Design Calculations
![WhatsApp Image 2026-03-28 at 20 30 47](https://github.com/user-attachments/assets/8fa5d3a3-6000-48c5-81cc-9d8c16b64e81)


# MOSFET Differential Amplifier – Calculation

## 🔧 Given Values

- Supply Voltage:  
  \( V_{DD} = 0.9 \, V \)  
  \( V_{SS} = -0.9 \, V \)

- Resistors:  
  \( R_1 = R_2 = 1.8k\Omega \)

- Tail Current:  
  \( I_{tail} = 1 \, mA \)

- Balanced Inputs ⇒  
  \( V_{out1} \approx V_{out2} \)

---

## 🧮 1. Drain Current Calculation

For a balanced differential pair:

\[
I_{D1} = I_{D2} = \frac{I_{tail}}{2}
\]

\[
I_{D1} = I_{D2} = \frac{1\,mA}{2} = 0.5\,mA
\]

**Simulation Result:**
- \( Id(M1) = 0.0005 \, A \)
- \( Id(M2) = 0.0005 \, A \)

---

## 🧮 2. Output Voltage Calculation

Voltage drop across resistor:

\[
V_R = I_D \times R
\]

\[
V_R = 0.5\,mA \times 1.8k\Omega = 0.9\,V
\]

Output voltage:

\[
V_{out} = V_{DD} - V_R
\]

\[
V_{out} = 0.9 - 0.9 = 0\,V
\]

**Simulation Result:**
- \( V(out1) \approx 0 \)
- \( V(out2) \approx 0 \)

---

## 🧮 3. Source Node Voltage

From simulation:

\[
V_S = -0.7046 \, V
\]

---

## 🧮 4. Gate-Source Voltage \( V_{GS} \)

\[
V_{GS} = V_G - V_S
\]

\[
V_{GS} = 0 - (-0.7046) = 0.7046 \, V
\]

---

## 🧮 5. Saturation Condition Check

Condition for NMOS saturation:

\[
V_{DS} > V_{GS} - V_{TH}
\]

\[
V_{DS} = V_D - V_S = 0 - (-0.7046) = 0.7046 \, V
\]

Assuming:

\[
V_{TH} \approx 0.4 - 0.5 \, V
\]

\[
V_{GS} - V_{TH} \approx 0.2 - 0.3 \, V
\]

\[
0.7046 > 0.3
\]

**Conclusion:** Transistors operate in **Saturation Region**

---

## 🧮 6. Supply Current Check

From simulation:

\[
I(V1) = -1\,mA
\]

\[
I_{total} = I_{tail} = 1\,mA
\]

---

## ✅ Final Results

| Parameter | Value |
|----------|------|
| Drain Current (each MOSFET) | \( 0.5 \, mA \) |
| Output Voltage | \( 0 \, V \) |
| Source Voltage | \( -0.7046 \, V \) |
| \( V_{GS} \) | \( 0.7046 \, V \) |
| Region of Operation | Saturation |
| Tail Current | \( 1 \, mA \) |

---
## DC ANALYSIS
![WhatsApp Image 2026-03-28 at 20 30 47 (1)](https://github.com/user-attachments/assets/253743e1-6f4f-4d4a-b330-bac2b71cb46a)
# MOSFET Differential Amplifier – Calculation


## Common-Mode Ranges

### ICMR
$$
-0.34V \le V_{ICM} \le 0.36V
$$

### OCMR
$$
-0.36V \le V_{OCM} \le 0.9V
$$

---

## Differential Input Range
$$
|V_{id}| \le 0.48V
$$

---

## CMRR (Common-Mode Rejection Ratio)

$$
CMRR = \frac{A_d}{A_c}
$$

$$
CMRR(dB) = 20\log_{10}\left(\frac{A_d}{A_c}\right)
$$

Higher CMRR ⇒ Better noise rejection  

---

## Transient Analysis

### Linear Case
![WhatsApp Image 2026-03-28 at 20 30 47 (2)](https://github.com/user-attachments/assets/ce5c32bb-cf94-4b6a-a13d-ee12a2049be2)

- $V_{id} = 100mV$  
- Output: Sinusoidal  
- Constant gain  

### Non-Linear Case
![WhatsApp Image 2026-03-28 at 20 30 48](https://github.com/user-attachments/assets/7ae8e425-a6a2-4730-9b2c-db2b497b2157)

- $V_{id} = 800mV$  
- Output: Clipping  
- One transistor OFF  

---

## Gain Analysis

$$
A_v = 5.74
$$

$$
A_v(dB) = 15.18dB
$$

### Comparison

| Type | Gain |
| :--- | :--- |
| Theoretical | 4.5 |
| Simulated | 5.74 |

---

## AC Analysis
![WhatsApp Image 2026-03-28 at 20 30 48 (2)](https://github.com/user-attachments/assets/0c7f4eb3-8c03-4f07-ba28-6c49e712aa2c)

| Parameter | Value |
| :--- | :--- |
| Midband Gain | 15.6 dB |
| Bandwidth | 5.128 GHz |
| Unity Gain BW | 30.9 GHz |

---

## Frequency Response

- Flat gain up to GHz range  
- Roll-off due to parasitic capacitances  
- Phase ≈ $180^\circ$  

---

## Power Efficiency

$$
P = 1.8mW
$$

Trade-off:
- Higher current → Higher gain  
- But → More power consumption  

---

## Non-Ideal Effects

- Channel Length Modulation  
- Mobility Degradation  
- Body Effect  
- Parasitic Capacitances  

---

## Advantages

- High CMRR  
- Good linearity  
- Simple design  
- IC compatible  

---

## Disadvantages

- Limited gain (resistive load)  
- Power consumption  
- Limited swing  
- Sensitive to mismatch  

---

## Applications

- Operational Amplifiers  
- Comparators  
- ADC/DAC  
- Communication Circuits  

---

## Conclusion

The MOSFET differential amplifier achieves:

- Gain ≈ **5.74 V/V**  
- Bandwidth ≈ **5.13 GHz**  
- Stable saturation operation  

The design successfully demonstrates both linear and non-linear behavior while meeting all specifications.
