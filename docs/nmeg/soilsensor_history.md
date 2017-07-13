# Site soil sensor histories

Note that I am using the period data for CS616 output (in uSeconds) at sites where this is available.

## GLand

### 2007-06-05 (First TOA5)
* 23 SWC (`cs616_wcr(x)` and 23 Tsoil (`soil_water_T(x)`) headers.
* `soil_water_T(x)` fields seem to be some kind of artifact - the values are scaled right, but they seem to be logging wrong (usually they are all the same).
* There is a `Tsoil_Avg` column in TOA5 data that appears to represent surface soil temperature.
* There may be some confusion between SWC_O3_37.5 and SWC_O3_52.5 sensors - check.

### 2008-08-21
*  1 CS616 fixed

### 2009-02-20
*  Program change
* Stopped reading the 1 extra CS616
* `cs616` headers changed to `(x,y)` format
* Added HFP and TCAV measurements
* Still no Tsoil measurements except `SoilT_Avg`

### 2009-07-15
 *  20 thermocouples were installed  at the site
* Headers are `mux25t_signal_Avg(x)`
* The depths are approximately the same as the CS616s, except that there are no sensors at G3 37.5 and 52.5

### 2009-08
* Fire at the site. CS616 and TCs went to NAN

### 2010-2-24
* Thermocouple multiplexer turned on and TC measurements appear to be working again shortly after this.

### 2010-05-12
*  20 Thermocouples and 18 new echo EC5 sensors installed in 4 pits.
* Thermocouples buried at all 5 depths in each pit, but there are no 52.5cm echo probes in the 2 Open pits.
* Note that the TC headers did not change from `mux25t_signal_Avg(x)`, which is problematic.
* There are also 4 "dummy" columns, which don't seem to be working.

### 2011-3-10
* Echo probes rewired so that Grass1 and Open 1 have all 5 depths and Open2 and Grass2 have only 2.5 to 37.5cm depths.

### 2011-3-23
* 20 CS616s were installed in the 4 pits alongside the Echo probes and TCs, but they are not read until June.

### 2011-06-09 to 2011-07-27
* New programs to read the CS616 probes, and there was some downtime during this changeover.
* Echo probes in Open pits were not read and headers disappeared after this change.
* CS616s were briefly read into `mux_soil_wcr(1-20)` headers (3 days), then into `swc_open1_depthincm_Avg`.
* Both of these headers persisted after July, but only the `swc_...` have data.

### 2012-08-09
 *  Program change that reduced soil measurement cycling from 5min to 30min frequency.

### 2014-01-16
 *  New program with new headers: `SWC_G1_2p5_Avg`, `SWC_echo_G1_2p5_Avg`, `SoilT_G1_2p5_Avg`

#### 2014-01-17 and 2014-02-17 (2 TOA5 files)
* Tsoil headers are messed up. There are no O3 and G3 pits and the headers are mixed up with the current ones, so these need to be renamed

## JSav

### 2007-05-04 (First TOA5)
*  No SWC or SoilT data.

### 2007-08-31
*  New program - SWC and Tsoil headers present
    * 20 Tsoil sensors logging under `soilT_Avg(x)` (but there are 28 headers), VWC logging under `Period(X)` and `VWC(X)`, but both are NANs
* There was a gap in the data between 8/6 and 8/31

### 2007-09-24
* Now the SWC sensors are working (logging to `VWC(X)`).

### 2008-02-25
* SWC headers changed to `cs616_wcr(x)`, but no data logged yet.
* There are also `soil_water_T(1)` headers, but these also have no data, and may just be an artifact.

### 2008-03-31
* Data is now logging into `cs616_wcr(x)` and `soil_water_T(x)` fields - data look similar but are scaled differently (not sure what the `_T` field is)
* Actually I think, in this case the`_T` field is calculated VWC, while the `cs616_wcr(x)` field is the period.

### 2008-06-10
* SHF plates installed

### 2008-12-18 to 2009-02-02
* Soil sensors down for a while here

### 2009-07-08
* There has been a changeover in soil data and probe locations
 * Tsoil headers changed to `SoilT_J1_2.5_Avg`
* Unfortunately the period headers `cs616_wcr(x)`, stayed the same, but now refer to different locations. We'll have to change the old ones to `_old` in the code
* The calculated VWC headers changed to:`SWC_J1_2.5`

### Summer 2011
* Intermittent problems with SWC sensors (recording NAN).

### 2011-08-11
* MUX replaced and seems to have fixed problem.

### Spring 2012
* More intermittent CS616 problems

### 2012-04-27
* CS616s removed from CR5000 and placed on a CR1000 in the same box.
    * `swc_j1_2.5_avg` headers are calculated VWC,  `PA_uS_Avg(1-18)` are the cs616 periods
    * These data come in on separate TOA5 files that are in the `soil` directory.
* Headers disappear from CR5k TOA5 files at this point

### 2014-01-10
* Header changes for CR5k
    * `sap_Avg(x)` to `sap_J1a_Avg`
    * `open_north_Avg` to `shf_open_north_Avg`
    * Added soil CO2 measurements

### 2014-01-17
* Header changes affecting the CR1000 soil moisture datalogger
    * cs616 headers changed to `SWC_O1_2p5` format

### 2014-02-25 to 2014-02-27
* Reinstalled CS616s in new pits (see new headers in format `SWC_J1_2p5_Avg`, `SoilT_J1_2.5_Avg`)
* All CS616s are on the CR5000 again
* Soil heat flux plates reinstalled in 4 (?) pits (3 pits in data headers).
* TCAVs added in similar pits as well.

### 2014-03-28
* Dug up and reinstalled CS616 and Tsoil at 5, 10, 30 cm. Headers changed on 4/15 (possibly earlier)


## SLand

### 2007-05-30 (first TOA5)
* 21 `soil_water_T(1)` and 21 `cs616_wcr(x)` headers, but they don't seem to be functioning correctly.
* Not sure what depth/location that 21st SWC and Tsoil reading is from

### 2007-07-05
* cs616's are functioning, but sensors 12 and 13 are all NANs
* `soil_water_T` sensors are not giving reasonable data and all sensors are identical.
* There is a `Tsoil_avg`column that looks correct.

### 2009-02-20
* New program: 22 SWC sensor columns with `soil_water_T_Avg(1)`	and `cs616_wcr_Avg(x)` headers
* Now there are 6 heat flux plates

### 2009-03-31
* At this point some rewiring was done on the AM16/32 Mux where the CS 616s are connected
* It seems that there were a couple problems:
    * There are only 20 probes, but 22 are being output by the datalogger program
    * Pit O2 sensors are wired out of order at the MUX, so they have been logged in the wrong headers
    * Not sure what to do about this yet

### 2009-06-24
* 20 thermocouples wired in to AM25t mux - reading into `mux25t_signal_Avg(1)` headers
* Old thermocouple headers and data still present, but still garbage.

### 2012-08-09
Program changes: 
* Tsoil now read into `soilt_S2_52.5_Avg` headers.
* CS616s now read every 30 minutes.

## New GLand

### 2009-08-06 (first TOA5 file)
* There are 20 CS616s and 20 Tsoil sensors with headers: `cs616_wcr(20)`,  `SWC_g1_2.5` (calculated VWC - not used), and `SoilT_g1_2.5_Avg`

### 2010-02-24
* Header changes for SWC to `cs616_wcr(1,1) `, `SWC_` (calculated values) headers disappeared.

### 2010-03-12
* 10 of the CS616s stopped being logged - Only Grass1 and Open1 probes are now being measured
* Order of measurements changed to G1 O1 G2 O2 for Tsoil

### 2010-03-26
* New CS616s were added and wired in the G1 O1 G2 O2 order, but it doesn't look like they are being logged yet.

### 2010-05-05
* Wiring continues to change, but it doesn't seem to affect the TOA5 files.
* Supposedly TC order is G1, O2, O1 G2

### 2010-05-12
* Further rewiring: Supposedly CS616 and TC order is now G1, G2, O1, O2.
* Headers haven't changed

### 2010-05-28
* New program that should now measure new CS616s and thermocouples in the order they are actually wired (see above).
* It may be worth swapping headers in the processing code to account for mistaken probe identity over the last 2 months.

### 2011-06-23
* New program for new TCAV added (installed on 5-24 - in open pit)

### 2014-01-17
* Some header changes (fairly minor)

## PJ

PJ is different - soil, sapflow, and CO2 data are logged by a separate CR23x at the site. Data from this logger is periodically downloaded and saved.

###2007-11-09 (first TOA5)
* No soil water or temperature measurements yet.

### 2008-06-19
* New headers for Echo probes and Soil T arrive, but values are invalid.
* 24 Echo probes: `echo_wcr(x,y)`
* 25 Tsoil probes: `soilT_Avg(x)`

### 2008-08-12
Values finally valid for Echo probes and Tsoil on main logger (fixed by someone - in logbook).

* I still don't know anything about the pit structure/depths for these SWC or Tsoil probes

### 2009-03-22
Thermocouples installed, not logging yet

### 2009-05-12
* TDR probes installed and connected to CR23X
* Soil CO2 probes wired in
* Heatflux plate locations noted.
* Soil measurements on the cr23x begin logging at this date. Data for 2009-2013 are in cr23x compilation files originally assembled by Laura Morillas. Find these in the "yearly_cr23x_compilations" direcory

### 2009-06-17
Echo, Tsoil headers removed from main datalogger (data was junk for the past while...)

### 2013-07-12
IRT sensors added to main datalogger

### 2014-01-01
cr23x data now comes in as monthly files in the "cr23x_files" directory

###2014-01-10
New program to main datalogger includes some header changes (but no soil sensors)

### 2014-03-21
Sent new program to main datalogger

### 2014-03-26
Sent new program with added IRT measurements

## PJ_girdle

PJ_girdle also has soil, sapflow, and CO2 data are logged by a separate CR23x at the site. Data from this logger is periodically downloaded and saved.

###2009-02-23 (first TOA5)
* No soil water or temperature measurements on main datalogger.

### 2009-04-28
* TDR probes installed and connected to CR23X
* Soil CO2 probes wired in
* Heatflux plate locations noted.
* Soil measurements on the cr23x begin logging at this date. Data for 2009-2013 are in cr23x compilation files originally assembled by Laura Morillas. Find these in the "yearly_cr23x_compilations" directory

### 2009-05-28 to 2009-06-09
Problems with cr23x data - many sensors not reading.

### 2013-07-03
NDVI and IRT sensors added to main datalogger

### 2014-01-01
cr23x data now comes in as monthly files in the "cr23x_files" directory

###2014-01-10
New program to main datalogger includes some header changes (T, RH, flux vars, but no soil sensors)

### 2014-03-26
Sent new program to main datalogger adds a few measurements (Wood psychrometers?)


## PPine

PPine soil data were logged by....

###2006-08-30 (first TOA5)
* No soil water or temperature measurements yet.

### 2006-11-18
* 4 CS107 thermistors were added - presumably these are measuring the soil?

### 2009-05-22
3 new soil heat flux measurements added (`shf_Avg(1-3)`)

### 2010-10-07
* TCAV and Hukesflux shf installed

### 2013-12-28
New soil data headers appear and major new header changes begin

### 2014-01-03
Some minor rearranging of sensor order in output

### 2014-01-09
SWC and Tsoil (107) measurements disappear

### 2014-05-23
SWC and Tsoil (107) measurements reappear in a slightly different order

## MCon

MCon soil data were logged by....

###2006-08-31 (first TOA5)
* No soil water or temperature measurements yet.

### 2006-12-04
* 4 CS107 thermistors were added - presumably these are measuring the soil?

### 2009-06-01
3 new soil heat flux measurements added (`shf_Avg(1-3)`)

### 2010-06-18
* TCAV and echo probe installed (`echo_h2o_Avg` & `TCAV_Avg`)

### 2013-11-12
Site rebuilt after the fire. Now logging Tsoil, SWC,  soil CO2 and new soil heat flux plates/TCAVs

### 2014
Some minor rearranging of sensor order in output, and minor header changes
