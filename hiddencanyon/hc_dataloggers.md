# Hidden Canyon dataloggers

There are two Campbell CR23x dataloggers at [Hidden Canyon](hc_sitedescription.md):

* **Met1** is located on the [met tower](hc_mettowers.md)and it logs meteorological data and powers the [modem and the Base and Met1 radios](hc_communicationsystem.md).
* **Forest1** is located on the [forest tower](hc_mettowers.md)and it logs meteorological data and [soil profile](hc_soilprofiles.md)data (via 3 multiplexers).

Both of these dataloggers are connected via radio to the [communications system](hc_communicationsystem.md).

## Met1

* Current wiring spreadsheet: 
* Current EDLOG program: 

### Sensors (with start date)

- Vaisala temp/RH sensor, *Dec 20, 2009*
- Met One windspeed and direction sensor, *Jan 7, 2010*
- Texas Electronics rain gauge, *Dec 20, 2009*
- Upward looking PAR ([LI-190](/instruments/_instli-190.md)), *Nov 11, 2009*
- Downward looking PAR ([LI-190](/instruments/inst_li-190.md)), *Jan 25, 2010*
- REBS Net Radiation sensor, *Jan 7, 2010* (day windset started working), *Jan 25, 2010* Negative correction factor changed
- Judd Snow Depth sensor, *Jan 14, 2010*, offest changed to 340cm *Aug 26, 2010*.
- Apogee IR radiometer (snow surface below tower), *Dec 20, 2009*
- Setra atmospheric pressure, *Dec 20, 2009*

### Peripherals

- Switch: Campbell A6REL-12 (switches power to modem and radios)
- Modem1: Sierra Wireless RavenXT
- Base Radio: Digi Xbee radio connected to the modem
- Met1 Radio: Digi Xbee radio connected to Met1 datalogger

### Change log

- 8/26/10 - connected A6REL-12, Base radio, Met1 radio, and modem to this datalogger and changed program to v3.

### Old EDLOG Programs

* 

## Forest1

* Current wiring spreadsheet: 
* Current EDLOG program: 

### Met Sensors (with start date)

- Vaisala temp/RH sensor, *Dec 18, 2009*
- Met One windspeed and direction sensor, *Dec 18, 2010*
- Apogee IR radiometer (Control snow surface temp), *Dec 18, 2009*, fixed EDLOG problem on *Feb 18, 2010*.
- Apogee IR radiometer (Treatment snow surface temp), *Jan 7, 2010*, repositioned on *March 4, 2010*.
- Apogee IR radiometer (Canopy surface temp), *Dec 18, 2009*, repositioned on *Jan 14, 2010*

### Soil profile sensors (via MUX1 and MUX2)

see the [soil profile page](hc_soilprofiles.md) for more details

- 12 Decagon EC-TM sensors
- 18 Campbell CS-616/615 sensors
- 6 Campbell 107 thermistors

### Peripherals

- MUX1: Campbell AM16/32B connected to 4 soil profiles
- MUX2: Campbell AM16/32 connected to 4 soil profiles
- Crydom D1D07 relay connected to 5v power and control port
- ForestRadio: Digi Xbee radio connected to RS-232 port

### Change log

- 10/16/2010: New datalogger program (v4) added, rewired MUX 1 & 2, added MUX 3 and profiles 5 & 7 to network. Appears to be collecting data as of 2:30pm.


