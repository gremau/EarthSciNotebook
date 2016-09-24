FIXME

###### Hidden Canyon towers

These towers are responsible for power, aboveground sensor measurements
(meteorological), and communication at the [Hidden Canyon
site](hiddencanyon:sitedescription).

 **There are three total towers at Hidden Canyon:\*\*

` * A solar tower with solar panels, a battery box, and charge controllers. Located in the clearing.`\
` * A met tower with meteorological instrumentation, a datalogger, and a modem and antenna for communication with the lab. Located just east of the solar tower.`\
` * A forest tower with some met instruments, and a datalogger that is connected to the `[`forest`
`soil`
`profiles`](hiddencanyon:soilprofiles)` via 2 multiplexers.`

===== Objectives ====

` - Continuous measurement of air temperature, relative humidity, windspeed and direction, soil and snow surface temperatures, snow depth, net radiation, and incoming and reflected PAR.`\
` - Provide environmental data to support the `[`ecohydrology`
`experiments`](hc_ecohydrology:overview)` at Hidden Canyon.`\
` - Measurement of weather patterns and longer term climatic trends at Hidden Canyon site. `\
` - Comparison of Hidden Canyon research results to results from similar studies at other sites with varying environmental conditions.`\
` - Measure the influence of forest cover on a subset of these measured environmental conditions (Temp/RH, surface temps, wind).`

##### Methods and Instrumentation

Tower descriptions and sensor lists are below. Sensors that have unique
or difficult configurations may have their own instrumentation page
(linked). Greater detail on towers, dataloggers, sensors, and wiring
layouts is tabulated in .

#### Met tower

{{ :hiddencanyon:img\_3847\_scaled\_.jpg?200|Met tower enclosure and
solar tower (background)}} {{
:hiddencanyon:img\_3825\_scaled\_.jpg?235|Instruments on Met tower}}

The Met tower is a mast about 7m tall, with an East/West oriented boom
at 3.7m height and a N/S oriented crossbar at 3.8 m height. The tower is
located in the open, about 16m east and slightly downhill of the solar
tower. Slope angle is 21-22° at the base of the tower. Aspect is 197°
(SSW).

 **Sensors and data collection start dates \*\*

` - Vaisala temp/RH sensor, //Dec 20, 2009//`\
` - Met One windspeed and direction sensor, //Jan 7, 2010//`\
` - Texas Electronics rain gauge, //Dec 20, 2009//`\
` - Upward looking PAR (`[`LI-190`](:instruments:li-190)`), //Nov 11, 2009//`\
` - Downward looking PAR (`[`LI-190`](:instruments:li-190)`), //Jan 25, 2010//`\
` - REBS Net Radiation sensor, //Jan 7, 2010// (day windset started working), //Jan 25, 2010// Negative correction factor changed`\
` - Judd Snow Depth sensor, //Jan 14, 2010//, offset changed to 340cm //Aug 26, 2010//.`\
` - Apogee IR radiometer (snow surface below tower), //Dec 20, 2009//`\
` - Setra atmospheric pressure, //Dec 20, 2009//`

 **Datalogger: \*\*

The datalogger at this tower is a Campbell CR23x called Met1. For more
details see the [Hidden Canyon datalogger
page](hiddencanyon:dataloggers).

 **Communications: \*\*

The Forest1 datalogger powers two radios, and a wireless modem via a
Campbell AM6REL12 every 8 hours. This allows communications between the
Met1 an Forest1 dataloggers and the Base radio, and communications via
the internet with the wireless modem (see [communications
page](hiddencanyon:communicationsystem)).

#### Forest tower

{{ :hiddencanyon:img\_3788\_scaled\_.jpg?200|Forest tower and
enclosure}} The forest tower is a fencepost about 2.5m tall with an
East/West oriented boom at the top of the post. It is located 40.5m east
and downhill of the Met tower. Slope angle is 20-21° at the base of the
tower. Aspect is 205° (SSW).

 **Sensors and start dates \*\*

` - Vaisala temp/RH sensor, //Dec 18, 2009//`\
` - Met One windspeed and direction sensor, //Dec 18, 2010//`\
` - Apogee IR radiometer (Control snow surface temp), //Dec 18, 2009//, fixed EDLOG problem on //Feb 18, 2010//.`\
` - Apogee IR radiometer (Treatment snow surface temp), //Jan 7, 2010//, repositioned on //March 4, 2010//.`\
` - Apogee IR radiometer (Canopy surface temp), //Dec 18, 2009//, repositioned on //Jan 14, 2010//`

 **Datalogger: \*\*

The datalogger at this tower is a Campbell CR23x called Forest1. For
more details see the [Hidden Canyon datalogger
page](hiddencanyon:dataloggers).

 **Multiplexers: \*\*

The Forest1 datalogger is connected to two Campbell AM16/32
multiplexers. Mux1 is uphill of the forest tower and is connected to
soil profiles 1-4. Mux2 is downhill of the forest tower and is connected
to soil profiles 5-8. More detail on this setup is at the [Hidden Canyon
soil profiles](hiddencanyon:soilprofiles) page.

 **Communications: \*\*

The Forest1 datalogger powers a radio via a relay every 8 hours. This
radio communicates with the base radio (see [communications
page](hiddencanyon:communicationsystem)).

#### Solar tower

The solar tower is located in the clearing about 1m east of CP1. It is a
mast 7 m tall with one boom and three solar panels facing south. The
enclosure on this tower contains two charge controllers and some
terminal strips. Two power cables exit the enclosure, one powering the
Met1 datalogger, and one powering the Forest1 datalogger. There is a
battery box with 5 batteries at the base of the mast.

##### Maintenance and data log

See here: <hiddencanyon:mettowerlog_1>.
