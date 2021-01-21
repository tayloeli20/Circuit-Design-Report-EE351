### EE 351-A Electronic Circuits 1

### Dr. Peter Osterberg

<span id="_hrqhgpm5ii44" class="anchor"></span>**Design Report**

Elias Taylor
------------

DATE: &lt;12/02/2020&gt; 
-------------------------

**Introduction:**

The goal of this project was to design and simulate a single-stage
Common Emitter Amplifier as shown in Fig. 4, but with unknown values for
R1, R2, RE and RC. The circuit also had constraints; the amplifier must
have a signal gain above 125 V/V for mid-band frequencies and also
consume less than 25 mW of DC power. We were able to accomplish this by
analysing the circuit's ideal values to determine the circuit's resistor
values and use those values to determine node currents, node voltages,
voltage gain and power consumed. The circuit was then simulated in
PSPICE to compare to both the AC and DC hand analysis values as well as
to generate Bode Plots for both the output voltage and phase voltage
values.

**Hand Analysis:**

The first thing accomplished was determining the current values for IE
and IC (current values going across each respective resistor). Using the
upper and lower bounds for our current based on the constraints given it
is possible to determine the upper and lower bound for our resistor
value. The resistor value was then chosen first and then it was possible
to determine the values for each respective current (see full hand
analysis for details). We were then able to use DC analysis to determine
the current values I1 and I2 for resistors R1 and R2 as seen in Fig. 1.
Once DC analysis was complete we converted our circuit for AC analysis
as seen in Fig. 2. We substituted the PNP transistor for the Hybrid-Pi
model for analysis, then simplifying the circuit as depicted in Fig. 3.
This gave us the gain as well as Rin and Rout (not given in PSPICE
simulation), allowing us to determine the DC power consumption. With
calculations complete we see our circuit does follow the 1/3rd rule as
well as the 1/10th rule and fits the constraints of under than or equal
to the power consumption of 25mW. With our values calculated we were
also able to determine that the circuit conforms to Bias stability for
both temperature and beta stability.

![](media/image1.png){width="5.229166666666667in"
height="2.6458333333333335in"}

Fig 1: Hand Drawn Circuit with Resistor Values

![](media/image7.png){width="5.375in" height="2.6354166666666665in"}

Fig 2: AC Hand Analysis

![](media/image5.png){width="5.875in" height="1.4791666666666667in"}

Fig 3: Simplified AC Analysis

**PSPICE Simulation:**

We then simulated the circuit in PSPICE after hand analysis was
complete. We modeled the circuit using QBREAKP3 as our PNP transistor.
The completed circuit modeled in PSPICE with current and voltage values
can be seen in Fig. 4. We then generated a Bode plot for Vout’s Voltage
Magnitude as well as the Phase value (Fig. 5), voltage magnitude in red
and output voltage phase in green. PSPICE also calculated the DC power
used being 9.63mW, also in the complete datasheet at the end of report
as well as Table 1. The midband gain was found using the cursor value
depicted in Fig. 6. The edited down datasheet for PSPICE can be seen at
the end of this report.

  **Parameter**   **Hand**       **PSPICE**
  --------------- -------------- --------------
  IC              625.0 uA       577.79 uA
  IE              587.5 uA       582.73 uA
  IB              5.29 uA        4.946 uA
  IR1             59.21 uA       59.43 uA
  IR2             64.5 uA        65.38 uA
  VC              4.66 V         4.622 V
  VB              9.6 V          9.58 V
  VE              10.30 V        10.34 V
  PDC             9.75 mW        9.63mW
  Gain            -159.958 V/V   -154.265 V/V
  Rin             4360.61 Ω      N/A
  Rout            5017.29 Ω      N/A

Table 1: Hand Calculation and Simulated Component

![](media/image4.png){width="6.5in" height="3.1944444444444446in"}

Fig 4: PSPICE Circuit Config. With Node Current & Voltage

Fig 5: Probe Cursor Value For Voltage Magn, A1 second Value is Midband
Gain.![](media/image2.png){width="2.03125in"
height="0.6770833333333334in"}

![](media/image3.png){width="6.223958880139983in"
height="3.5208333333333335in"}

Fig 6: PSPICE Bode Plots of Output Voltage Magnitude and Phase

**Conclusion:**

Our completed values for both hand analysis and PSPICE values are
recorded in Table 1 above. We had a margin of error for both AC and DC
hand calculated values compared to PSPICE, but it is small enough for us
to conclude that our calculations are correct as they are in an
acceptable range. The margin of error may be due to rounded values by
hand compounding, or because PSPICE simulates conditions not factored
into our hand analysis. Over all the design goal was met, and the
Current Emitter Amplifier behaves within the given constraints.

![](media/image8.jpg){width="8.53125in" height="11.01562554680665in"}

![](media/image10.jpg){width="8.520833333333334in"
height="10.98437554680665in"}

![](media/image9.jpg){width="8.5in" height="11.005208880139982in"}

![](media/image6.jpg){width="8.520833333333334in"
height="11.005208880139982in"}

\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

\* Schematics Netlist \*

C\_Cb \$N\_0001 \$N\_0002 20u

C\_CL \$N\_0003 Vout 20u

R\_RL 0 Vout 100k

R\_R2 0 \$N\_0002 148.8k

V\_V2 \$N\_0004 0 15v

R\_Rs \$N\_0005 \$N\_0001 100

V\_Vs \$N\_0005 0 DC 0V AC 1V

R\_R1 \$N\_0002 \$N\_0004 91.2k

R\_Rc 0 \$N\_0003 8k

C\_CE \$N\_0006 0 100u

Q\_Q4 \$N\_0003 \$N\_0002 \$N\_0006 QbreakP-X1

R\_RE \$N\_0006 \$N\_0004 8k

\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

\*\*\*\* BJT MODEL PARAMETERS

QbreakP-X1

PNP

IS 100.000000E-18

BF 110

NF 1

VAF 80

BR 1

NR 1

CJE 10.000000E-12

CJC 5.000000E-12

TF 500.000000E-12

CN 2.2

D .52

\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

NODE VOLTAGE NODE VOLTAGE NODE VOLTAGE NODE VOLTAGE

( Vout) 0.0000 (\$N\_0001) 0.0000 (\$N\_0002) 9.5797

(\$N\_0003) 4.6223 (\$N\_0004) 15.0000

(\$N\_0005) 0.0000 (\$N\_0006) 10.3380

VOLTAGE SOURCE CURRENTS

NAME CURRENT

V\_V2 -6.422E-04

V\_Vs 0.000E+00

**TOTAL POWER DISSIPATION 9.63E-03 WATTS**
