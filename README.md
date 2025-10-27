Project Title:

Smart Energy Theft Detection and Automatic Cutoff using eSim

Developed by:

Rupawaani K

1. Project Overview

This project aims to detect and prevent electricity theft by sensing variations in the supply current using a shunt resistor and an operational amplifier–comparator setup.
When abnormal current (caused by unauthorized load connection) is detected, the system triggers an alarm LED and automatically disconnects the load using a MOSFET switch.

The entire circuit is designed and simulated using eSim (FOSSEE, IIT Bombay) — an open-source EDA tool based on KiCad and Ngspice.

2. Tools and Environment Used

Software: eSim (FOSSEE IIT Bombay)

Simulation Engine: Ngspice

Design Platform: KiCad Schematic Editor

Analysis Type: Transient Analysis (0 to 1 s)

Operating Voltage: 12 V DC

3. Circuit Components
Component	Symbol	Description	Typical Value
DC Supply	V1	Power source	12 V
Shunt Resistor	R1	Current sensing resistor	1 Ω
Load Resistor	R2	Simulated load	100 Ω
Op-Amp	LM321	Amplifies voltage difference	Gain ≈ 5
Comparator	B-source / LM311	Compares with reference (0.8 V)	—
MOSFET	Mseries	Acts as cutoff switch	N-channel
LED	D1	Theft alarm indicator	Red LED
Divider Resistors	R3, R4	Generate reference voltage	10 kΩ each
Current Source	I1	Simulates theft event	0.2 A pulse
4. Working Principle

The shunt resistor (R1) develops a voltage proportional to the supply current.

The op-amp (LM321) amplifies this voltage.

The comparator compares the amplified voltage with a fixed reference voltage (Vref = 0.8 V).

When the sensed current exceeds the normal limit (theft condition), comparator output goes HIGH (12 V).

This signal:

Turns ON the alarm LED, and

Turns OFF the MOSFET connected in series with the load (cutoff).

As a result, the load is disconnected, preventing further power theft.

5. Simulation Results

Normal Condition (0–0.3 s):
Comparator output = LOW (0 V), Load Voltage = 12 V (connected).

Theft Condition (0.3–0.6 s):
Current spike detected → Comparator output = HIGH (12 V), Load Voltage = 0 V (cutoff active).

Restored Condition (>0.6 s):
Current normal → Comparator output returns LOW, Load reconnected.

The waveform plots confirm the correct operation of theft detection and automatic disconnection.
