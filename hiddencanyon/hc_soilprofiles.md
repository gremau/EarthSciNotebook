FIXME

# Hidden Canyon soil profiles

A number of soil moisture and soil moisture/temperature profiles are
replicated throughout the [Hidden Canyon
site](hiddencanyon:sitedescription). They provide continuous
measurement of soil moisture and soil temperature at three depths.
Installation began in the fall of 2009.

//Measurement start date: 11 November, 2009//

 **Relevant links:\*\*

` * These sensor profiles are tied in to the `[`Hidden` `Canyon`
`towers`](hiddencanyon:mettowers)\
` * Plot layouts, snowpack treatments, and profile locations are `[`detailed`
`here`](hc_ecohydrology:overview)\
` * Profile data is analysed using procedures `[`described`
`here`](procedures:sensordata_tips)

## Objectives

` - Record seasonal and interannual changes in soil moisture and temperature at three depths.
` - Provide soil moisture/temperature data to support the `[`ecohydrology`
`experiments`](hc_ecohydrology:overview)` at Hidden Canyon.
` - Measure differences in SM/ST in high and low stand density areas and high and low slope position
` - Measure differences in SM/ST in snowmelt treatment and control plots`

## Methods

{{ :hiddencanyon:hc\_profiles1\_scaled.jpg?250|Installation of Campbell
616 sensors}} Soil moisture and temperature sensor profiles were
installed at [Hidden Canyon](hiddencanyon:sitedescription) in
October of 2009 and 2010. One square meter soil pits were excavated to a
depth of 70-80 cm. Soil was excavated in layers, placed on tarps, and
three sensors were inserted into the vertical face of the excavated pit
horizontally and parallel to the surface of the soil. Sensors were
inserted at 5 cm, 20 cm, and 60 cm depths and the layers of excavated
soil were replaced in order, and compacted using foot pressure. Several
types of sensors are in use, in separate profiles. Four sensor profiles
(1d, 2d, 3d, 4d) measure both soil temperature and soil volumetric water
content using [hiddencanyon:soilprofiles\#Decagon
EC-TM's](hiddencanyon:soilprofiles#Decagon_EC-TM's)
(combination sensors. Four profiles (1,2,3,4) measure soil volumetric
water content only using [\[hiddencanyon:soilprofiles\#Campbell
CS-616's]([hiddencanyon:soilprofiles#Campbell_CS-616's) or
[\[hiddencanyon:soilprofiles\#Campbell
CS-615's]([hiddencanyon:soilprofiles#Campbell_CS-615's)
sensors. Two sensor profiles (5 & 7) have both water content
reflectometers (CS-616s) and thermistors (Campbell 107s) installed in
the same pit. Sensors are multiplexed at three separate Campbell
AM-16/32 multiplexers and are controlled and read by a [Campbell CR23x
datalogger](hiddencanyon:dataloggers) (Forest1).

Multiplexer, datalogger, and sensor connections are documented in .

### Decagon EC-TM's

These sensors are digital. They must be turned on, require a 50ms delay,
and they then output three numbers in serial format --- Soil moisture,
conductivity (always 0 for these particular sensors), and soil moisture.
Serial data is read in through a COM port (Instruction P15 in EDLOG) on
the datalogger. There have been some problems with these sensors failing
at install and the data they give seems to have a small diurnal
oscillation in soil moisture that we can't explain. We are unlikely to
use them again.

Not working:
------------

` * Profile 4d-60cm, Profile 3d-20cm, and Profile 1d-60cm were down from install (roughly) until being replaced on Sept 8th.`

` * Profile 2d-60cm is reading too low (all readings are negative) but the shape of the response seems good. The consensus among the Decagon people is that this sensor is either in an airgap or near a rock and it needs to be excavated and reinstalled. --- //`[`Greg`
`Maurer`](primaryproductivity@gmail.com)` 2010/08/11 12:10//
` `

### Campbell CS-616's

These are working pretty well, even though none of them are new and some
appear to have been in service for a long time. The period is read with
instruction P138 (CS616 Water Content Reflectometer), and then converted
to soil VWC with a polynomial fit (Instruction P55) on EDLOG
dataloggers. They can also be read with instruction P27 (Period
Average). They appear to give more reliable data (no diurnal soil
moisture pattern) than the Decagons do.

### Campbell CS-615's

A number of the sensors installed in the soil moisture profiles are
CS-615's. This was discovered after they were installed. These sensors
have different programming and calibration routines at the datalogger,
and the datalogger program had to be written with multiple loops to
accommodate the mix of 615's and 616's. They are read with Instruction
P27, but the parameters are different, as are the calibration
coefficients (in instruction P55) for converting to soil VWC.

CS-615 sensor locations:
------------------------

` * Profile 1 - 5, 20, and 60cm
` * Profile 2 - 5cm and 20cm
` * Profile 3 - 60cm`

Parameters for reading 615 sensors at the dataloggers
-----------------------------------------------------

` * All 615's are configured with calibration coeffients for low EC soils (< 1.0 dS m`^`-1`^`). C0 = -0.187, C1 = 0.037, C2 = 0.335.`

### Unsolved Campbell sensor problems

` * All Campbell sensors in profiles 1 and 3 gave an intermittent error reading (6999) intermittently for several months after install. Wiring has been thoroughly checked, and the MUX seems to work OK with the Decagons. Mysteriously, around April 30th (day 120), this intermittent problem got MUCH less frequent and the sensors gave mostly good data. We're not sure what changed. Data recorded between the intermittent errors (which was very sparse up until the end of April) is in the expected range for the sensors.  --- //`[`Greg`
`Maurer`](primaryproductivity@gmail.com)` 2010/08/11 12:04//`

` * There is one sensor, Profile 3 - 20cm, that is reading too high, though the shape of the response seems to be normal, but reversed. Check this one's wiring. --- //`[`Greg`
`Maurer`](primaryproductivity@gmail.com)` 2010/08/11 12:10//`

### Sentek Envirosmart Probes

In summer of 2010 several Sentek Envirosmart Probes will be installed.
More to come on this later.

### Multiplexers

` * Profiles 1, 1d, 3, & 3d are multiplexed at Mux 1, a Campbell AM16/32 downhill of the `[`forest`
`tower`](hiddencanyon:mettowers)`.
` * Profiles 2, 2d, 4, & 4d are multiplexed at Mux 2, a Campbell AM16/32B uphill of the `[`forest`
`tower`](hiddencanyon:mettowers)`.
` * Profiles 5 and 7 are multiplexed at Mux 3, a Campbell AM 16/32 at about 48E and 25N.
` * More on wiring and programming for these instruments is in `` and on the `[`Hidden`
`Canyon` `datalogger` `page`](hiddencanyon:dataloggers)`.`

## 2010 Soil profile log

` * CS-615 sensors in Profile 2 began working as of 14 Jan, 2010 (New EDLOG program)--- //`[`Greg`
`Maurer`](primaryproductivity@gmail.com)` 2010/01/15 11:03//
` * Decagon sensors in Profile 4d-60cm, Profile 3d-20cm, Profile 1d-60cm are not working. Tested these three sensors with a direct connection to a datalogger at the sensor leads and they all appear to be dead (-INF signal in Loggernet). --- //`[`Greg`
`Maurer`](primaryproductivity@gmail.com)` 2010/02/19 08:15//
` * Three malfunctioning sensors (4d-60, 3d-20, 1d-60) were replaced Sept 8, 2010. They appear to work.
` * Renumbered site plots and profiles. Plots are 1-6 in order from east to west, profiles are sequential starting downslope in plot 1 (Profile 1), upslope plot 1 (Profile 2), downslope plot 2 (Profile 3), etc... See the `[`experimental`
`design`
`page`](hc_ecohydrology:overview)` for more details on this.
` * Installed new profiles, numbers 5 and 7, in early October. These have Campbell CS-616s and 107 thermistors at each depth.
` * Rewired and reordered sensors at Mux 1 and 2, installed Mux 3 and wired profiles 5 and 7 to it. Forest 1 datalogger was down from Oct 8th to the 15th. 
` * Installed new Forest1 datalogger program (v4) and the new Forest1 measurement scheme became operational at ~2:30pm Oct 16th.
` * Possible loss of data starting around Nov 11, 2010 to Jan 11, 2011. FIXME`

## Maintenance and data log

See here: <hiddencanyon:soilprofilelog_1>
