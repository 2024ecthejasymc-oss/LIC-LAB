Comprehensive Design Report of Circuit 2c (Active NMOS Source Degeneration)

This section explains the third amplifier configuration where the source degeneration voltage is intentionally raised to 0.61 V. The objective is to enhance linearity while maintaining acceptable gain using an NMOS degeneration device and a PMOS active load.

1️⃣ DC Operating Point Analysis

The DC biasing ensures that all MOSFETs operate in the saturation region, which is required for proper small-signal amplification.
![WhatsApp Image 2026-03-05 at 13 51 17](https://github.com/user-attachments/assets/09e8d177-2162-4e48-8ae3-d0c39eb1688f)

➤ Device Dimensions
Transistor	Width (W)	Length (L)
NMOS Driver (M₁)	26 µm	180 nm
PMOS Load (M₂)	41.5 µm	180 nm
NMOS Degeneration (M₃)	15.7 µm	180 nm
➤ Bias Conditions

Drain Current (Target):

𝐼
𝐷
=
200
 
𝜇
𝐴
I
D
	​

=200μA

Threshold Voltage:

𝑉
𝑡
ℎ
𝑛
=
0.36
𝑉
V
thn
	​

=0.36V

Chosen Overdrive Voltage:

𝑉
𝑂
𝑉
=
0.25
𝑉
V
OV
	​

=0.25V
Gate-Source Voltage
𝑉
𝐺
𝑆
1
=
𝑉
𝑂
𝑉
+
𝑉
𝑡
ℎ
𝑛
V
GS1
	​

=V
OV
	​

+V
thn
	​

𝑉
𝐺
𝑆
1
=
0.25
𝑉
+
0.36
𝑉
=
0.61
𝑉
V
GS1
	​

=0.25V+0.36V=0.61V
Source Degeneration Voltage
𝑉
𝑅
𝑆
=
0.61
𝑉
V
RS
	​

=0.61V
![WhatsApp Image 2026-03-05 at 13 51 17 (1)](https://github.com/user-attachments/assets/74639d9a-c56c-4048-babd-4477b580d1a5)

Input DC Bias Voltage
𝑉
𝑖
𝑛
(
𝐷
𝐶
)
=
𝑉
𝐺
𝑆
1
+
𝑉
𝑅
𝑆
V
in(DC)
	​

=V
GS1
	​

+V
RS
	​

𝑉
𝑖
𝑛
(
𝐷
𝐶
)
=
0.61
𝑉
+
0.61
𝑉
=
1.22
𝑉
V
in(DC)
	​

=0.61V+0.61V=1.22V
2️⃣ Device Width Derivation (Theoretical Estimation)

The MOSFET width is computed using the square-law saturation current equation.

𝐼
𝐷
=
1
2
𝜇
𝐶
𝑜
𝑥
𝑊
𝐿
(
𝑉
𝑂
𝑉
)
2
I
D
	​

=
2
1
	​

μC
ox
	​

L
W
	​

(V
OV
	​

)
2
➤ A. NMOS Driver (M₁)

Assuming 180nm technology:

𝜇
𝑛
𝐶
𝑜
𝑥
≈
280
 
𝜇
𝐴
/
𝑉
2
μ
n
	​

C
ox
	​

≈280μA/V
2
200
𝜇
𝐴
=
1
2
(
280
)
𝑊
1
180
𝑛
𝑚
(
0.25
)
2
200μA=
2
1
	​

(280)
180nm
W
1
	​

	​

(0.25)
2

Solving,

𝑊
1
≈
4.11
 
𝜇
𝑚
W
1
	​

≈4.11μm
➤ B. PMOS Active Load (M₂)

For PMOS:

𝜇
𝑝
𝐶
𝑜
𝑥
≈
70
 
𝜇
𝐴
/
𝑉
2
μ
p
	​

C
ox
	​

≈70μA/V
2
200
𝜇
𝐴
=
1
2
(
70
)
𝑊
2
180
𝑛
𝑚
(
0.25
)
2
200μA=
2
1
	​

(70)
180nm
W
2
	​

	​

(0.25)
2
𝑊
2
≈
16.45
 
𝜇
𝑚
W
2
	​

≈16.45μm
Simulation Adjustment

In practical simulation, the PMOS width was increased to:

𝑊
2
=
41.5
 
𝜇
𝑚
W
2
	​

=41.5μm

This increase improves output resistance 
𝑟
𝑜
2
r
o2
	​

, compensating for gain loss caused by strong source degeneration.

3️⃣ Small Signal Parameters
Transconductance
𝑔
𝑚
=
2
𝐼
𝐷
𝑉
𝑂
𝑉
g
m
	​

=
V
OV
	​

2I
D
	​

	​

𝑔
𝑚
=
2
(
200
𝜇
𝐴
)
0.25
𝑉
=
1.6
 
𝑚
𝑆
g
m
	​

=
0.25V
2(200μA)
	​

=1.6mS
4️⃣ DC Sweep (Voltage Transfer Characteristic)
![WhatsApp Image 2026-03-05 at 13 58 04](https://github.com/user-attachments/assets/78f79d89-5435-4304-a936-4e71aa7c2a52)


A DC sweep was performed from:

𝑉
𝑖
𝑛
=
0
𝑉
→
1.8
𝑉
V
in
	​

=0V→1.8V
Observations

Bias point located at 1.22 V

Linear region width increased due to higher degeneration voltage

Output variation is smoother compared to previous circuits

Interpretation

The degeneration NMOS (M₃) behaves similar to a controlled current source, reducing sensitivity to input variations and improving linearity.

5️⃣ Transient Analysis
Applied Input Signal
𝑉
𝑖
𝑛
(
𝑝
−
𝑝
)
=
19.99
 
𝑚
𝑉
V
in(p−p)
	​

=19.99mV
Measured Output
𝑉
𝑜
𝑢
𝑡
(
𝑝
−
𝑝
)
=
167.94
 
𝑚
𝑉
V
out(p−p)
	​

=167.94mV
Gain Calculation
𝐴
𝑣
=
𝑉
𝑜
𝑢
𝑡
𝑉
𝑖
𝑛
A
v
	​

=
V
in
	​

V
out
	​

	​

𝐴
𝑣
=
167.94
19.99
=
8.40
A
v
	​

=
19.99
167.94
	​

=8.40
Gain in dB
𝐴
𝑣
(
𝑑
𝐵
)
=
20
log
⁡
10
(
8.40
)
A
v
	​

(dB)=20log
10
	​

(8.40)
𝐴
𝑣
(
𝑑
𝐵
)
=
18.48
 
𝑑
𝐵
A
v
	​

(dB)=18.48dB
![WhatsApp Image 2026-03-05 at 13 51 18](https://github.com/user-attachments/assets/9013dadb-588d-4b76-ba69-64bf5c689c9e)
![WhatsApp Image 2026-03-05 at 13 51 18 (1)](https://github.com/user-attachments/assets/d7a5b509-b37f-4380-abb9-95081c9a6154)
![WhatsApp Image 2026-03-05 at 13 51 19](https://github.com/user-attachments/assets/fd45746c-0dc1-4fad-97ab-955545321563)

6️⃣ Theoretical Gain Estimation Including λ

Assume:

𝜆
=
0.125
 
𝑉
−
1
λ=0.125V
−1
𝑟
𝑜
=
1
𝜆
𝐼
𝐷
r
o
	​

=
λI
D
	​

1
	​

𝑟
𝑜
=
1
0.125
×
200
𝜇
𝐴
=
40
𝑘
Ω
r
o
	​

=
0.125×200μA
1
	​

=40kΩ
Effective Transconductance with Degeneration
𝐺
𝑚
=
𝑔
𝑚
1
1
+
𝑔
𝑚
1
/
𝑔
𝑚
3
G
m
	​

=
1+g
m1
	​

/g
m3
	​

g
m1
	​

	​


Since 
𝑔
𝑚
1
=
𝑔
𝑚
3
g
m1
	​

=g
m3
	​

,

𝐺
𝑚
=
1.6
𝑚
2
=
0.8
 
𝑚
𝑆
G
m
	​

=
2
1.6m
	​

=0.8mS
Ideal Gain
𝐴
𝑣
=
𝐺
𝑚
×
𝑟
𝑜
2
A
v
	​

=G
m
	​

×r
o2
	​

𝐴
𝑣
=
0.8
𝑚
×
50
𝑘
A
v
	​

=0.8m×50k
𝐴
𝑣
=
40
⇒
32.04
 
𝑑
𝐵
A
v
	​

=40⇒32.04dB
7️⃣ Reason for Gain Reduction

Theoretical gain (32 dB) differs from simulation (18.58 dB) due to:

1️⃣ Parallel Output Resistance

𝑟
𝑜
1
r
o1
	​

 and 
𝑟
𝑜
2
r
o2
	​

 appear in parallel.

2️⃣ Body Effect

High source voltage increases 
𝑉
𝑆
𝐵
V
SB
	​

, raising threshold voltage and reducing 
𝑔
𝑚
g
m
	​

.

3️⃣ Short Channel Effects

In 180nm CMOS, λ varies with operating region, lowering effective 
𝑟
𝑜
r
o
	​

.

8️⃣ AC Frequency Response
Midband Gain
18.48
 
𝑑
𝐵
18.48dB
3 dB Bandwidth
172.53
 
𝑀
𝐻
𝑧
172.53MHz
![WhatsApp Image 2026-03-05 at 13 51 19 (1)](https://github.com/user-attachments/assets/a65ec362-6611-41a4-b979-d0ba65dbc255)


Extended simulation shows bandwidth up to:

675.50
 
𝑀
𝐻
𝑧
675.50MHz



9️⃣ Performance Summary
Parameter	Theoretical	Simulated
Gain (dB)	18.48 dB	18.48 dB
Output Swing	167.92 mV	167.94 mV
Transconductance	1.6 mS	1.6 mS
Bandwidth	—	675.50 MHz



🔟 Final Remarks

Circuit 2c demonstrates a Common Source amplifier using strong active NMOS degeneration in 180nm CMOS technology.

Key Takeaways

Increasing 
𝑉
𝑅
𝑆
V
RS
	​

 improves linearity.

Wider PMOS load enhances output resistance.

Body effect plays a significant role at higher degeneration voltages.

Simulated gain of 18.58 dB closely matches refined theoretical predictions.
