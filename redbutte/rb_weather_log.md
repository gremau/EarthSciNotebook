## Red Butte Weather Station Logbook (Fall 2011 to present)

Maintenance log and visits to [Red Butte weather stations](redbutte/rb_weatherstations.md):

(also see:)

**2-03-2014**

* Modified new WS4 file (original data in WS4_140115_orig.dat):
  * Changed errors (6999, -6999) to NaN
  * Removed lines that were clear errors and changed dates back to 2013/14 (lines 174-end)
* Modified new WS6 file (original data in WS6_140115_orig.dat):
  * Changed errors (6999, -6999) to NaN
  * Added a column filled with 6 that is missing (a glitch in the new program).
  * Removed a day that had a duplicate record (day 325)
  * Removed lines that were clear errors and changed dates back to 2013/14 (lines 176-end)
* Plotted the data collected on 1/11/2014 and 1/15/2014
  * **WS1** (in the garden)
    * There was a power outage on day 341 (Dec 7, 2013) and all data is missing after that.
    * T/RH = new sensor seems to be working fine
    * Wind sensor 1 = still not working
    * Wind sensor 2 = ok, and this has windspeed and wind direction
    * Rain gauge = ok
    * PAR = ok (ten minute only)
    * Battery = ok? I suspect the battery is not functioning because nighttime periods are not recorded (no solar panel input?)
  * **WS2** (by the reservoir)
    * T/RH = ok
    * Wind sensor = New sensor working fine
    * Rain gauge = still ok
    * Battery = losing capacity, low and erratic voltages - needs to be replaced.
  * **WS4** (halfway up canyon)
    * There was a power outage that reset the date around Nov 19, 2013 and it looks like data resumed a bit in early Jan (2014).
    * T/RH = ok
    * Wind sensor = OK
    * Rain gauge = not working.
    * Battery = losing capacity, low and erratic voltages - needs to be replaced.
  * **WS6** (top of Parleys fork)
    * There was a power outage that reset the date around Dec 3, collection resumed, then stopped around Jan 1, 2014.
    * T/RH = ok
    * Wind sensor = ok
    * Rain gauge = ok
    * Battery = losing capacity, low and erratic voltages - needs to be replaced.
* **TO DO:**
  * Check WS1 and replace battery (probably)
  * Fix WS6 program (missing fourth column in data output should be WS #)

**1-20-2014**

* Downloaded data from all storage modules and uploaded to Dropbox
* Storage modules are cleared,tested, and have programs loaded.

**1-15-2014**

* Pulled storage module from WS4 and WS6
* WS 4 initially seemed to be unresponsive, but after testing voltage it again seemed fine.
* Set the clocks for both.
* All 4 stations have modules with the program loaded in location 8.

**1-11-2014**

* Pulled storage module from WS1 and WS2
* WS1 seemed to not be collecting data at the time, so I reloaded the program and it then seemed alright.

**7-6-2013**

* Replaced wind sensor at WS2 with a replacement from an Ehleringer storage cabinet. Seems to work fine (Met One 014C).
* Sensor with the broken bearing was labeled and put back in the Ehleringer cabinet where the replacement came from.

**6-7-2013**

* Replaced T/RH sensor on WS1 with an HMP45AC that susan found.
  * I don't know much about this sensor (when it was last calibrated, etc.), and I used the standard multiplier and offset (in Campbell manual).
* Uploaded the new datalogger program to read this sensor - seems to be working
  * The new program is in the project Dropbox (130606 version).
* Swapped the storage module to get data from 5-23 to today.
  * The file for this period is in the Dropbox, and the data haven't been added to the aggregated files yet.


**5-31-2013**

* Visited WS1
  * The Vaisala HMP35 is broken - one wire lead for the thermistor is sheared off.
  * Temporarily put an old HMP35 (found at garden) on WS1 and removed the current one for inspection.

* Visited WS4 & 6
  * Installed new storage modules
  * Transferred datalogger programs from new modules to dataloggers
  * Reset clocks
  * Data is being collected again at these sites, and future power outages shouldn't cause a problem (programs are in location 8 in the SMs).

**5-29-2013**

* Changed the date for all WS6 data files (that I have collected)
  * I did this based on storage module dates - so I know the start/stop dates for each file
  * As usual - there are `_orig` files in the directory that haven't been changed
* Plotted the data collected on 5-3 and 5-23
  * **WS1** (in the garden)
    * There was a power outage that reset the date over the winter - I fixed this in the datafile (and there is a `_orig` version saved).
    * T/RH = Seems to have broken on 1-5-2013. It is reading a negative number all the time
      * This affects the vapor pressure measurements also
    * Wind sensor 1 = still not working
    * Wind sensor 2 = ok, and this has windspeed and wind direction
    * Rain gauge = ok
    * PAR = ok (ten minute only)
    * Battery = ok? (:!: This is also reading ~-46 like the T sensor, but I checked it with a multimeter on 5-23-2013 and it was ok - ~13V)
  * **WS2** (by the reservoir)
    * T/RH = ok
    * Wind sensor = Data are flat for the last 1-2 months. Dave E confirms that the sensor has frozen up (bearing?) and it will need to be replaced.
    * Rain gauge = ok for the last year, though it looks like it had problems before that
    * Battery = ok (still losing capacity, but voltage is > 12)
  * **WS4** (halfway up canyon)
    * There was a power outage that reset the date over the winter
    * Only a few days of data were collected - all sensors looked ok in this short time, except maybe the rain gauge.
  * **WS6** (top of Parleys fork)
    * There was a power outage that reset the date over the winter.
    * Only a few days of data were collected, and data look ok in this short time.
    * The date is wrong for this WS, and the last few datafiles - this was adjusted using dates of collection.
    * :!: NOTE that there is a `_orig` file with unchanged data (datalogger dates say 2004).
* **TO DO:**
  * Swap storage modules for WS2-6 with modules that have programs loaded in location 8.
    * Load these on to 4 & 6 after they are swapped
  * Test and replace T-RH unit on WS1

**5-23-2013**

* Revisited WS1 and WS4.
* Cut the lock off of WS1 (never found the key), and swapped the storage module.
* There are some problems with WS1 data.
  * There was a power outage that reset the date over the winter - I fixed this in the datafile (and there is a _orig version saved).
  * Data from the temperature sensor is bad and it is affecting vapor pressure measurements.
  * The battery voltage is reading ~-46 - this may be related to the temperature problem.
* Checked the WS4 battery and solar panel voltages and downloaded the running program from the CR10.
  * Battery and solar panels seem fine.
  * The running program looked invalid - was probably erased in a power outage.
* REMEMBER - When swapping out modules, store the datalogger program in location 8 (see [here](instruments:cr10dataloggers#Preventing_data_loss)).

**5-3-2013**

* Visited WS2, 4, & 6 to swap storage modules
* WS4 & 6 were not collecting data, and appeared to have lost power (and their programs)
  * The data collection stopped soon after the fall 2012 visit.
  * WS6 Still thinks it is 2031 - need to reset clock
* WS2 seems OK.
* WS1 was was inaccessible because the key was missing from the usual place.

**1-8-2013**

* Went to WS1 (Garden) and downloaded all data (Austin needed early Nov. data)
* Reset clock on datalogger - it had reset itself to 4 years earlier for some reason. Date of this change was sometime after the last collection (early Nov).

**11-2-5-2012**

* Visited weather stations 1-4 and swapped out storage modules.
* Took photos and checked wiring.
* Plotted data
  * **WS1** (in the garden)
    * T/RH = ok
    * Wind sensor 1 = not working
    * Wind sensor 2 = ok, and this has windspeed and wind direction
    * Rain gauge = ok
    * PAR = ok (ten minute only)
    * Battery = ok? (:!: Big drop in voltage, but everything seems to be working ok - not sure I believe the drop)
  * **WS2** (by the reservoir)
    * T/RH = ok
    * Wind sensor = ok
    * Rain gauge = ok for the last year, though it looks like it had problems before that
    * Battery = ok (still losing capacity, but voltage is > 12)
  * **WS4** (halfway up canyon)
    * T/RH = ok
    * Wind sensor = ok
    * Rain gauge = looks like my fix helped, but it may be down again
    * Battery = capacity is better now, but there may be a bad connection and a slow decline in capacity.
  * **WS6** (top of Parleys fork)
    * This datalogger is having problems, looks like a short may be resetting the date. Most of the data seems intact though.
    * **NOTE** that I doctored the data file (using my best judgement) to remove bad data. There is a raw data file marked `_orig` on the data download site that contains the un-doctored data. Missing or removed data are marked as "NaN" in all other files.
    * T/RH = ok
    * Wind sensor = ok
    * Rain gauge = ok
    * Battery = battery capacity back up to 12v? I think there must be a short somewhere.

**4-9-2012** Plotted 4/4 weather station data today:

* **WS1** (in the garden)
  * T/RH = ok
  * Wind sensor 1 = not working
  * Wind sensor 2 = ok, and this has windspeed and wind direction
  * Rain gauge = ok
  * PAR = ok
  * Battery = ok (losing capacity?)
* **WS2** (by the reservoir)
  * T/RH = ok
  * Wind sensor = ok
  * Rain gauge = ok for the last year, though it looks like it had problems before that
  * Battery = ok (losing capacity?)
* **WS4** (halfway up canyon)
  * T/RH = ok
  * Wind sensor = ok
  * Rain gauge = still broken, but may have been fixed at last visit
  * Battery = abruptly lost capacity (down to ~10V), seems to power the sensors though
* **WS6** (top of Parleys fork)
  * Datalogger needs time reset (thinks it is 2003)
  * T/RH = ok
  * Wind sensor = ok
  * Rain gauge = ok
  * Battery = low capacity (down to 9-10V), seems to power the sensors though

**4-4-2012**

* Visited weather stations 1-6 and swapped out storage modules.
* Did some taping of wiring at weather stations 2 and 4 (insulation on wires is cracking)

**11-28-2011** - Greg and Susan visited WS6

* Uploaded WS6_111122.dld program from the laptop
* Verified that all sensors were working - all were, including the T/RH and precip gauge.
* Replaced T/RH sensor shelter with a new one and realligned/reattached precip gauge.

**11-21-22-2011**

* SC32A jumper set as per CS instructions. It should be possible to connect to a CR10 with this in the field.
* Rebuilt WS6 program from Dropbox using Edlog (Document DLD File). The most recent file was called WS2_071030.dld. Leaving T/RH calibrations (multiplier and offsets) alone even though it is likely we will replace this sensor. May have to do a calibration of all sensors in spring.
  * WS6_111122.CSI is now on Dropbox
* Went through calibration data on Dropbox - Looks like all T/RH sensors were calibrated (except maybe #4)in the recent past using a dewpoint generator.

**11-16-2011** - Plotted data from all sensors in matlab to look
        at what sensors are working. This is what I found:

* **WS1** (in the garden)
  * T/RH = ok
  * Wind sensor 1 = not working
  * Wind sensor 2 = ok, and this has windspeed and wind direction
  * Rain gauge = ok
  * PAR = ok, though there is a weird seasonal jump in PAR (by about 300μmol m^-2^ s^-1^ in the middle of summer)
  * Battery = ok (no charging problems)
* **WS2** (by the reservoir)
  * T/RH = ok
  * Wind sensor = ok
  * Rain gauge = ok for the last year, though it looks like it had problems before that
  * Battery = ok (no charging problems)
* **WS4** (halfway up canyon)
  * T/RH = ok
  * Wind sensor = ok
  * Rain gauge = broken for the last 1.5 years
  * Battery = seems to be losing capacity over time and may need replacement soon

**10-7-2011**

* Was able to download data from all 3 returned storage modules (WS1, 2, & 4)
* See procedure [here](instruments/inst_cr10dataloggers.md)
* Uplodaded data files to project Dropbox

**10-5-2011** - Susan and Greg visited WS6

* T/RH and rain sensors are both bent out of shape
* Station appears to have lost power and there is no program running.

**9-30-2011** - Collected storage module from WS1 at around 5:30pm


**9-27-2011** - Susan and Greg collected storage modules from WS2 & 4, did not reach WS6.

