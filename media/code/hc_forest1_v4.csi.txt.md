{CR23X}

<!-- -->

HC\_Forest1\_v4.csi\
\
Controls Hidden Canyon Forest1 datalogger (1)\
Operates 2 multiplexers, each with 6 Decagon EC-TM and 6 Campbell CS-616/615 sensors,\
and 3 IR radiometers, 1 T/H probe, 1 windset (direct to CR23x)\
\
by Greg Maurer\
version 1 (11/02/2009)\
version 2 (01/07/2010): Doubled delay in instruction 15 (serial I/O) to 50. This had little effect on\
reading the decagon sensors\
version 3 (01/13/2010): Added CS 615 loops to the Campbell processing instructions (there are 5 CS-615's\
in the profiles)\
version 4 (10/16/2010): Added table 2 (switch on relay for radio power), Changed mux wiring and added\
third MUX.\
\*\*\*Note that campbell 616s on MUX 1 & 2 are enabled with SW12V, not COM ports (avoids serial mode problem)

-   Table 1 Program

` 01: 60        Execution Interval (seconds)`

------------------------- Datalogger measurements -------------------------------\
\
----Measure battery voltage----

1: Batt Voltage (P10)

`1: 1        Loc [ batt_volt ]`

----Measure panel temperature of datalogger----

2: Panel Temperature (P17)

`1: 2        Loc [ panelT    ]`

\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\
MUX Notes\
\
MUX 1 and 2 are each wired to 6 Decagon and 6 Campbell VWC sensors\
MUX 3 is wired to 6 Campbell 616's and 6 107 thermistors\
\
4x16 mode\
\
MUX 1, 2, & 3 wired to Forest1-CR23x as follows:\
\
Res ---&gt; C1\
Clk ---&gt; C2, C3, C4 (for Mux 1, 2, and 3 respectively)\
12V and G---&gt; 12V and G\
\
MUX 1 and 2 only:\
COM OddH ---&gt; SW12vdc\
COM OddL ---&gt; C5 & C6\
COM EvenH---&gt; SE 1 & 3\
COM EvenL---&gt; SE 2 & 4\
COM gnd ---&gt; CR23x signal gnd\
\
MUX 3:\
COM OddH ---&gt; EX 3\
COM OddL ---&gt; C7\
COM EvenH---&gt; SE 5\
COM EvenL---&gt; SE 6\
COM gnd ---&gt; CR23x signal gnd\
\
----Campbell CS-616/15 sensor----\
\
Orange(enable)---&gt; Odd H (SW12V)\
Green(signal) ---&gt; Even H/L (SE)\
Red(12V) ---&gt; Terminal strip (12vdc)\
Black(ground) ---&gt; signal ground\
Clear(shield) ---&gt; Terminal strip (power ground)\
\
----Campbell 107 thermistors----\
\
Black(excitation) ---&gt; Odd H (EX 3)\
Red(T signal) ---&gt; Even H & L (SE 5&6)\
Purple(signal gnd)---&gt; signal ground\
Clear(shield) ---) signal ground\
\
----Decagon EC-TM sensor----\
\
Wiring to AM16/32 panel is:\
White(excite) ---&gt; Odd H (SW12vdc)\
Red (signal) ---&gt; Odd L (C5/C6)\
Bare (sheath) ---&gt; signal ground\
\
\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*

<!-- -->

-------- Reset MUX1, MUX2, MUX3 ---------

3: Do (P86)

`1: 41       Set Port 1 High`

||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||\
||||||||||||||||||||||||| Campbell sensor loops (MUX 1-3) ||||||||||||||||||||||||\
||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||

<!-- -->

-\*-\*-\*-\*-\*-\*-\*-\*-\* MUX 1 \*-\*-\*-\*-\*-\*-\*-\*-\*-\*-\
Clock with control port 2\
Pit 1 & 3 wired in order: 1-5cm, 1-20cm, 1-60cm, 3-60cm, 3-5cm, 3-20cm\
\
\*\*\* Loop 1: \*\*\*\
\
4 CS-615s in Profile 1 (all 3 depths) & 3 (60cm)

4: Beginning of Loop (P87)

`1: 0        Delay
`2: 2        Loop Count`

`    5:  Step Loop Index (P90)
`     1: 2        Step`

`    6:  Do (P86)
`     1: 72       Pulse Port 2`

`    7:  Delay w/Opt Excitation (P22)
`     1: 1        Ex Channel
`     2: 0        Delay W/Ex (0.01 sec units)
`     3: 1        Delay After Ex (0.01 sec units)
`     4: 0        mV Excitation`

Use SW12V to enable sensors

`    8:  Do (P86)
`     1: 49       Turn On Switched 12V`

`    9:  Period Average (SE) (P27)
`     1: 2        Reps
`     2: 4        200 kHz Max Freq @ 500 mV Peak to Peak, Period Output
`     3: 1        SE Channel
`     4: 10       No. of Cycles
`     5: 5        Timeout (0.01 sec units)
`     6: 3     -- Loc [ Period1   ]
`     7: .001     Multiplier
`     8: 0.0      Offset`

`    10:  Do (P86)
`     1: 59       Turn Off Switched 12V`

11: End (P95)

CONVERT Periods 1-4 to soil VWC\
These coefficients are for a low EC ( &lt;1.0 dS per meter)

12: Polynomial (P55)

`1: 4        Reps
`2: 3        X Loc [ Period1   ]
`3: 21       F(X) Loc [ P1_5sm    ]
`4: -0.187   C0
`5: 0.037    C1
`6: 0.335    C2
`7: 0.0      C3
`8: 0.0      C4
`9: 0.0      C5`

\*\*\* Loop 2: \*\*\*\
\
2 CS-616s in Profile 3 (5 & 20cm)

13: Do (P86)

`1: 72       Pulse Port 2`

14: Delay w/Opt Excitation (P22)

`1: 1        Ex Channel
`2: 0        Delay W/Ex (0.01 sec units)
`3: 1        Delay After Ex (0.01 sec units)
`4: 0        mV Excitation`

Use period average command with SW12V excitation (instead of P138).

15: Do (P86)

`1: 49       Turn On Switched 12V`

16: Period Average (SE) (P27)

`1: 2        Reps
`2: 4        200 kHz Max Freq @ 500 mV Peak to Peak, Period Output
`3: 1        SE Channel
`4: 100      No. of Cycles
`5: 1        Timeout (0.01 sec units)
`6: 7        Loc [ Period5   ]
`7: 1        Multiplier
`8: 0.0      Offset`

17: Do (P86)

`1: 59       Turn Off Switched 12V`

CONVERT period 5 & 6 to soil VWC

18: Polynomial (P55)

`1: 2        Reps
`2: 7        X Loc [ Period5   ]
`3: 25       F(X) Loc [ P3_5sm    ]
`4: -.0663   C0
`5: -.0063   C1
`6: 0.0007   C2
`7: 0.0      C3
`8: 0.0      C4
`9: 0.0      C5`

Pause MUX1 on channel 4

19: Do (P86)

`1: 72       Pulse Port 2`

-\*-\*-\*-\*-\*-\*-\*-\*-\* MUX 2 \*-\*-\*-\*-\*-\*-\*-\*-\*-\*-\
Clock with control port 3\
Pit 2 & 4 wired in order: 2-5cm, 2-20cm, 2-60cm, , 4-5cm, 4-20cm, 4-60cm\
\
\*\*\* Loop 1: \*\*\*\
\
2 CS-615s in Profile 2 (5 & 20cm)

20: Do (P86)

`1: 73       Pulse Port 3`

21: Delay w/Opt Excitation (P22)

`1: 1        Ex Channel
`2: 0        Delay W/Ex (0.01 sec units)
`3: 1        Delay After Ex (0.01 sec units)
`4: 0        mV Excitation`

Use SW12V to enable sensors

22: Do (P86)

`1: 49       Turn On Switched 12V`

23: Period Average (SE) (P27)

`1: 2        Reps
`2: 4        200 kHz Max Freq @ 500 mV Peak to Peak, Period Output
`3: 3        SE Channel
`4: 10       No. of Cycles
`5: 5        Timeout (0.01 sec units)
`6: 9        Loc [ Period7   ]
`7: .001     Multiplier
`8: 0.0      Offset`

24: Do (P86)

`1: 59       Turn Off Switched 12V`

CONVERT Periods 7 & 8 to soil VWC\
These coefficients are for a low EC ( &lt;1.0 dS per meter)

25: Polynomial (P55)

`1: 2        Reps
`2: 9        X Loc [ Period7   ]
`3: 27       F(X) Loc [ P2_5sm    ]
`4: -0.187   C0
`5: 0.037    C1
`6: 0.335    C2
`7: 0.0      C3
`8: 0.0      C4
`9: 0.0      C5`

\*\*\* Loop 2: \*\*\*\
\
4 CS-616s in Profile 2 (60cm) and 4 (5,20,60cm)

26: Beginning of Loop (P87)

`1: 0        Delay
`2: 2        Loop Count`

`    27:  Step Loop Index (P90)
`     1: 2        Step`

`    28:  Do (P86)
`     1: 73       Pulse Port 3`

`    29:  Delay w/Opt Excitation (P22)
`     1: 1        Ex Channel
`     2: 0        Delay W/Ex (0.01 sec units)
`     3: 1        Delay After Ex (0.01 sec units)
`     4: 0        mV Excitation`

Use period average command with SW12V excitation (instead of P138).

`    30:  Do (P86)
`     1: 49       Turn On Switched 12V`

`    31:  Period Average (SE) (P27)
`     1: 2        Reps
`     2: 4        200 kHz Max Freq @ 500 mV Peak to Peak, Period Output
`     3: 3        SE Channel
`     4: 100      No. of Cycles
`     5: 1        Timeout (0.01 sec units)
`     6: 11    -- Loc [ Period9   ]
`     7: 1        Multiplier
`     8: 0.0      Offset`

`    32:  Do (P86)
`     1: 59       Turn Off Switched 12V`

33: End (P95)

CONVERT period 9-12 to soil VWC

34: Polynomial (P55)

`1: 4        Reps
`2: 11       X Loc [ Period9   ]
`3: 29       F(X) Loc [ P2_60sm   ]
`4: -.0663   C0
`5: -.0063   C1
`6: 0.0007   C2
`7: 0.0      C3
`8: 0.0      C4
`9: 0.0      C5`

Pause MUX2 on channel 4

35: Do (P86)

`1: 73       Pulse Port 3`

-\*-\*-\*-\*-\*-\*-\*-\*-\* MUX 3 \*-\*-\*-\*-\*-\*-\*-\*-\*-\*-\
Clock with control port 4\
Pit 5 & 7 wired in order: 5-5cm, 5-20cm, 5-60cm, , 7-5cm, 7-20cm, 7-60cm\
\
\*\*\* Loop 1: \*\*\*\
\
6 CS-616s in Profile 5 & 7 (all depths)

36: Beginning of Loop (P87)

`1: 0        Delay
`2: 3        Loop Count`

`    37:  Step Loop Index (P90)
`     1: 2        Step`

`    38:  Do (P86)
`     1: 74       Pulse Port 4`

`    39:  Delay w/Opt Excitation (P22)
`     1: 1        Ex Channel
`     2: 0        Delay W/Ex (0.01 sec units)
`     3: 1        Delay After Ex (0.01 sec units)
`     4: 0        mV Excitation`

`    40:  CS616 Water Content Reflectometer (P138)
`     1: 2        Reps
`     2: 5        SE Channel
`     3: 17       All reps use C7
`     4: 15    -- Loc [ Period13  ]
`     5: 1.0      Multiplier
`     6: 0.0      Offset`

41: End (P95)

CONVERT period 13-18 to soil VWC

42: Polynomial (P55)

`1: 6        Reps
`2: 15       X Loc [ Period13  ]
`3: 33       F(X) Loc [ P5_5sm    ]
`4: -.0663   C0
`5: -.0063   C1
`6: 0.0007   C2
`7: 0.0      C3
`8: 0.0      C4
`9: 0.0      C5`

\*\*\* Loop 2: \*\*\*\
\
6 thermistors (107s) in Profile 5 & 7 (all depths)

43: Beginning of Loop (P87)

`1: 0        Delay
`2: 3        Loop Count`

`    44:  Step Loop Index (P90)
`     1: 2        Step`

`    45:  Do (P86)
`     1: 74       Pulse Port 4`

`    46:  Temp (107) (P11)
`     1: 2        Reps
`     2: 5        SE Channel
`     3: 23       Excite all reps w/E3, 60Hz, 10ms delay
`     4: 39    -- Loc [ P5_5st    ]
`     5: 1.0      Multiplier
`     6: 0.0      Offset`

47: End (P95)

48: Do (P86)

`1: 74       Pulse Port 4`

||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||\
||||||||||||||||||||||||| Decagon sensor loops (MUX 1-3) |||||||||||||||||||||||||\
||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||\
\
Sensors need a 5 second resting period between excitations\
\
-\*-\*-\*-\*-\*-\*-\*-\*-\* MUX 1 \*-\*-\*-\*-\*-\*-\*-\*-\*-\*-\
Clock with control port 2\
\
Profile 1d & 3d wired in order: 1d-5cm, 1d-20cm, 1d-60cm, , 3d-5cm, 3d-20cm, 3d-60cm

49: Beginning of Loop (P87)

`1: 0        Delay
`2: 6        Loop Count`

`    50:  Step Loop Index (P90)
`     1: 3        Step`

`    51:  Do (P86)
`     1: 72       Pulse Port 2`

POWER UP SENSOR

`    52:  Do (P86)
`     1: 49       Turn On Switched 12V`

DELAY FOR SENSOR TO POWER UP AND SEND DATA - Important!

`    53:  Delay w/Opt Excitation (P22)
`     1: 1        Ex Channel
`     2: 0        Delay W/Ex (0.01 sec units)
`     3: 50       Delay After Ex (0.01 sec units)
`     4: 0        mV Excitation`

MAKE SURE MUX COMMON GND IS NOT SHARED WITH POWER GROUND, OTHERWISE\
SIGNAL IS SHORTED.

`    54:  Port Serial I/O (P15)
`     1: 1        Reps
`     2: 31       TTL ASCII, 1200 Baud
`     3: 0        TX after CTS
`     4: 5        No RTS/DTR, C5 TXD/RXD
`     5: 45       Start Loc for TX [ P3d_5_1   ]
`     6: 0        Number of Locs to TX
`     7: 13       Termination Character for RX
`     8: 50       RX Buffer Size or Max Chars to RX if Par 2 indexed (--)
`     9: 1        Time Out for CTS (TX) and/or RX (0.01 sec units)
`    10: 45   --  Start Loc for RX [ P3d_5_1   ]
`    11: 1        Multiplier for RX
`    12: 0        Offset for RX`

POWER OFF SENSOR

`    55:  Do (P86)
`     1: 59       Turn Off Switched 12V`

56: End (P95)

-\*-\*-\*-\*-\*-\*-\*-\*-\* MUX 2 \*-\*-\*-\*-\*-\*-\*-\*-\*-\*-\
Clock with control port 3\
\
Profile 2d & 4d wired in order: 2d-5cm, 2d-20cm, 2d-60cm, , 4d-5cm, 4d-20cm, 4d-60cm

<!-- -->

Set number of times to increment MUX1

57: Beginning of Loop (P87)

`1: 0        Delay
`2: 6        Loop Count`

`    58:  Step Loop Index (P90)
`     1: 3        Step`

`    59:  Do (P86)
`     1: 73       Pulse Port 3`

POWER UP SENSOR

`    60:  Do (P86)
`     1: 49       Turn On Switched 12V`

DELAY FOR SENSOR TO POWER UP AND SEND DATA - Important!

`    61:  Delay w/Opt Excitation (P22)
`     1: 1        Ex Channel
`     2: 0        Delay W/Ex (0.01 sec units)
`     3: 50       Delay After Ex (0.01 sec units)
`     4: 0        mV Excitation`

MAKE SURE MUX COMMON GND IS NOT SHARED WITH POWER GROUND, OTHERWISE\
SIGNAL IS SHORTED.

`    62:  Port Serial I/O (P15)
`     1: 1        Reps
`     2: 31       TTL ASCII, 1200 Baud
`     3: 0        TX after CTS
`     4: 6        No RTS/DTR, C6 TXD/RXD
`     5: 63       Start Loc for TX [ P4d_5_1   ]
`     6: 0        Number of Locs to TX
`     7: 13       Termination Character for RX
`     8: 50       RX Buffer Size or Max Chars to RX if Par 2 indexed (--)
`     9: 1        Time Out for CTS (TX) and/or RX (0.01 sec units)
`    10: 63   --  Start Loc for RX [ P4d_5_1   ]
`    11: 1        Multiplier for RX
`    12: 0        Offset for RX`

POWER OFF SENSOR

`    63:  Do (P86)
`     1: 59       Turn Off Switched 12V`

64: End (P95)

\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*

<!-- -->

POWER OFF (RES low) all 3 muxes

65: Do (P86)

`1: 51       Set Port 1 Low`

\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*\_\*

<!-- -->

---------------------------- Forest Tower Sensors ------------------------------\
Sensors at Forest1 pole\
\
----- Apogee SI-111 Infrared radiometers-----\
# 2361 - located over treatment plot\
First measure resistnce of the thermistor and calculate sensor body\
temperature

66: AC Half Bridge (P5)

`1: 1        Reps
`2: 25       5000 mV, 60 Hz Reject, Fast Range (same as code 45)
`3: 7        SE Channel
`4: 1        Excite all reps w/Exchan 1
`5: 2500     mV Excitation
`6: 81       Loc [ mV_thrm   ]
`7: 1.0      Multiplier
`8: 0.0      Offset`

67: Z=1/X (P42)

`1: 81       X Loc [ mV_thrm   ]
`2: 82       Z Loc [ 1_mV_thrm ]`

68: Z=X+F (P34)

`1: 82       X Loc [ 1_mV_thrm ]
`2: -1.0     F
`3: 83       Z Loc [ 2_mV_thrm ]`

69: Z=X\*F (P37)

`1: 83       X Loc [ 2_mV_thrm ]
`2: 24900    F
`3: 84       Z Loc [ R_thrm    ]`

70: Z=LN(X) (P40)

`1: 84       X Loc [ R_thrm    ]
`2: 85       Z Loc [ InR_thrm  ]`

71: Z=X\*F (P37)

`1: 85       X Loc [ InR_thrm  ]
`2: 0.001    F
`3: 86       Z Loc [ Scaled_R  ]`

72: Polynomial (P55)

`1: 1        Reps
`2: 86       X Loc [ Scaled_R  ]
`3: 87       F(X) Loc [ SH_Coeffs ]
`4: .001129  C0
`5: .234108  C1
`6: 0.0      C2
`7: 87.7547  C3
`8: 0.0      C4
`9: 0.0      C5`

73: Z=1/X (P42)

`1: 87       X Loc [ SH_Coeffs ]
`2: 88       Z Loc [ SB_Temp_K ]`

74: Z=X+F (P34)

`1: 88       X Loc [ SB_Temp_K ]
`2: -273.15  F
`3: 89       Z Loc [ SB_Temp_C ]`

Measure mV output of thermopile

75: Volt (Diff) (P2)

`1: 1        Reps
`2: 21       10 mV, 60 Hz Reject, Slow Range
`3: 5        DIFF Channel
`4: 90       Loc [ mV_tpile  ]
`5: 1.0      Multiplier
`6: 0.0      Offset`

Calculation of m(slope) coefficient for target temperature calculation.\
Each sensor has unique C0, C1, and C2 values on their calibration sheet.

76: Polynomial (P55)

`1: 1        Reps
`2: 89       X Loc [ SB_Temp_C ]
`3: 91       F(X) Loc [ m_slope   ]
`4: 14338.4  C0
`5: 62.2373  C1
`6: 0.86384  C2
`7: 0.0      C3
`8: 0.0      C4
`9: 0.0      C5`

77: Z=X\*F (P37)

`1: 91       X Loc [ m_slope   ]
`2: 99999    F
`3: 91       Z Loc [ m_slope   ]`

Calculation of b (intercept) coefficient for target calculation. Each\
sensor has unique C values (again - on calib sheet).

78: Polynomial (P55)

`1: 1        Reps
`2: 89       X Loc [ SB_Temp_C ]
`3: 92       F(X) Loc [ b_inter   ]
`4: -12.7368 C0
`5: -4.82953 C1
`6: 0.28300  C2
`7: 0.0      C3
`8: 0.0      C4
`9: 0.0      C5`

79: Z=X\*F (P37)

`1: 92       X Loc [ b_inter   ]
`2: 99999    F
`3: 92       Z Loc [ b_inter   ]`

Target temperature calculation based on m and b coefficients.

80: Z=F x 10\^n (P30)

`1: 0.4      F
`2: 1        n, Exponent of 10
`3: 93       Z Loc [ Exponent1 ]`

81: Z=F x 10\^n (P30)

`1: .025     F
`2: 1        n, Exponent of 10
`3: 94       Z Loc [ Exponent2 ]`

82: Z=X\^Y (P47)

`1: 88       X Loc [ SB_Temp_K ]
`2: 93       Y Loc [ Exponent1 ]
`3: 95       Z Loc [ 1_SB_4Pow ]`

83: Z=X\*Y (P36)

`1: 90       X Loc [ mV_tpile  ]
`2: 91       Y Loc [ m_slope   ]
`3: 96       Z Loc [ 2_mVxm    ]`

84: Z=X+Y (P33)

`1: 95       X Loc [ 1_SB_4Pow ]
`2: 96       Y Loc [ 2_mVxm    ]
`3: 97       Z Loc [ 3_Sum1    ]`

85: Z=X+Y (P33)

`1: 92       X Loc [ b_inter   ]
`2: 97       Y Loc [ 3_Sum1    ]
`3: 98       Z Loc [ 4_Sum2    ]`

86: Z=X\^Y (P47)

`1: 98       X Loc [ 4_Sum2    ]
`2: 94       Y Loc [ Exponent2 ]
`3: 99       Z Loc [ SurfT_T_K ]`

87: Z=X+F (P34)

`1: 99       X Loc [ SurfT_T_K ]
`2: -273.15  F
`3: 100      Z Loc [ SurfT_T_C ]`

---- Apogee SI-111 Infrared radiometer ----\
# 2364 - located over control treatment plot near Forest1\
First measure resistnce of the thermistor and calculate sensor body\
temperature

88: AC Half Bridge (P5)

`1: 1        Reps
`2: 25       5000 mV, 60 Hz Reject, Fast Range (same as code 45)
`3: 8        SE Channel
`4: 1        Excite all reps w/Exchan 1
`5: 2500     mV Excitation
`6: 81       Loc [ mV_thrm   ]
`7: 1.0      Multiplier
`8: 0.0      Offset`

89: Z=1/X (P42)

`1: 81       X Loc [ mV_thrm   ]
`2: 82       Z Loc [ 1_mV_thrm ]`

90: Z=X+F (P34)

`1: 82       X Loc [ 1_mV_thrm ]
`2: -1.0     F
`3: 83       Z Loc [ 2_mV_thrm ]`

91: Z=X\*F (P37)

`1: 83       X Loc [ 2_mV_thrm ]
`2: 24900    F
`3: 84       Z Loc [ R_thrm    ]`

92: Z=LN(X) (P40)

`1: 84       X Loc [ R_thrm    ]
`2: 85       Z Loc [ InR_thrm  ]`

93: Z=X\*F (P37)

`1: 85       X Loc [ InR_thrm  ]
`2: 0.001    F
`3: 86       Z Loc [ Scaled_R  ]`

94: Polynomial (P55)

`1: 1        Reps
`2: 86       X Loc [ Scaled_R  ]
`3: 87       F(X) Loc [ SH_Coeffs ]
`4: .001129  C0
`5: .234108  C1
`6: 0.0      C2
`7: 87.7547  C3
`8: 0.0      C4
`9: 0.0      C5`

95: Z=1/X (P42)

`1: 87       X Loc [ SH_Coeffs ]
`2: 88       Z Loc [ SB_Temp_K ]`

96: Z=X+F (P34)

`1: 88       X Loc [ SB_Temp_K ]
`2: -273.15  F
`3: 89       Z Loc [ SB_Temp_C ]`

Measure mV output of thermopile

97: Volt (Diff) (P2)

`1: 1        Reps
`2: 21       10 mV, 60 Hz Reject, Slow Range
`3: 6        DIFF Channel
`4: 90       Loc [ mV_tpile  ]
`5: 1.0      Multiplier
`6: 0.0      Offset`

Calculation of m(slope) coefficient for target temperature calculation.\
Each sensor has unique C0, C1, and C2 values on their calibration sheet.

98: Polynomial (P55)

`1: 1        Reps
`2: 89       X Loc [ SB_Temp_C ]
`3: 91       F(X) Loc [ m_slope   ]
`4: 13076.1  C0
`5: 73.8305  C1
`6: .60645   C2
`7: 0.0      C3
`8: 0.0      C4
`9: 0.0      C5`

99: Z=X\*F (P37)

`1: 91       X Loc [ m_slope   ]
`2: 99999    F
`3: 91       Z Loc [ m_slope   ]`

Calculation of b (intercept) coefficient for target calculation. Each\
sensor has unique C values (again - on calib sheet).

100: Polynomial (P55)

`1: 1        Reps
`2: 89       X Loc [ SB_Temp_C ]
`3: 92       F(X) Loc [ b_inter   ]
`4: -82.1327 C0
`5: -9.16495 C1
`6: 0.35482  C2
`7: 0.0      C3
`8: 0.0      C4
`9: 0.0      C5`

101: Z=X\*F (P37)

`1: 92       X Loc [ b_inter   ]
`2: 99999    F
`3: 92       Z Loc [ b_inter   ]`

Target temperature calculation based on m and b coefficients.

102: Z=F x 10\^n (P30)

`1: 0.4      F
`2: 1        n, Exponent of 10
`3: 93       Z Loc [ Exponent1 ]`

103: Z=F x 10\^n (P30)

`1: .025     F
`2: 1        n, Exponent of 10
`3: 94       Z Loc [ Exponent2 ]`

104: Z=X\^Y (P47)

`1: 88       X Loc [ SB_Temp_K ]
`2: 93       Y Loc [ Exponent1 ]
`3: 95       Z Loc [ 1_SB_4Pow ]`

105: Z=X\*Y (P36)

`1: 90       X Loc [ mV_tpile  ]
`2: 91       Y Loc [ m_slope   ]
`3: 96       Z Loc [ 2_mVxm    ]`

106: Z=X+Y (P33)

`1: 95       X Loc [ 1_SB_4Pow ]
`2: 96       Y Loc [ 2_mVxm    ]
`3: 97       Z Loc [ 3_Sum1    ]`

107: Z=X+Y (P33)

`1: 92       X Loc [ b_inter   ]
`2: 97       Y Loc [ 3_Sum1    ]
`3: 98       Z Loc [ 4_Sum2    ]`

108: Z=X\^Y (P47)

`1: 98       X Loc [ 4_Sum2    ]
`2: 94       Y Loc [ Exponent2 ]
`3: 101      Z Loc [ SurfT_C_K ]`

109: Z=X+F (P34)

`1: 101      X Loc [ SurfT_C_K ]
`2: -273.15  F
`3: 102      Z Loc [ SurfT_C_C ]`

---- Apogee SI-111 Infrared radiometer----\
# 2362 - pointed at canopy near Forest1\
First measure resistnce of the thermistor and calculate sensor body\
temperature

110: AC Half Bridge (P5)

`1: 1        Reps
`2: 25       5000 mV, 60 Hz Reject, Fast Range (same as code 45)
`3: 13       SE Channel
`4: 1        Excite all reps w/Exchan 1
`5: 2500     mV Excitation
`6: 81       Loc [ mV_thrm   ]
`7: 1.0      Multiplier
`8: 0.0      Offset`

111: Z=1/X (P42)

`1: 81       X Loc [ mV_thrm   ]
`2: 82       Z Loc [ 1_mV_thrm ]`

112: Z=X+F (P34)

`1: 82       X Loc [ 1_mV_thrm ]
`2: -1.0     F
`3: 83       Z Loc [ 2_mV_thrm ]`

113: Z=X\*F (P37)

`1: 83       X Loc [ 2_mV_thrm ]
`2: 24900    F
`3: 84       Z Loc [ R_thrm    ]`

114: Z=LN(X) (P40)

`1: 84       X Loc [ R_thrm    ]
`2: 85       Z Loc [ InR_thrm  ]`

115: Z=X\*F (P37)

`1: 85       X Loc [ InR_thrm  ]
`2: 0.001    F
`3: 86       Z Loc [ Scaled_R  ]`

116: Polynomial (P55)

`1: 1        Reps
`2: 86       X Loc [ Scaled_R  ]
`3: 87       F(X) Loc [ SH_Coeffs ]
`4: .001129  C0
`5: .234108  C1
`6: 0.0      C2
`7: 87.7547  C3
`8: 0.0      C4
`9: 0.0      C5`

117: Z=1/X (P42)

`1: 87       X Loc [ SH_Coeffs ]
`2: 88       Z Loc [ SB_Temp_K ]`

118: Z=X+F (P34)

`1: 88       X Loc [ SB_Temp_K ]
`2: -273.15  F
`3: 89       Z Loc [ SB_Temp_C ]`

Measure mV output of thermopile

119: Volt (Diff) (P2)

`1: 1        Reps
`2: 21       10 mV, 60 Hz Reject, Slow Range
`3: 8        DIFF Channel
`4: 90       Loc [ mV_tpile  ]
`5: 1.0      Multiplier
`6: 0.0      Offset`

Calculation of m(slope) coefficient for target temperature calculation.\
Each sensor has unique C0, C1, and C2 values on their calibration sheet.

120: Polynomial (P55)

`1: 1        Reps
`2: 89       X Loc [ SB_Temp_C ]
`3: 91       F(X) Loc [ m_slope   ]
`4: 14222.3  C0
`5: 68.0776  C1
`6: .77405   C2
`7: 0.0      C3
`8: 0.0      C4
`9: 0.0      C5`

121: Z=X\*F (P37)

`1: 91       X Loc [ m_slope   ]
`2: 99999    F
`3: 91       Z Loc [ m_slope   ]`

Calculation of b (intercept) coefficient for target calculation. Each\
sensor has unique C values (again - on calib sheet).

122: Polynomial (P55)

`1: 1        Reps
`2: 89       X Loc [ SB_Temp_C ]
`3: 92       F(X) Loc [ b_inter   ]
`4: -72.4861 C0
`5: -2.25549 C1
`6: 0.24962  C2
`7: 0.0      C3
`8: 0.0      C4
`9: 0.0      C5`

123: Z=X\*F (P37)

`1: 92       X Loc [ b_inter   ]
`2: 99999    F
`3: 92       Z Loc [ b_inter   ]`

Target temperature calculation based on m and b coefficients.

124: Z=F x 10\^n (P30)

`1: 0.4      F
`2: 1        n, Exponent of 10
`3: 93       Z Loc [ Exponent1 ]`

125: Z=F x 10\^n (P30)

`1: .025     F
`2: 1        n, Exponent of 10
`3: 94       Z Loc [ Exponent2 ]`

126: Z=X\^Y (P47)

`1: 88       X Loc [ SB_Temp_K ]
`2: 93       Y Loc [ Exponent1 ]
`3: 95       Z Loc [ 1_SB_4Pow ]`

127: Z=X\*Y (P36)

`1: 90       X Loc [ mV_tpile  ]
`2: 91       Y Loc [ m_slope   ]
`3: 96       Z Loc [ 2_mVxm    ]`

128: Z=X+Y (P33)

`1: 95       X Loc [ 1_SB_4Pow ]
`2: 96       Y Loc [ 2_mVxm    ]
`3: 97       Z Loc [ 3_Sum1    ]`

129: Z=X+Y (P33)

`1: 92       X Loc [ b_inter   ]
`2: 97       Y Loc [ 3_Sum1    ]
`3: 98       Z Loc [ 4_Sum2    ]`

130: Z=X\^Y (P47)

`1: 98       X Loc [ 4_Sum2    ]
`2: 94       Y Loc [ Exponent2 ]
`3: 103      Z Loc [ CanT_K    ]`

131: Z=X+F (P34)

`1: 103      X Loc [ CanT_K    ]
`2: -273.15  F
`3: 104      Z Loc [ CanT_C    ]`

---- HMP45A RH/T sensor ----\

132: Do (P86)

`1: 49       Turn On Switched 12V`

Stabilize sensor

133: Delay w/Opt Excitation (P22)

`1: 1        Ex Channel
`2: 0        Delay W/Ex (0.01 sec units)
`3: 15       Delay After Ex (0.01 sec units)
`4: 0        mV Excitation`

Measure temperature

134: Volt (SE) (P1)

`1: 1        Reps
`2: 24       1000 mV, 60 Hz Reject, Slow Range
`3: 17       SE Channel
`4: 105      Loc [ AirT_For  ]
`5: 0.1      Multiplier
`6: -40      Offset`

Measure relative humidity

135: Volt (SE) (P1)

`1: 1        Reps
`2: 24       1000 mV, 60 Hz Reject, Slow Range
`3: 18       SE Channel
`4: 106      Loc [ RH_For    ]
`5: 0.1      Multiplier
`6: 0.0      Offset`

turn off sensor

136: Do (P86)

`1: 59       Turn Off Switched 12V`

-----Met-One windset - wind speed and direction-----

137: Pulse (P3)

`1: 1        Reps
`2: 1        Pulse Channel 1
`3: 22       Switch Closure, Output Hz
`4: 107      Loc [ WS_For_ms ]
`5: .799     Multiplier
`6: .2811    Offset`

138: If (X&lt;=&gt;F) (P89)

`1: 107      X Loc [ WS_For_ms ]
`2: 1        =
`3: .2811    F
`4: 30       Then Do`

`    139:  Z=F x 10^n (P30)
`     1: 0        F
`     2: 0        n, Exponent of 10
`     3: 107      Z Loc [ WS_For_ms ]`

140: End (P95)

141: AC Half Bridge (P5)

`1: 1        Reps
`2: 25       5000 mV, 60 Hz Reject, Fast Range (same as code 45)
`3: 19       SE Channel
`4: 2        Excite all reps w/Exchan 2
`5: 5000     mV Excitation
`6: 108      Loc [ WDir_For  ]
`7: 712      Multiplier
`8: 0.0      Offset`

142: If (X&lt;=&gt;F) (P89)

`1: 108      X Loc [ WDir_For  ]
`2: 3        >=
`3: 360      F
`4: 30       Then Do`

`    143:  Z=F x 10^n (P30)
`     1: 0        F
`     2: 0        n, Exponent of 10
`     3: 108      Z Loc [ WDir_For  ]`

144: End (P95)

-----Write Data to Final Storage every 30 min-----

145: If time is (P92)

`1: 0        Minutes (Seconds --) into a
`2: 30       Interval (same units as above)
`3: 10       Set Output Flag High (Flag 0)`

146: Set Active Storage Area (P80)\^12982

`1: 1        Final Storage Area 1
`2: 1        Array ID`

147: Resolution (P78)

`1: 0        Low Resolution`

148: Real Time (P77)\^13262

`1: 1110     Year,Day,Hour/Minute (midnight = 0000)`

149: Average (P71)\^25120

`1: 1        Reps
`2: 1        Loc [ batt_volt ]`

150: Average (P71)\^5738

`1: 1        Reps
`2: 2        Loc [ panelT    ]`

151: Average (P71)\^4500

`1: 18       Reps
`2: 3        Loc [ Period1   ]`

152: Average (P71)\^27730

`1: 60       Reps
`2: 21       Loc [ P1_5sm    ]`

153: Average (P71)\^29314

`1: 1        Reps
`2: 100      Loc [ SurfT_T_C ]`

154: Average (P71)\^29457

`1: 1        Reps
`2: 102      Loc [ SurfT_C_C ]`

155: Average (P71)\^1649

`1: 5        Reps
`2: 104      Loc [ CanT_C    ]`

156: Wind Vector (P69)\^30082

`1: 1        Reps
`2: 0        Samples per Sub-Interval
`3: 0        S, theta(1), sigma(theta(1)) with polar sensor
`4: 107      Wind Speed/East Loc [ WS_For_ms ]
`5: 108      Wind Direction/North Loc [ WDir_For  ]`

Controls relay that switches on/off forest radio\
Run table every half hour

-   Table 2 Program

` 02: 1800      Execution Interval (seconds)`

set control port 8 high every 8 hours

1: If time is (P92)

`1: 0        Minutes (Seconds --) into a
`2: 480      Interval (same units as above)
`3: 48       Set Port 8 High`

set control port 8 low 30 minutes later

2: If time is (P92)

`1: 30       Minutes (Seconds --) into a
`2: 480      Interval (same units as above)
`3: 58       Set Port 8 Low`

-   Table 3 Subroutines

End Program

-Input Locations- 1 batt\_volt 1 1 1 2 panelT 1 1 1 3 Period1 1 2 1 4
Period2 1 2 1 5 Period3 1 1 0 6 Period4 1 1 0 7 Period5 5 2 1 8 Period6
17 1 1 9 Period7 5 2 1 10 Period8 17 2 1 11 Period9 5 2 1 12 Period10 17
2 1 13 Period11 1 1 0 14 Period12 1 1 0 15 Period13 5 2 2 16 Period14 17
2 2 17 Period15 1 2 0 18 Period16 1 2 0 19 Period17 1 2 0 20 Period18 1
2 0 21 P1\_5sm 1 1 1 22 P1\_20sm 1 0 1 23 P1\_60sm 1 0 1 24 P3\_60sm 1 0
1 25 P3\_5sm 1 0 1 26 P3\_20sm 1 0 1 27 P2\_5sm 5 0 2 28 P2\_20sm 17 0 1
29 P2\_60sm 5 0 1 30 P4\_5sm 9 0 1 31 P4\_20sm 9 0 1 32 P4\_60sm 17 0 1
33 P5\_5sm 5 0 1 34 P5\_20sm 9 0 1 35 P5\_60sm 9 0 1 36 P7\_5sm 9 0 1 37
P7\_20sm 9 0 1 38 P7\_60sm 17 0 1 39 P5\_5st 5 0 1 40 P5\_20st 17 0 1 41
P5\_60st 0 0 0 42 P7\_5st 0 0 0 43 P7\_20st 0 0 0 44 P7\_60st 0 0 0 45
P3d\_5\_1 1 1 1 46 P3d\_5\_2 1 0 0 47 P3d\_5\_3 1 0 0 48 P3d\_20\_1 1 0
0 49 P3d\_20\_2 1 0 0 50 P3d\_20\_3 1 0 0 51 P3d\_60\_1 1 0 0 52
P3d\_60\_2 1 0 0 53 P3d\_60\_3 1 0 0 54 P1d\_5\_1 1 0 0 55 P1d\_5\_2 1 0
0 56 P1d\_5\_3 1 0 0 57 P1d\_20\_1 1 0 0 58 P1d\_20\_2 1 0 0 59
P1d\_20\_3 1 0 0 60 P1d\_60\_1 1 0 0 61 P1d\_60\_2 1 0 0 62 P1d\_60\_3 1
0 0 63 P4d\_5\_1 1 1 1 64 P4d\_5\_2 1 0 0 65 P4d\_5\_3 1 0 0 66
P4d\_20\_1 1 0 0 67 P4d\_20\_2 1 0 0 68 P4d\_20\_3 1 0 0 69 P4d\_60\_1 1
0 0 70 P4d\_60\_2 1 0 0 71 P4d\_60\_3 1 0 0 72 P2d\_5\_1 1 0 0 73
P2d\_5\_2 1 0 0 74 P2d\_5\_3 1 0 0 75 P2d\_20\_1 1 0 0 76 P2d\_20\_2 1 0
0 77 P2d\_20\_3 1 0 0 78 P2d\_60\_1 1 0 0 79 P2d\_60\_2 1 0 0 80
Pd\_60\_3 1 0 0 81 mV\_thrm 1 3 3 82 1\_mV\_thrm 1 3 3 83 2\_mV\_thrm 1
3 3 84 R\_thrm 1 3 3 85 InR\_thrm 1 3 3 86 Scaled\_R 1 3 3 87 SH\_Coeffs
1 3 3 88 SB\_Temp\_K 1 6 3 89 SB\_Temp\_C 1 6 3 90 mV\_tpile 1 3 3 91
m\_slope 1 6 6 92 b\_inter 1 6 6 93 Exponent1 1 3 3 94 Exponent2 1 3 3
95 1\_SB\_4Pow 1 3 3 96 2\_mVxm 1 3 3 97 3\_Sum1 1 3 3 98 4\_Sum2 1 3 3
99 SurfT\_T\_K 1 1 1 100 SurfT\_T\_C 1 1 1 101 SurfT\_C\_K 1 1 1 102
SurfT\_C\_C 1 1 1 103 CanT\_K 1 1 1 104 CanT\_C 1 1 1 105 AirT\_For 5 0
1 106 RH\_For 9 0 1 107 WS\_For\_ms 9 2 2 108 WDir\_For 17 2 2 -Program
Security- 0000 0000 0000 -Mode 4- -Final Storage Area 2- 0 -CR10X ID- 0
-CR10X Power Up- 3 -CR10X Compile Setting- 3 -CR10X RS-232 Setting- -1
-DLD File Labels- 0 -Final Storage Labels- 0,1,12982 1,Year\_RTM,13262
1,Day\_RTM 1,Hour\_Minute\_RTM 2,Period1\_AVG\~3,4500 2,Period2\_AVG\~4
2,Period3\_AVG\~5 2,Period4\_AVG\~6 2,Period5\_AVG\~7 2,Period6\_AVG\~8
2,Period7\_AVG\~9 2,Period8\_AVG\~10 2,Period9\_AVG\~11
2,Period10\_AVG\~12 2,Period11\_AVG\~13 2,Period12\_AVG\~14
2,Period13\_AVG\~15 2,Period14\_AVG\~16 2,Period15\_AVG\~17
2,Period16\_AVG\~18 2,Period17\_AVG\~19 2,Period18\_AVG\~20
3,panelT\_AVG\~2,5738 4,batt\_volt\_AVG\~1,25120
5,SurfT\_T\_C\_AVG\~100,29314 6,SurfT\_C\_C\_AVG\~102,29457
7,CanT\_C\_AVG\~104,1649 7,AirT\_For\_AVG\~105 7,RH\_For\_AVG\~106
7,WS\_For\_ms\_AVG\~107 7,WDir\_For\_AVG\~108
8,WS\_For\_ms\_S\_WVT\~107,30082 8,WDir\_For\_D1\_WVT\~108
8,WDir\_For\_SD1\_WVT\~108 9,P1\_5sm\_AVG\~21,27730 9,P1\_20sm\_AVG\~22
9,P1\_60sm\_AVG\~23 9,P3\_60sm\_AVG\~24 9,P3\_5sm\_AVG\~25
9,P3\_20sm\_AVG\~26 9,P2\_5sm\_AVG\~27 9,P2\_20sm\_AVG\~28
9,P2\_60sm\_AVG\~29 9,P4\_5sm\_AVG\~30 9,P4\_20sm\_AVG\~31
9,P4\_60sm\_AVG\~32 9,P5\_5sm\_AVG\~33 9,P5\_20sm\_AVG\~34
9,P5\_60sm\_AVG\~35 9,P7\_5sm\_AVG\~36 9,P7\_20sm\_AVG\~37
9,P7\_60sm\_AVG\~38 9,P5\_5st\_AVG\~39 9,P5\_20st\_AVG\~40
9,P5\_60st\_AVG\~41 9,P7\_5st\_AVG\~42 9,P7\_20st\_AVG\~43
9,P7\_60st\_AVG\~44 9,P3d\_5\_1\_AVG\~45 9,P3d\_5\_2\_AVG\~46
9,P3d\_5\_3\_AVG\~47 9,P3d\_20\_1\_AVG\~48 9,P3d\_20\_2\_AVG\~49
9,P3d\_20\_3\_AVG\~50 9,P3d\_60\_1\_AVG\~51 9,P3d\_60\_2\_AVG\~52
9,P3d\_60\_3\_AVG\~53 9,P1d\_5\_1\_AVG\~54 9,P1d\_5\_2\_AVG\~55
9,P1d\_5\_3\_AVG\~56 9,P1d\_20\_1\_AVG\~57 9,P1d\_20\_2\_AVG\~58
9,P1d\_20\_3\_AVG\~59 9,P1d\_60\_1\_AVG\~60 9,P1d\_60\_2\_AVG\~61
9,P1d\_60\_3\_AVG\~62 9,P4d\_5\_1\_AVG\~63 9,P4d\_5\_2\_AVG\~64
9,P4d\_5\_3\_AVG\~65 9,P4d\_20\_1\_AVG\~66 9,P4d\_20\_2\_AVG\~67
9,P4d\_20\_3\_AVG\~68 9,P4d\_60\_1\_AVG\~69 9,P4d\_60\_2\_AVG\~70
9,P4d\_60\_3\_AVG\~71 9,P2d\_5\_1\_AVG\~72 9,P2d\_5\_2\_AVG\~73
9,P2d\_5\_3\_AVG\~74 9,P2d\_20\_1\_AVG\~75 9,P2d\_20\_2\_AVG\~76
9,P2d\_20\_3\_AVG\~77 9,P2d\_60\_1\_AVG\~78 9,P2d\_60\_2\_AVG\~79
9,Pd\_60\_3\_AVG\~80
