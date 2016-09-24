# Western U.S. NRCS data

Collection of environmental data, including met and soils data, from
NRCS, Ameriflux, and other research stations and its processing for
analysis is covered here.

 **See also:\*\* [Overview
        page](west_stationdata:overview), [Data program
        documentation](programdocs), [Data analysis
        log](analysislog_1)

//Start date: 25 Jan, 2010//

## Objectives

` * Gather continuous measurements of soil moisture, soil temperature, weather/climate, snowpack dynamics, and metrics of soil biological activity for western U.S. mountain sites.
` * Quantify spatial variability (by elevation, topography, lat/lon) in climate, snowpack dynamics, SM/ST.
` * Quantify inter-annual variability in climate, snowpack dynamics, SM/ST.
` * Assess the relationships between spatial or inter-annual variability in SM/ST, climate, and snowpack dynamics among sites.`

## Data Sources

### National Water and Climate Center - SNOTEL, SCAN, and Snow Course data

Most data, including SNOTEL (mountain) and SCAN (lowland) automated
station data comes from the National Water and Climate Center. This
division of the USDA's Natural Resources Conservation Service runs the
Snow Survey (Snow Courses), SNOTEL network, and SCAN network and
provides a few online interfaces for accessing this data.

` * `[`The` `NWCC` `station`
`inventory`](http://www.wcc.nrcs.usda.gov/nwcc/inventory)` lists SCAN/SNOTEL sites by state and element (sensor or data type). This provides good inventory and indexing data.
` * `[`Individual` `station`
`sites`](http://www.wcc.nrcs.usda.gov/nwcc/site?sitenum=1140&state=az)` like this one allow generation of element (sensor or data) reports for particular time periods, including historical periods.
` * `[`The` `Snow` `Course` `data`
`portal`](http://www.wcc.nrcs.usda.gov/snowcourse/sc-data.html)` allows access to historical snow measurements. Many of these measurements extend back to the 1950's or earlier, and many snow courses are still measured today. They provide calibration data for adjacent SNOTEL stations.`

### Other (potentially useful) sites

The [Ameriflux
network](http://public.ornl.gov/ameriflux/index.html),
[Fraser Experimental
Forest](http://www.fs.fed.us/rm/fraser/), Tenderfoot? New
Mexico flux gradient?

## SNOTEL and SCAN raw data files

Files are downloaded as .csv (usually), and are often edited using
various [text editing and data file handling
tools](procedures:programming#Text_editing_and_data_file_handling).

#### Soil station inventory files

Files are downloaded from [the NWCC station inventory
site](http://www.wcc.nrcs.usda.gov/nwcc/inventory). The
original column headers are:

` network,station id,start_date,end_date,lat,lon,elev,element,state,county,basin,site_name,site_info_link,cdbs_id,shef_id,gmt_offset,`

Several inventory files, selected using the dropdowns, are useful:

` - Selecting **precipitation accumulation** gives pretty much all SNOTEL and SCAN sites.
` - Selecting **soil moisture and temperature** gives a file containing only sites with soil sensor profiles (SCAN and SNOTEL).`

These inventory files have been put into a master spreadsheet that keeps
track of sites and the data collected for them (see the inventory
directory).

#### Hourly SM/ST data

Files downloaded from individual station sites by specifying download of
hourly wateryear data for SM/ST sensors. One file for each year that the
sensors have been in operation must be downloaded.

Fields in these files: \^ Variable name \^ Measurement \^ Units/Format
\^ Measurement period \^ | Site Id | Site identification number |
integer | - | | Date | Date | yyyy-mm-dd | - | | Time | Time of
measurement | hh:mm | - | | SMS.I-1:-2(-8, -20) | Soil moisture @ -2 in
(or -8in, -20in) | VWC (%) | hourly average | | STO.I-1:-2(-8, -20) |
Soil moisture @ -2 in (or -8in, -20in) | °C | hourly average | |
STO.I-1:0 or STO.I-2:0 | \*\*Calculated values are sometimes present at
odd depths (0) or marked with I-2 (ignore these)\*\* |||

Data collected:
---------------

All datafiles for UT, ID SNOTEL sites with soil profiles.

#### Daily summaries - all sensors

Files downloaded from individual station sites by specifying download of
daily wateryear data for all sensors. One file for each year that the
sensors have been in operation must be downloaded. \*\*Instantaneous
measurements in these files are for 12AM\*\* (data is the same as 12am
files - see below). These files include daily calculated temperatures
(TMAX, TMIN, TAVG).

Fields in these files: \^ Variable name \^ Measurement \^ Units/Format
\^ Measurement period \^ | Site Id | Site identification number |
integer | - | | Date | Date | yyyy-mm-dd | - | | Time | Time of
measurement | hh:mm | - | | WTEQ.I-1 | Snow water equivalent (pillow) |
inches | Instantaneous | | PREC.I-1 | Accumulated Precipitation | inches
| Instantaneous | | TOBS.I-1 | Observed temperature | °C | Instantaneous
| | TMAX.D-1 | Maximum daily temperature | °C | Calculated daily | |
TMIN.D-1 | Minimum daily temperature | °C | Calculated daily | |
TAVG.D-1 | Average daily temperature | °C | Calculated daily | |
SNWD.I-1 | Snow depth (Judd sensor) | inches | Instantaneous | |
SMS.I-1:-2(-8, -20) | Soil moisture @ -2 in (or -8in, -20in) | VWC (%) |
Instantaneous | | STO.I-1:-2(-8, -20) | Soil temp @ -2 in (or -8in,
-20in) | °C | Instantaneous | | SAL.I-1:-2(-8, -20) | Soil salinity @ -2
in (or -8in, -20in) | grams/l | Instantaneous | | RDC.I-1:-2(-8, -20) |
Real dielectric constant (each soil sensor) | unitless | Instantaneous |
| BATT.I-1 | Battery voltage | voltage | Instantaneous | | STO.I-1:0 or
STO.I-2:0 | \*\*Calculated values are sometimes present at odd depths
(0) or marked with I-2 (ignore these)\*\* ||| | WTEQ.I-2 | \*\*Some
sites have additional (backup?) measurements - Ignore these \*\* |||

Note that the calculated values (for temperature) are suspect prior to
hourly recording of measurements (see note below).

Data collected:
---------------

All datafiles for AZ. CO, ID, MT, NM, NV, UT, WY SNOTEL sites.

#### Instantaneous measurement files

Instantaneous measurements for individual or all sensors can be
downloaded hourly, or for every third hour (12AM, 3AM...6PM, 9PM). These
contain instantaneous measurements for any sensors chosen (including
all) at the time period chosen. They do not include summary data (TMIN,
TMAX, TAVG) like the files above).

 **NOTE:\*\* At many snotel sites, true hourly measurements did not
        begin until well after the site was established (mid to late
        90's at many).

## Sensors and calibrations

Soil sensors at these sites are [Stevens
Hydra-Probe](http://www.stevenswater.com/soil_moisture_sensors/index.aspx)
sensors. Some appear to be the analog version of the sensor which
measures soil moisture, temperature, and electrical conductivity. Some
may be the digital version (HydraProbe II), but I'm not sure about
this.SM/ST sensors are generally located at 2, 8 and 20 inch depths (5,
20, 50cm), but there seems to be some variability among sites here. SCAN
sites may have measurements from more depths.

### Soil moisture equation change - Feb, 2010

The NRCS issued a notice about a change in the equation used to convert
sensor output to soil moisture in the winter of 2009/10. This will take
effect for all data, including already collected data, beginning in
February 2010. The change in the equation is documented in an article in
the [Vadose Zone
Journal](http://vzj.geoscienceworld.org/cgi/content/abstract/4/4/1070)((Seyfried,
M.S., L.E. Grant, E.Du, and K Humes. 2005. Dielectric loss and
calibration of the hydra probe soil water sensor. Vadose Zone J.
4:1070-1079)) but it is unclear how this will affect the data already
received for this project. Data currently available on NRCS websites
should be updated with this change.

### Sensor moves/replacements

See the sensor history page (linked on individual SNOTEL site pages) for
detailed info on sensor maintenance, movement, or replacement.

` - Louis Meadow site had sensors moved on 12/15/2003. Apparently sensors at -4 and -8 were moved to -8 and -20 respectively. Not sure if sensors were physically moved, or just renamed in the datalogger output.`

### Other Notes:

` * WVF is volume fraction of water in field moist soil (comparable to percent of field capacity)
` * At least some files start or end with a few lines of data collected at odd intervals (bad data).`

## Data processing and filtering

For info on how the data were quality checked and filtered, see the
[data quality control](data_qc) page.

Programs that load and process the raw data, as well as the outputs they
produce, are documented [here](programdocs). Some of the
development of these programs and results are documented
[here](analysislog_1).

## Older data

Some data was downloaded from the NRCS ftp site with help from Tim
Bardsley, Dana Kuiper, and Maggie Dunklee.

Data from all SNOTEL sites with soil moisture and temperature profiles
installed was obtained from the
[NRCS](http://www.wcc.nrcs.usda.gov/snow/) in the spring of
2009. This included data from 252 sites, including SCAN sites, for the
period from install date to May 29, 2009. Data streams include soil
moisture at up to 3 depths, soil temperature at up to 3 depths, avg air
temp, max air temp, min air temp, snow depth, and snow water equivalent
(SWE). Data were received as .csv files, one for each data stream at
each site, with these fields and formats:

\^ Station ID \^ Date sampled \^ Variable code \^ Value \^ Quality
control flag \^ | \*\*3-4 digit int\*\* | \*\*yyyy-mmm-dd hh:mm:ss\*\* |
\*\*String\*\* | \*\*Float\*\* | \*\*Character\*\* | | 345 | 2003-Sep-06
21:00:00 | WTEQ | -0.3 | V | | 345 | 2003-Sep-06 22:00:00 | WTEQ | -0.3
| V | | 345 | 2003-Sep-06 23:00:00 | WTEQ | -0.2 | E |

Soil moisture and soil temperature files \*\*do not have a QC control
column\*\*. The station ID's are indexed along with their name, state,
elevations, lat/lon, install dates, and other info in the
\*\*soil\_stations.csv\*\* file.
