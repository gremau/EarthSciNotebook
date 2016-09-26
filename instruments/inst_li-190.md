# Li-Cor LI-190 PPFD sensors

These sensors measure PAR, photosynthetically active radiation
(wavelengths from 400-700 nm) as photosynthetic photon flux density
(PPFD). PPFD is typically measured in μmol s^-1^ m^2^.

## Output, wiring, and multipliers

These sensors output μA across two leads and a multiplier is used to
relate the μA signal to μmol s^-1^ m^2^. Multipliers are typically in
the range of -140 to -170 μmol s^-1^ m^-2^ per μA. The two leads are a
bare shield (positive) and a center conductor (negative). This output
can be converted to mV (which is read by Campbell dataloggers) using a
resistor as long as the multipliers are also converted via Ohm's law. A
shunt resistor (roughly 600 Ohms) is placed either between the
datalogger terminals or across the leads using an adapter supplied by
Li-Cor.

Wiring to Campbell dataloggers
------------------------------

\^ Diff H | Li-Cor Shield (Pos), resistor | \^ Diff L | Li-Cor center
conductor (Neg), resistor, ground jumper | \^ gnd | ground jumper |

 **Note:** Li-Cor recommends connecting the wires in the reverse
        way (Pos-->Diff L, Neg-->Diff H) to reduce interference,
        but this gives only negative values on a Campbell CR23x, even if
        the multiplier is entered as a negative value in the
        datalogger program.

Converting the multiplier to mV
-------------------------------

μA current output can be converted to mV using Ohm's law (Voltage =
Current \* Resistance). Multipliers are given as -μmol s^-1^ m^2^ per
μA. A resistor has a voltage in Ohms. The steps to convert to μmol s^-1^
m^2^ per mV are:

- Convert multiplier (//mult//) to μA/1000μmol: //1000μmol/mult//
- Convert multiplier from μA to A: //mult * 1A/10`^`6`^`μA//
- Change amps to volts: //mult * R// (R = resistance of shunt resistor in Ohms)
- Multiplier is now in //V/1000μmol s`^`-1`^m`^`2`^`//
- Change multiplier to mV: //mult * 1000//
- Reciprocal of this number(//1000/mult//) is the multiplier in //μmol s`^`-1`^m`^`-2`^`/mV//
- In short: //mult/0.001A*R//`

 **Note:** Li-Cor and Campbell recommend a 604 Ohm resistor.
        There may be problems especially with higher resistances.

## EDLOG instructions

These sensors are generally read using code like this:

<code>

Measure UPWARD looking Quantum sensor - Q27246\
Bridged with a 604ohm resistor to convert uA to mV

39: Volt (Diff) (P2)

`1: 1        Reps
`2: 41       10 mV, 60 Hz Reject, Fast Range
`3: 5        DIFF Channel
`4: 30       Loc [ PAR_Up    ]
`5: 1.0      Multiplier
`6: 0.0      Offset`

Set negative values to zero

40: If (X&lt;=>F) (P89)

`1: 30       X Loc [ PAR_Up    ]
`2: 4        <
`3: 0.0      F
`4: 30       Then Do`

   41:  Z=F x 10^n (P30)
    1: 0        F
    2: 0        n, Exponent of 10
    3: 30       Z Loc [ PAR_Up    ]`

42: End (P95)

Convert mV to umoles m\^-2 s\^-1 using converted multiplier

43: Z=X\*F (P37)

`1: 30       X Loc [ PAR_Up    ]
`2: 243.112  F
`3: 30       Z Loc [ PAR_Up    ]`

~~~

## Deployed sensors

\^ Serial no. \^ Location \^ Measurement \^ μA Multiplier \^ Resistor \^
mV Multiplier \^ | Q27246 | Hidden Canyon - Met tower | Upward looking
PPFD | -146.84 | 604Ω | 243.112 | | Q33398 | Hidden Canyon - Met tower |
Downward looking PPFD | -158.23 | 560Ω | 282.553 |
