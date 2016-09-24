# Red Butte Canyon Weather Stations

This document describes the long-term weather stations located in Red
Butte Canyon.

//Originally, this info was taken from /RedButte/RBCWeatherStations.doc
on the project Dropbox, last modified on 11/5/2007. It has been
subsequently changed to reflect recent activity.//

## History

For a history of these stations, begin by reading Ehleringer et al.
1992. Red Butte Canyon Research Natural Area: History, Flora, Geology,
Climate, and Ecology. Great Basin Naturalist 52(2), pp95-121. The
present weather stations have been running since 1982 but are positioned
in the same locations as much older weather stations. At this time, the
historical weather station data (prior to 1982) have not been
aggregated, quality checked, and made available to the public.

## Weather Station Site Metadata

\^ Station \^ Location description \^ Latitude \^ Longitude \^ Elevation
\^ Historical data span \^ Current data span \^ | RB #1 | Biology
Experimental Garden| 40° 46' | 110° 50' |1515 m | 1942 - 1964 | 1991 -
present | | RB #2 | Head of RB Reservoir | 40° 47' | 111° 48' | 1653 m
| 1942 - 1964 | 1982 - present | | RB #3 | Along RB Creek at Brush
Basin | 40° 48' |111° 47' | 1865 m |1942 - 1952 | Retired | | RB #4 |
Along RB Creek 100 m west of Beaver Cyn | 40° 48' | 111° 46' | 1890 m |
1942 - 1971 | 1982 - present| | RB #5 | Parleys Fork 100 m above inlet
to RB Creek | 40° 47' | 111° 48' | 1753 m | 1942 - 1956 | Retired | | RB
#6 | Top of Elk Fork | 40° 49' | 111° 46' | 2195 m | 1946 - 1971 | 1982
- present | More information on geology, hydrology, ecology, vegetation,
and other aspects of the canyon can be found at the [Red Butte Canyon
Research Natural Area website](http://redbuttecanyon.net/).

## Recent Status of the Stations

Weather stations 1,2,4, and 6 are currently running. All four collect
daily data for temperature, relative humidity, wind speed, and rainfall.
Weather station 1 also collects data every ten minutes for all above
mentioned sensors as well as for wind direction and photosynthetically
active radiation (PAR).

Log books
---------

Log books are maintained for each weather station and, as of 11/5/2007,
these were located in ASB room 510 in the eastern most cubicle. These,
however, only extend back to 2000 despite efforts to locate any
historical documentation of these stations. Each log book has a copy of
a topo map with the approximate location marked.

Online maintenance log
----------------------

There is an up-to-date [maintenance log
here](redbutte:rbweather_log).

Recent sensor history (&gt;1982)
--------------------------------

The begin date of sensors on the current weather stations is shown here.
Data could be present up to present, except for occasional gaps in the
record. Some of this info comes from the README.TXT file in the
CurrentData folder of the RBWS Dropbox.

` * Weather station 1:
`   * 02 Apr, 1992 - Begin air temp and precip sensors
`   * 30 Jun, 1995 - Begin wind sensor
`   * 08 Mar, 2000 - Begin RH and vapor pressure sensors
`   * Jun 2004 - Order of column headings changes, begin hourly data output
`   * 22 May, 2005 - Change hourly data output to 10 minute data output, add PAR sensor
` * Weather station 2, 4, 6:
`   * 11 Aug, 1982 - Begin air temp, wind speed, PAR(?), and vapor pressure ( :!: see note above about problems with vp) sensors
`   * 01 Jun, 1991 - Light measurements seem to end around this time for all stations.
`   * 07 Apr & 14 May, 1992 - Begin WS2 & 4 precip sensor
`   * 26 Apr, 1993 - Begin WS6 precip sensor.
`   * June 2004 - Order of column headings change`

Missing data
------------

` * **Oct 29, 2007 -> May 26, 2009 (all data, WS2, 4, 6) ** - :?: The last data collection prior to Fall 2011 appears to have been in late 2007. Is there a missing datafile between these dates? Was available memory on the storage module exceeded?
` * **Nov 10, 2012 -> May 31, 2013 (all data, WS4, 6)** - The datalogger programs were erased, probably during a power outage. This is a hard lesson that programs need to be loaded on replacement storage modules (see `[`here`](instruments:cr10dataloggers#Preventing_data_loss)`).`

## Current Data

These data are made available to the general public at
<http://ecophys.utah.edu/download/Red_Butte_Weather/>. Some summary data
is viewable on the [RBC website](http://redbuttecanyon.net/)

Currently, the daily data for all weather stations for all years are
stored in a single file called “RBWSall\_yymmdd.txt” where the yymmdd is
the most recent data collected. This daily file is also saved as an
excel file that can be found online. Historically, the data were saved
by year. These data can be found in an archived folder online as excel
files in their original state
(http://ecophys.utah.edu/download/Red\_Butte\_Weather/YearlyDataFiles/).
After compiling the data for all years and all stations into one file
and plotting all data, it was discovered that all relative humidity data
(or vapor pressure as it were) were logged incorrectly between 1992 and
2000. These data have been removed from the currently updated data file.
Peruse the “Quality Control of Web Files” folder located in the project
Dropbox for more on this issue.

## Equipment and maintenance procedures

Weather stations are visited twice yearly (spring and fall), or more
often as necessary. As of 3/5/2012, a tool box containing all necessary
storage modules, keypads, tools and manuals could be found in the
Bowling Lab, fourth floor of ASB.

#### Station Description

Each weather station consists of a tripod, enclosure, Campbell CR10 (or
CR10x at WS1) datalogger, solar panel, battery/power supply, storage
module, and a number of sensors (which vary slightly between sites).

#### Site Visit Protocol

 **Materials list\*\*

` * A tested, empty storage module for each station. Make sure it has the appropriate datalogger program loaded into location 8.
` * CR10KD keypad
` * Voltage/Multimeter for testing solar and battery voltages.
` * Labeling tape and sharpie for labeling modules as they are swapped out.
` * Screwdrivers, including a small standard (Campbell issue ones are easy to find)
` * Electrical tape
` * Any sensor hardware that needs to be replaced
` * Extra serial cable (blue, three ended ones)`

Upon visiting each site, one should write the date of visitation in the
log book along with the datalogger time, day of year, and year. With the
keypad plugged in, press “\*5” to view the time, then press “A” to view
the day of year, then “A” to view year. One should also write down all
currently measured values by pressing “\*6” and then “A” to advance
through each value. Once the integrity of the station has been
established by visual inspection and datalogger inspection, remove the
existing storage module and replace it with one that has been erased and
tested in the lab.

 **//IMPORTANT NOTE//\*\* - Remember to load the weather station
        program into location 8 of the replacement storage module. This
        will keep the datalogger from forgetting its program after a
        power outage. See
        [here](instruments:cr10dataloggers#Preventing_Data_Loss).

Technical details on working with these dataloggers and storage modules
can be found [here](instruments:cr10dataloggers).

#### Datalogger Programs

The current programs running on each weather station can be found on the
project Dropbox at: RedButte/CR10\_Programs/Current Programs. One can
also obtain the program straight from the datalogger by dumping it to
the storage module using the appropriate keystrokes…see datalogger
manual.

#### Data Reduction

After all storage modules have been collected, they should be downloaded
using some version of Campbell Scientific software (currently
LoggerNet). All data should be plotted to check for integrity before
pasting into the “RBWSall\_yymmdd” file and uploading to the web.
