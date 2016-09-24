# Sentek EnviroSCAN profiles

These soil sensor profiles are inserted into a buried PVC tube to
measure soil water content and salinity. The sensor profile assembly
consist of a plastic probe, sensors placed at 10cm intervals along the
probe, and an SDI-12 interface (circuitboard) at the top of the
assembly. Sensors are connected to the SDI interface with a ribbon cable
running along the probe. Installation and communication with old
dataloggers are both a bit tricky.

## Installation

#### Standard auger method

This installation is for uniform, fine textured soils. Details
[here](http://www.campbellsci.com/enviroscan). In rocky
mountain soils it is better to opt for the slurry method below (in my
opinion).

#### Slurry method

This installation is suitable for soils in which augering a uniform hole
for the access tube is difficult. This includes rocky, non-uniform soils
such as those found in subalpine forests. A hole slightly larger than
the diameter of the access tube is augered to depth with a standard
bucket auger. Rocks must be broken up and removed with the auger, so if
this is not possible with the larger rocks, the hole will have to be
relocated. Once a suitable hole is augered, it is filled \~1/3 full with
a slurry mixture of grey cement, kaolinite clay powder, and water. A
sealed PVC access tube is then inserted into the slurry and pushed down
to the desired depth, and the slurry is allowed to set around the tube.
The sensor probe is then inserted into the access tube and wired once
the slurry is dry.

In theory, the slurry around the access tube equilibrates with the soil
water content of surrounding soil and allows good measurements of
relative soil water content. This method does not allow accurate
measurements of absolute soil moisture unless extensive calibrations are
done using the slurry and field soil (this sounds like it would be very
difficult in practice).

## Datalogger communication

#### Wiring

Our sensors have the old revision of the SDI interface board (v1.2). At
the top of the board are 5 input/output pins labeled from 1 to 5. Most
pins have broken off and they are now soldered to wires. The terminals
are (in order):

- +12Vin
- not used
- not used
- Ground
- SDI-12 data`

The +12V and Ground wires must be connected to an appropriate power
source (12V/SW12V and G on a Campbell 23x for example) and the SDI-12
data wire must connect to an SDI-12 capable serial port.

#### Datalogger control

Measurement commands are issued with SDI-12 from a serial port. For
example, on a Campbell edlog datalogger, the SDI-12 Recorder instruction
is issued using a control port and an SDI address. If there are multiple
SDI devices on the same line, they may need separate SDI addresses to
work. The sensor then takes measurements at each sensor along the probe
and sends back a scaled frequency measurement and a water content that
is derived from this scaled frequency (WC alone can also be sent).

Edlog program
-------------

==

is a working program for measuring a Sentek probe with 4 sensors using a Campbell cr23x datalogger.`
