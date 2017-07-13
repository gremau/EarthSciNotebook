# NMEG flux processing log

## AmeriFlux data submissions

2007-2014 are submitted and in review, and we think these data may make it into the FLUXNET2015 data release.

## The bad IRGA - #0922

Bai Yang originally brought to my attention the fact that there were higher H2O concentrations at PJ control in 2014 than in earlier years ( by about 5-10%. Upon investigation I noticed that the timing of these higher than normal values roughly coincided with the period that a specific IRGA (ser# 0922) was installed at the site (5/2/2014 to 10/31/2014). This IRGA was subsequently installed at

* PJ_girdle from 2014/11/7 to 2015/1/23
* PPine from 2015/2/17 to 2015/8/18, checked agc at this time and it was ok

Later investigation by Steven indicated that this IRGA was not holding its calibration well, so we sent the IRGA back to LiCor. I don't think the data need to be corrected, however. There appears to be a similar pattern in atmospheric H2O concentration observed at PJ_girdle during the 2013-2014 growing seasons (low in 2013, higher by a similar amount in 2014). So, though the data may be slightly more noise in 2014 due to the calibration problem, there doesn't appear to be a level shift that needs to be corrected for this IRGA.

## 2007 and 2008 QC

GLand and SLand done 

## Drought and Info-flow papers

### Drought
* Sites are arranged along an elevation/water availability gradient. It follows that drought severity and ecosystem response is higher at low elevation.
    - Rank years according to precip defecit, vpd anomaly, and other metrics along the gradient.
    - Which are good years and which are bad relative to our measurements and according to long term mean?
    - Need to add some metric of soil water availability
 * Quantify ecosystem response - is there a gradient of drought sensitivity among our sites?
    - Calculate NEE, GPP, and RECO anomaly in each year. Is this related to precip defecit, vpd anom, soil water availability?
    - Dan's sensitivity curves (flux vs temp/vpd/etc - binned for all years and by season/year).
* What does THE GRADIENT tell us about southwestern drought and vulnerability to drought?

### Info-flow
* Hypothesis - Info flow between water (swc, vpd, etc) is higher at low elevation sites.
    - below a certain availability threshold water has little info flow to fluxes
    - Above the water availability threshold - Tair, radiation, nutrient avail, etc contains more information.


## PJ_girdle 2009

* There is a correction to 2009 PJ_girdle fluxes that was developed in 2010 and has been used ever since. However, it was commented out in the code I ran to reprocess fluxes recently and this is the reason that my fluxes looked so different for this year. This correction gets applied in the UNM_flux_031010.m script. I have added the appropriate conditional statments to make it run whenever this script is run for PJ_girdle prior to Sept 1 2009.

* That said - I think the fluxes look a little bogus with this correction. There appears to be an abnormally high amount of CO2 uptake early in 2009. Just a feeling, but maybe the data prior to about April 20 does not need any correction.

## Partitioning type analysis

See the IPy notebook. Several sites have strange issues with partitioned fluxes

## What happens when datalogger clocks are reset?

Periodically we have to reset our datalogger clocks. We are curious about what happens to the data logged when this occurs.

### 30 min data

* Data is collected as normal, and the observations stored in the internal table in the datalogger either are missing timestamps or have duplicate timestamps.
* Consequently, during the half hour period during which the clock is changed a larger or smaller number of observations is used to derive each 30 min value in the output table.
* The sign of the change in observations  depends on whether the datalogger time was moved forward (fewer observations) or back (more observations).
* This can be seen in the `n_Tot` column in the TOA5 file. A normal half hour period with no clock change has 18,000 observations.

### 10 hz data

* Again, data is collected as normal in the datalogger table, which may mean not all timestamps are present in the observations, or some timestamps are duplicated.
* All observations are present in the 10hz output table (TOB1 file).
* When 10hz data are processed into 30 min fluxes, the `iok` variable indicates how many 10hz observations were used to calculate the flux. This value fluctuates up or down during the 30 min clock reset period.

##2015-04-20

1. Moved all 8100 data from Sandia and consolidated files from PJ and PJG folders into one - `PJX_all8100data`. A few of the testing folders on the ftp might still have different files (did not overwrite).

## 2015-04-14

In the last couple days I have:

1. Created new issue trackers for all sites and shared them with the lab.
2. Created an always-up-to-date tutorial for people using processed data.
3. Figured out how to create new daily files from the ameriflux files I have made
    * This involves creating an "aggregator" object for the site, then writing a file from it:

            agg = UNM_Ameriflux_daily_aggregator(UNM_sites.JSav);
            agg.write_daily_file();

    * The aggregator output is dependent on the files it finds  in $FLUXROOT$/Ameriflux_files



## 2015-04-10

This has been put in the issue tracker spreadsheets

Looking at results from MPI gapfiller/partitioner.

* JSav 2014 is terrible - fluxes are bad and there are SWin spikes.
* GLand 2009 looks bad - Lots of missing fluxes and LE filling looks bad  - maybe there is a bad met stream?
* MCon 2009, 2010, and 2012 SWin looks bad - see note below about met gapfilling.
* PPine SWin also looks bad early and late in year - appears related to met gapfilling.  I think most of this gapfilling is unnecessary... related to mysterious end of year radiation removal.
* PPine flux fingerprints, especially LE,  are a little wide after gapfilling also - maybe related to radiation?
* Of course 2013 gapfilling at MCon and PPine sucks...

## 2015-04-09

This has been put in the issue tracker spreadsheets

Gapfilled Met data for GLand, SLand, New\_GLand, PJ, PJ\_girdle, and JSav 2009:2014

* Need to look at PPine gapfilling - precip units are wierd, we must have some RH, and SWin filling is a little lower than ours.
    - There also appears to be a timeshift/tilt issue in 2009
* PJ sites were filled with bad PPFD values from JSav in 2014.
* MCon 2014 precip gauge data reads 0 for the 1st half of year, so it is not gapfilled. Need to change this.
* First 100 days at SLand in 2014 probably need to be set to NaN and filled in (no precip).
* Radiation filling at MCon is bad, it looks ok in a timeseries but the sensor is tilted/shifted - see early 2009 data. Also, not sure why it is filling SWin at the end of the year... raw data looks ok there.

## Ameriflux QC

This has been put in the issue tracker spreadsheets

### PJ

* 2009: Big precip events days 250-255.
* 2011: Fc noisy in Dec. due to IRGA issues
* 2012: Fc noisy in Jan. due to IRGA issues
* 2013: SWin gap in middle of summer.
* 2014: PAR drops significantly around day 168. Gapfilling from JSav this year is bad.

### PJ_girdle

* 2009: Precip data missing at start of year, but it appears to be NaN (not zero) so it should be gapfilled. RH missing early in year.
* 2010: Something strange with PPFD in mid summer (2 sensors maybe?).
* 2011: Good
* 2012: Large gap days 300-339
* 2013: SWin a little high early and late in year
* 2014: Big PPFD drops between days 50 and 75. IRGA change and big [CO2] drops between days 112-130 - it looks to me like this  negatively impacts Fc (false uptake?). Code removes this now. SWin a little high early and late in year. Gapfilling from JSav this year is bad.

### MCon

* 2009: No SWin until May, then it seems a little high. No precip data.
* 2010: No PPFD until August, and SWin looks high. Precip starts around day 280. RH looks bad in first half of year. There is something funny with Fc (or maybe just less noisy than usual) and perhaps datalogger timing in Nov-Dec (Day 300 on look strange).
* 2011: SWin a little high. Maybe a slight timing issue in Jan (related to end of year 2010?). Noisy Fc data at end of year - check for IRGA change.
* 2012: Datalogger times were a total mess this year. Looks somewhat better, but the CNR1 was tilted. SWin a little high. Huge precip event around day 75. Fc is very noisy at the beginning and end of the year and there are some high IRGA CO2 values here (cold weather problems?).
* 2013: CNR1 tilted and small datalogger time reset in Jan-Feb. Sensor was probably leveled in late March? SWin still high. Fire wiped out most of year. No precip after fire.
* 2014: Clock shift. Precip missing until day 184. SWin is too high. No RH.

### PPine

Pay attention to sketchy normalization steps with PPine respiration - setting CO2 limits results in unexpected behavior.

* 2009: SWin is strange up to mid-May. PPFD a little low until it drops to 0 on day 318. No precip data. Period of bad Fc (removed) days 151-183, but bad LE and HS are not removed at this time.
* 2010: PPFD and SWin drop to 0 on day 318 again. Precip data starts day 236.
* 2011: PPFD and SWin drop to 0 on day 318 again (WTF???) must be some kind of cutoff coded somewhere? No RH data.
* 2012: No RH data. Same PPFD/SWin day 318 problem.
* 2013: Clock reset for small period in late Nov. No good PPFD or SWin. No RH data.
* 2014: Clock reset in middle of summer. No RH.

### New_GLand

* 2010: Clock reset June 27. No PPFD until day 85. Scattered low [CO2] at various periods - seems to be coincident with rain - removing some higher resp pulses.
* 2011: Power outages in July? SWin is too low. Precip seems a little low - winter/spring storm amounts are lower than at GLand and New_Gland is missing an event on day 100 that is present at GLand .
* 2012: PPFD is too high in Nov & Dec. SWin is too low.
* 2013: SWin too low. Precip has one unbelievably large event (25mm). May have missed events at days ~135 and 160 that happened at GLand. Funny PPFD calibration starting day 250.
* 2014: SWin still low to approx. day 18. Missing precip to Apr 2 - make sure it is filled - CHECKED - it is.

### SLand

* 2009: SWin is too high. PAR is messed up. Fc looks pretty good and there arent many coarse filters applied.
* 2010: Generally pretty good.
* 2011: PPFD disappears around day 160. Precip may have a problem - there are fewer precip events than GLand and old code used to remove data.
* 2012: Pretty good.
* 2013: Possibly some funny SWin at the end of the year - possibly related to a header change (non-Tcor to Tcor?)
* 2014: Jan Rg data looks too high (see not above). PAR sensor change in May and large PPFD spike days 257-267. Missing early year Precip followed by huge event on day 92.

### GLand

Shifted everything 1.5 hours

* 2009: PPFD data needs major attention. Gaps in flux data days 26-52 and 295-332. We could consider filling these with 30 min data (if available) or other site data (suspect this was done in the past).
* 2010: PPFD is crazy high, but then gets normalized. Big gaps in flux data days 100-119 and 295-327 -- Fill? IRGA calibration looks terrible this year. Exceptions were made for low CO2 calibration problems around days  85-99 and 152-168. Not sure if this was the right decision.
* 2011: PPFD disappears around day 160? Gaps in 30min and flux data days 165-207 could maybe fill a little flux data in with 30min data.
* 2012: Gap days 197-215. Crazy PPFD normalization again. Clock shift in Dec.
* 2013: PPFD too big.
* 2014: PPFD shifts down at around day 150 - new sensor? Bad IRGA cal period in middle of monsoon (Days 323-328) - probably should remove.

### JSav

* 2009: There was a clock reset in the code, but looks like it was wrong. Days 1:65 and 140:165 are missing flux data. Might be filled with 30 min data. PPFD has some funky negative values early in year.
* 2010: Not too many problems. Half-hour shift. Missing data between days 210 & 235.
* 2011: Days 45-52 have crazy [CO2] values.
* 2012: Looks pretty good except for gap in flux data at end of year (fill w/ 30min?). Huge precip value around day 190.
* 2013: Missing flux days 1-16. Funky missing flux data days 80-105. Possibly another clock shift around day 178. Huge precip event around day 214
* 2014: Have to remove giant PPFD spike early in year. Funny high nighttime Rg early in year. RH is too high (out of cal?).

## 2015-03-31
### Problem with PJ data card?
There is a funky gap between about 1/10 and 02/04 in the card data. Can't tell why yet but it seems to fill in data that is missing in the FLUXALL file/TOA5 files. Data look ok so far.

## Problem at GLand and New_GLand
Between 2014-01-17 and 2014-03-04 the datalogger program was incorrect and did not increment the CS616 measurement channel properly. This means the data files for this period are incorrect because every other sensor's column contains the data from the prior sensor in the mux measurement loop (for sensors on the same CR5000 SE channel). The program loaded on 2014-03-04 fixes this problem. This should probably be fixed in the header resolution files somehow...?

Something similar happened at New_GLand between 2014-06-13 and 2014-07-11 - Fixed (card was read incorrectly as GLand).


## PAR at GLand and SLand

During 2009 (and possibly other years) GLand and SLand had standard PAR sensors (LiCor?) and Par-Lite sensors (not sure what this is). These sensors have a fundamentally different response. Par lite data is preferred for whatever reason, so there is a script (`combine_PARavg_PARlite.m`) to use Par-Lite data when available and linearly correct the other PAR observation to this.

## Filling data for 2009-2014

### PJC

* 2009-2011 - no large gaps.
* 2012 = TOB1 data missing on Dec 3 & 4, not in wireless data.
* 2013 and 2014 are pretty good 

### PJ_girdle

* 2009: Data start February 23. Lots of gaps after this. Wireless downloads and cards do not have the data.
* 2010 and 2011 are pretty good
* 2012: Large gap Oct 29 to Dec 3 - not on wireless or in old card data
* 2013 has a 6-day gap in mid August and a 2 day gap in late Nov (TOA5 and TOB1 data missing) not on wireless or in cards.
* 2014 is pretty good 

### MCon 

Earliest wireless is from Sept 2012

* 2009 - 18 days of TOA5 and TOB1 data are missing at the start of the year. Can't get them off card and no wireless at this time.
* 2010 - Card data from late-Jan to mid-March and mid-June to mid-July is corrupt and there are big gaps in TOA5 and TOB1 data here both times. This data may exist somewhere, because the old fluxall seems to have some of the february data, but I'm not sure where....
* 2011 - is pretty good.
* 2012: There are large gaps in TOB1 and TOA5 data between April 15 and May 11, and between June 17 and July 20 that are not fillable with card data.
* 2013: Site down from May 3 to Nov 11 due to fire.
* 2014 - Jun 12, 09:30 to  Jun 20, 11:00 - not sure what happened here - original TOA5 data looks like these dates were overwritten with earlier data. There were some instrument changes and new programs that may have contributed.

### GLand

* 2009: A fair amount of TOB1 data is missing - wireless downloads are unreliable this far back. A small amount of card data was repaired and filled in a couple days. In old fluxall files some of this may be filled in with either the 30 minute data or the `UNM_gapfill_from_local_data.m` script.
* 2010 is pretty good.
* Large gap in June/July 2011 - was able to fill in some TOA5 data, but card and wireless ts_data files for this period are corrupt (I guess).
* No TOA5 data or TOB1 data to fill gaps in July/Aug 2012
* 2013 and 2014 are good

### New_GLand

* 2010: Large gaps in TOA5 and TOB1 data Feb 19 to March 12 . Not fillable from card or wireless.
* 2011: May 12 to June 22 TOB1 data is missing. Was able to rescue most of this from a corrupted card file, remaining fluxes could be filled in from TOA5 data.
* 2012: Missing TOB1 data Aug 2-8 and TOA5 gap on the 7-8th. Filled Aug 2-7 with wireless data. TOA5 missing data seems to show the batteries or power failing in early morning hours starting in April/May.
* 2013 & 2014 are pretty good - 1-2 days TOB1 and TOA5 (contiguous) data missing

### SLand

* 2009 - All but 10 days of TOA5 data filled in
* 2010-2012 are pretty much filled in
* 2013 -13 day gap in August that I can't find wireless TOA5 or TOB1 data for.
* 6 day gap in July 2014 data that I can't find wireless TOA5 or TOB1 data for.

### JSav

* There was no wireless at JSav prior to 2011.
* 2009 - There is a gap in TOB1 and TOA5 data at the start of the year (Jan 1 to Feb 2nd) that I can't find or fix data for. Some of the fluxes after Jan 20 can be filled in with existing 30min data. There is also a big gap in TOB1 data from 5/21 to 6/14/2009 that could be filled in with 30 min data (TOB card data is corrupt).
* 2010 - There is quite a bit of TOA5 and TOB1 data in August that seems to be unrecoverable.
* 2011 - pretty good
* 2012 - gap in fluxes at end of year that could be filled with 30 min data?
* 2013 there are multi-day gaps in TOB1 data in March and July that cannot be found on wireless.
* 2014 - pretty good except for two 1-day TOA5 gaps in September (not on wireless)

### PPine

* Don't think there is any wireless data for PPine before 2012 or maybe 2013.
* 2009 and 2010 TOB1 data are good. There is missing TOA5 data in March/April 2010, but it appears to be related to battery/power problems at the site ( ? - short outages ).
* Early 2011 gaps (Jan/February) in TOB1 and TOA5 data seem to be due to faulty/corrupt cards (tried to repair but failed). Some fluxes might be fillable from TOA5 data.
* There was a corrupt data card in Aug 2012 that was sent to Campbell and data was returned with the wrong timestamps. This needs to be put into the fluxall files manually, but I'm not sure how to do this yet. See documentation for this card in the `PPine\ts_data\20_Aug_2012_PPine_tsdata` directory and the `fix_20Aug2012_PPine_card_data.m` script.  A couple days of TOA5 data were lost around the same time.
* 2013 - Large gap associated with the fire (not fillable) and ~30 days of missing TOA5 and TOB1 data in late Nov through Dec that cannot be found in wireless or card data.
* 2014 - Quite a bit of TOA5 data missing, but never for very long periods (except for 1 day in Dec that was not on wireless).

## 3-12-2015



## 3-11-2015

Making new FLUXALL and AF files.

* Most of PJ AF files look good - but the Rg filling still needs to be fixed. Waiting for PJ_girdle to be finished first.
* Filling in some missing data for 2009 and 2012 at PJ_girdle.
    - Could not find any missing 2009 data - wireless files were unusable.
    - Was able to fill in some data in Aug 2012 with wireless, but not the large gap from 10/29/2012-12/04/2012
    - Made new fluxall files for PJ_girdle 2009-2013.
* Working on GLand filling. Lots of gaps in 2009, 2011, and 2012.

## 3-5-2015

Making new FLUXALL and AF files.

* All PJ - relaxed CO2 limits to: co2_max_by_month = [ 2.5, 2.5, 2.5, 3.5, 4, 5, 6, repmat( 6, 1, 5 ) ]
* One of the HMP sensors delivered bad Tair and RH data from 2009 to late 2012 (or later). Data from this sensor, which appears to be the canopy level sensor (not top of tower)  is labeled AirTC_2 and RH_2. This is a potential issue for other variables output from the datalogger as well, as e_sat, e, h2o_hmp, and rho_d are calculated with these to variables by the datalogger. This AirT and RH data is now excluded from the qc and gf files (but notes remain  below).
* PJ 2009 & 2010: OK, except for rH
* PJ 2011
    - rH
    - There are some low CO2 filters applied at the end of the year that seem a little strange. CO2 (ppm measured by IRGA) went pretty low at this time, probably due to some type of calibration problem. There are also cal problems in 2012.
    - Missing data periods: day 33, 59.5-61.5, 336-338, 352-357
* PJ 2012
    - rH has the same problem, but changes to a new problem out 2/3 through year
    - Change in datalogger time on afternoon of day 342.
    - Created exception to low_co2 filter for days 168-174.
    - Missing data periods: day 19-23.5 (not fixable), 70.5-71.5, 220-237.5 (found on wireless), 312.5-317.5 (not fixable), 338-340 (not fixable).
* PJ 2013
    - rH looks like garbage the entire year.
    - There is a messed up Rg sensor from mid June to mid July. Logs indicate that there was a broken lead that led to this that was repaired around July 17.
    - Filling the Rg data was problematic. We fill from PJG by default, which has a similar timeshift, so initially the timing of the filled in Rg data was offset. MAKE SURE TO CORRECT ALL "for_gapfilling" FILES BEFORE MET GAPFILLING!!!!.

## 2-27-2015

### Timing issues
 Shifts and such are working now - one remaining issue - plotting data for a timestamp means you are plotting the data for the prior half hour. This means data in plots is always plotted 15 minutes later than the period it was collected. I'm not sure how this affects our time shifts yet.

### 10hz data processing

`UNM_process_10hz_main.m` is the main script that does this, This is called from `card_data_processor.m` if there is no 10hz data, or if reprocessing is specified.

1. `UNM_process_10hz_main` breaks the processing period into chunks ( 30 day is the default ) and gets directory of TOB1 files.
2. `UNM_process_10hz_main` then loops through each chunk and passes the start and end time of each chunk, some configuration items (lag, sonic orientation), and the directory to `process_TOB1_chunk.m`.
3. `process_TOB1_chunk.m` opens each file using `read_TOB1_file`, vertically concatenates the data, makes a matlab datenum for each observation, bins observations into 30 minute periods, and sends each 30 minute chunk of data to `UNM_30min_TS_averager`.
4. It appears that `process_TOB1_chunk.m` correctly shifts the timestamp on these chunks such that each 30 minute average is for the the observations in the half hour PRIOR to its timestamp.
5. `UNM_30min_TS_averager` calls a number of other functions to correct high frequency data and calculate the 30 min fluxes from 10hz data ( `UNM_dry_air_conversions`, `UNM_csat3`, `UNM_flux_031010` and others).
5. These 30 minute averages are then vertically concatenated by `process_TOB1_chunk.m`, the 30 day chunks are returned to `UNM_process_10hz_main`, vertically concatenated, given a timestamp, given `jday`, and then missing data periods are filled in (with timestamp and NaNs).

## 2-25-2015
* Something is wrong with the way `jday` gets calculated in the fluxall files. It starts out ok, but then gets rounded.
    * Figured this out - it was an issue with the precision of exporting FLUXALL files in `export_dataset_tim.m` I set this to 8 (should be a minimum from now on).
* I have noticed that in most instances the timestamp variables are getting moved by `UNM_fix_datalogger_timestamps.m`, so the 30min data moves, but its timestamp variable is moved along with it.
* 10hz data is moved relative to the 30min data, but its timestamps move with it also.
* However, AF files ARE actually shifted relative to FLUXALL data - this was confusing.
* After examination this doesn't seem to be too bad of a problem. In the `RBD` script at least, the original data timestamp is what is used to create the output files, so effectively, the data do move relative to the timestamp, even though it does not appear this way in the `UNM_fix_datalogger_timestamps.m` script. There is probably a better and more consistent way to do this though.

## 2-22-2015
Implemented script to calculate solar noon, theoretical sunrise, and sunset for a site to use in our analysis (`noaa_solar_calculations.m`). This is based on the NOAA calculator [here](http://www.esrl.noaa.gov/gmd/grad/solcalc/).

## 2-20-2015

### Investigating time shifts

I have mainly used PJ2010 as a case study for this, and have only used 1 date for checking (July 21, 2010 at 3pm). From the figures the AF team sent in August, it looks like our clocks are at least an hour fast (at solar noon, roughly 12:10 actual time our clocks say it is 1:30) in 2008-2010.

* There doesn't appear to be any problem putting 30min data into a fluxall file. Timestamps and data seem to match up between the TOA5 files and the fluxall files made in 2013.
* Made new 10hz data (TOB1_filled.txt files) and FLUXALL files for PJ 2009 and 2010 so I could compare timestamps in the FLUXALL files and make sure they were lining up with the raw data files (TOA5 and TOB1).
* Data in new FLUXALL files (mine) line up with the TOA5 files and TOB1 files!
* Some covariances and ustar also appear to line up pretty well between the 10hz and 30min sides of the files (ie. `wt_covariance` vs. `cov_Ts_Uz` and `ustar` vs `u_star`), but they are not exact.
* Fc values don't match particularly well between the 30min and 10hz sides of the FLUXALL file.
* The AF files on cdiac  (made in spring/summer 2013) contain the shifts defined in the current version of RBD.m and the qc file made around the same time. This means that 10hz data is shifted 30 minutes earlier, and 30min data is shifted 1 hour earlier relative to the fluxall made at the same time. The more current version of the fluxall file that I made has the same shifts.

### The way it was done by Tim/Randy

1. `get_solar_elevation.m` is used to calculate a theoretical solar angle for each timestamp in a dataset.
2.  A function called `match_solar_elevation.m` then calculates the time differences (offset) between observed sunrise (first increase in radiation), and theoretical (solar elevation above 0).
3. Running `UNM_site_plot_doy_time_offsets.m` for a particular day of the year will show the results of `match_solar_elevation.m`.
4. These offsets are plotted in the function `UNM_site_plot_fullyear_time_offsets.m`.
5. Somehow these plotted time offsets are used to make a determination about how much and when to shift the data.
6. Actual shifting of the data (by site and year) is configured and executed in `UNM_fix_datalogger_timestamps.m` when the `RemoveBadData` scripts are run.
7. `UNM_fix_datalogger_timestamps.m` executes each individual shift with a call to`shift_data.m`. I suspect that the timestamp columns are being moved along with the data in most cases because the 'columns_to_shift' variables are set incorrectly. This should be fixed.

## 2-17-2015
Currently updating ancillary meteorology (for gapfilling) data. Note that:

* PRISM data for the 2nd half of 2014 is still provisional (I have not downloaded it yet)
* There is no DayMet data for 2014 (yet?)
* I have found a way to download good data from the DRI Jemez site (documented in the README file)
* 2014 VCP SNOTEL sites and VCP preserve sites are current.
* Still trying to track down a good way to get Sev data

## 2-11-2015
Some current issues:

* Soil sensor/header histories are now complete, including new header resolution files. Soil sensor histories are in a separate note here. The code also incorporates separately logged data (second datalogger) into the fluxall files automatically now for all sites but MCon and PPine. There is still some work to do on resolving the DRI soil sensor data for  these sites. Still have not made new AmeriFlux "soil" files.
* Am working on improvements to the precipitation filling scripts. Once these are complete, data for 2014 from the various sources needs to be tracked down.

## 1-16-2015
Have been piecing together the soil sensor/header histories for Sev sites and JSav for the last week. This has resulted in a new series of header resolution files and some changes to how they are generated. Once all sites are done, there are a few tasks left:

* Assemble good datasets of separately logged soil data from sites with extra dataloggers (MCon, PJ sites, PPine, and Jsav in 2012-13)
* Incorporate separately logged soil data into fluxall making code.
* Remove calls to other header renaming code (currently this is the `UNM_assign_soil_data_labels` files) as fluxall files are made.
* Figure out how to make new AF soil files using these new fluxall files.

## 1-8-2015

Now that we are processing cards that span 2014-2015 there is a problem in which the 10 hz data processsing code does not allow this. So These cards will have to be split up to complete the 2014 fluxall files and star the 2015 fluxall files. This should be done in card_data_processor.m.

## 1-5-2015

What is the deal with soil sensor data at a site? See the [[Site soil sensor histories]] note

## 12-18-2014

Prior to going to AGU I made new AF files with filled precip. However, there is an issue where some files end with a row of zeroes that throws of reading and analyzing the data - should fix this.

There is still a problem with headers PJG 2009 Radiation and CNR1 temp are messed up!

## 12-11-2014

Have been working on improving the met gapfilling procedures and adding data sources for this (mainly for precip). See commits () and ().

Note that all qc and for_gapfilling files will need to be remade.

## 12-8-2014

Precip values in qc files are not corrected for the incorrect multiplier values.... this should be fixed.

## 12-5-2014

To access [DayMet data](http://daymet.ornl.gov/) for our sites, there is a multiple pixel extractor tool that can be downloaded from the site. Downoad and unzip this tool, then edit the `latlon.txt` file within the new folder to include our site coordinates and the desired output filenames. Run `daymet_multiple_extraction.sh` (or the .jar file) and this will download temp, precip, and other data (1980 to 12/31 of prior year) for each point in the `latlon.txt` file and create a new csv file. 

## 12-4-2014

To access [PRISM datasets](http://prism.oregonstate.edu/recent/) requires reading the band interleaved (.BIL) files they provide. This can be done in by using [GDAL]( http://www.gdal.org/) from python, but some things need to be installed on the system first. On windows it is a little tricky and you need to be sure the GDAL you install (which comes from [here](http://www.gisinternals.com/sdk/)) is compatible with your Python installation. 

* Decent instructions can be found [here](http://pythongisandstuff.wordpress.com/2011/07/07/installing-gdal-and-ogr-for-python-on-windows/).

Once GDAL is installed, the python bindings need to work. I have installed the Anaconda Python distribution on the lab computer, with Python 3.4. GDAL is only compatible up to 3.3, so we need to also create a Python 3.3 environment. Instructions for this can be found [here](http://www.walkingrandomly.com/?p=5089).

* Use `activate py33` from the windows shell to switch to this environment

There are two python scripts and a list of coordinates (`site_coords.txt`) needed to generate daily precip datasets from PRISM. In ipython run `getPrismPrecip.py`. This calls the `prismParser` class to open the Bil files and extracts the PRISM grid cell value for each site listed in the `site_coords.txt` file.

## 12-2-2014

1. Added a linear fit to make Rlong_incoming data at PJG for 2009 to 2013 match the same data at PJC. There was an offset between the sensors that  seemed to be in error. I generated the regression coefficients for each year using R, then applied the linear fit in `UNM_RBD_apply_radiation_calibration_factors.m`. See changeset 731 (05b89ee30c8b).

## 11-25-2014

1. Made new fluxall files for 2007-2008 at most sites (with records that far back). These have not had 10hz data filled in with 30min data because the `30_min_spooler` does not currently work for them.

2. There is no precip data for MCon or PPine in 2007 & 2008. It appears in the old fluxall files, but I have no idea where this originally came from. I tried pasting in precip from old files, but this didn't work well.

3. There are no radiation components (including CNR1 temp) for PJC in 2007.

4. PJG 2013 Rlong in and out are still missing in the new ameriflux files!

5. PJ 2007 looks terrible in the partitioned data returned from eddyproc - should probably investigate this and exclude from Biederman analysis.

6. Ultimately I was unable to make new `fgf` and `fgf_filled` files for MCon and PPine 2007 & 2008, or for PJ 2007 due to the issues above. Instead of try to solve these problems now, I sent older `fgf_filled` files to Jena and will use these (at least for the 4 sites Joel needs).

7. Also sent an older `fgf_filled` file to partitioner for MCon 2010 because the fluxall file I made is missing precip values and has large unfilled gaps (compared to old files).

## 11-24-2014

1. Have now created new AF files for all sites from 2009-2013
    - PJ 2011 will need to be revised to use the updated fluxall from Dan
2. Moving towards making new fluxall files for 2007-08
    - Copied TOB1 data over from archive disk (MyBook, L:).
    - Have also moved old fluxall.xls files over from jemez to compare with.
3. `UNM_30min_spooler` and the `UNM_30min_flux_processor` scripts that it calls need major work. Some of the old versions of them seem pretty buggy. 

## 11-20-2014

1. I think the Massman and WPL corrections need to be examined in detail. When processing 10hz data files program calls are: `process_TOB1_chunk.m` -> `UNM_30min_TS_averager.m` -> `UNM_flux_031010` -> `UNM_WPLMassman.m` (which calculates WPL and calls -> UNM_massman.m to get the Massman correction). However, the WPL correction is also calculated in `UNM_flux_031010`, so it doesn't look like the `UNM_WPLMassman.m` calculation is used. I'm not sure which is correct. In any case, if these need to be changed all 10hz data will need to be recalculated into 30min fluxes. Which will take ... forever.

        Another solution is just to remove the cold weather fluxes when they look bad at MCon. Essentially this is what the CO2 max-min filter (which I am still using) is doing, but I will have to improve on this solution.

2. Marcy is curious if PJG and PJC have the same energy balance. Need to compare R_long in and R_short in for both sites and see if they correlate well. If not, can we correct this (a regression maybe?).

3. The radiation corrections in `UNM_RBD_apply_radiation_calibration_factors.m` are highly suspect. These need to be reviewed.

## 11-16-2014

1. Could not fill any missing 2013 or 2012 data for MCon using the wireless data that Renee provided (all are real gaps-no irga/sonic data).
2. Filled part of 11/15-11/19 and 11/25-11/28 gaps with wireless data and will generate flux data with 30min side (ts_data file is corrupt).
3. Figured out what fluxes from which files make it into Ameriflux files. This is determined in `UNM_Ameriflux_prepare_output_data.m`. Lasslop partitioning is used.

### Unfilled fluxes are:

- `NEE_obs` comes from `fc_raw_massman_wpl` in the qc file for the site/year.
- `LE_obs` comes from `HL_wpl_massman` in the qc file
- `H_obs` comes from `HSdry_massman` in the qc file

### Gapfilled fluxes are:

- `NEE_f` comes from `NEE_f` in DataSetafterFluxpart.txt.
- `LE_f` comes from `LE_f` in DataSetafterFluxpart.txt.
- `H_f` comes from `H_f` in DataSetafterFluxpart.txt.

The script ensures that observed values are used where available.

### Partitioned fluxes are:

- `RE_f` comes from `Reco_HBLR` in DataSetafterFluxpartGL2010.txt (Lasslop partitioned).
- `GPP_f `comes from `GPP_HBLR` in DataSetafterFluxpartGL2010.txt (Lasslop partitioned).

### Recalculations to NEE, GPP and RE to ensure carbon balance

- `NEE_2` = `NEE_f`
- `GPP_2` = `RE_f`  - `NEE_2`, when GPP is negative, set to zero and add difference to RE.
- `RE_2` = `RE_f` plus the difference when NEE exceeds RE.

These values (`NEE_2`, `GPP_2`, and `RE_2`) are then sent to the output both preserving original gaps, and in gapfilled form.

## 11-12-2014

Verified that the burba correction we have in RBD.m is correct, according to the spreadsheet that came from George Burba. I put MCon 2010 data into both and came out with roughly the same values.

I am a little concerned that units under particular headers differ between some years/sites. For example MCon 2010 `H2O_mean` header is in mmol/mol, while this changes to g/m^3 in later years. Rho measurements appear to be in different units, and moist and dry values may be confused in some fluxall files (based on what I can tell from the datalogger program).

## 11-10-2014

1. Moved all old `fluxall.txt` files over from jemez (except 2014) from the 8 sites. For now I am ignoring Excel fluxall files but have included other ancillary datasheets (not sure what some are).
2. Moved all old `processed_data` files over from jemez. Within each sites `processed_data` directory, the old files are in the `fgf_archive`, `fgf_filled_archive`, `qc_archive`, and `fluxpart_archive` folders.
     - for the most part I have checked and then left files in subdirs of `processed_data` on jemez. Usually these are subsets of data, archived data (perhaps prior to processing changes), or irregular looking files. May be worth looking at these at some point.
3. In process of moving all data in each sites `toa5` and `ts_data` directories from Jemez to Sandia.
    - GLand, JSav, MCon, New_GLand, PJ, PPine, PJ_girdle, SLand
    - All subdirectories in Jemez `toa5` and `ts_data` folders were moved
4. Moved old ancillary met data over from jemez.
5. Moved old licor 8100 data files and MCon precip data files over from jemez


## 11-07-2014

Met with Marcy/Dan/Laura:

TO DO in prep for AGU:

1. Get calculated u* tresholds calculated for all years at all sites (or as many as possible) using the MPI eddyproc tool.
2. Make plots of the binned u*/NEE from each site/year (output from RBD.m)
3 Compare the MPI and our u* thresholds
4. Check that longwave radiation looks ok in current and older AF files
5. Compare Reichstein and Lasslop partitioning of Reco at MCon and decide which to use.
6. Regenerate older AF files with new changes to RBD (inc. Burba, u*, etc) - do this for as many sites/years as possible.

## 11-06-2014

Working on Burba correction and other issues at MCon. 

* implemented the Burba correction but it doesn't change winter uptake fluxes radically (they are still there mostly).
* Also investigated timestamp corrections to see if they were to blame, but no indication of this yet

## 11-05-2014

Met with Marcy to discuss some issues with MCon data. Part of this is motivated by Joel Biederman's findings that this site seems to have abnormally low Reco (relative to GPP). A few things need to be examined.

* We have somewhat unusual looking amounts of uptake (negative NEE) in the depths of winter, even when temps are low. This may indicate that our Burba cold temp correction is faulty.
    - I checked this, and think the Burba correction isn't being applied to the flux data. It seems to be calculated correctly (I think), but it is never applied to the `Fc` values that are exported for further processing.
* The partitioned fluxes at MCon look sort of funny. Reco is pretty low in winter/spring (and similar to PPine), but there is not much of an increase when the weather warms up. This could be a partitioner problem (we should compare both the Lasslop and Reichstein methods). 
* Other possible explanations for the low respiration include N deposition, which can suppress decomposition and stimulate GPP, low C stocks due to harvest (though Marcy seems to think there is tons of soil C there), or we may be losing some of the respiration to downslope flow from the ridge.
* There is a pulse of respiration around May during many years at MCon. Maybe this is snowmelt related?

TO DO:

1. Fix the Burba correction in RBD.m and see that it is applied to the outgoing data.
2. Make plots of Fc with and without the Burba correction.
3. Make winter plots of uncorrected and Burba corrected flux vs temperature.
4. Plot summer Reco form both Lasslop and Reichstein partitioning methods.
5. Look at the timing of snowmelt (maybe using albedo) at MCon to see if the positive NEE pulse is related to this.
6. Marcy wants to know what parameters the eddyproc site uses - not sure which parameters or how to find them out. Maybe look in the info log?
7. Prod Marcy to ask around about N deposition and soil C data at MCon.

## 11-04-2014

Solving GLand/New_GLand problems from prior months - all card data files have been moved to the right folders and are ready to be reprocessed. New(ish) cards have also had files copied to `Raw_data_from_cards` directories, and to a directory on the NAS.

* There is a missing `1473.ts_data.dat` file (for GLand) from 9/4/2014. This file exists on the card but it is corrupt and cannot be copied or repaired by CardConvert. May need to be found on wireless.

## 11-03-2014

Revisited ustar filtering (run `UNM_RemoveBadData(UNM_sites.{SITE}, {YEAR}, "iteration", 1, "draw_plots" 3)` at SLand, PJ, PJG, and JSav.

* Changed JSav: 0.8 --> 0.9
* I sent 2013 data from the lowest 6 sites to the MPI partitioner without u* filtering applied and asked for eddyproc to do u* filtering.
    * In general, eddyproc's selected u* thresholds are much more conservative (higher) than ours.  They have been added as comments in RBD.m
* Did not change any limits for now. These seem like pretty subjective calls to use the plots RBD.m makes.

## 10-31-2014

The 1 day per 30 gaps in fluxall TOB data is being introduced in the flux processing code for some reason

## 10-29-2014

* There are now 2 irgas at SLand. Archive the `ts_data2.dat`and `flux.dat` files in the `Raw_data_from_cards` folder, then cancel conversion to TOA5 and TOB1. At some point we'll need to process these, and there will be an extra irga at GLand.

* Other sites missing data in 2013:
    - PJG and SLand have missing 10hz data one day a month (not sure why) - this was all filled in with 30min data
    - PJ 11/22 - 26 - nothing on wireless, looks like irga was down - not filled
    - GLand 10/18 - 22 - filled in with wireless data.
    - New_GLand 11/22-24 and 11/24-25 were missing from the card data and wireless data - not filled
    - PPine has big gaps in Nov. and Dec., but there is no wireless data to fill with.
        - 30min data that is available (rare) during PPing gaps looks pretty suspect to me so I didn't fill from 30 min periods.
    -  Similar problem at MCon - there are gaps (outside of fire) but the 30min data available to fill them looks funny to me.

* All the 30min fill in periods for JSav, SLand, GLand, and PJ_girdle were added to `UNM_30_min_spooler.m`.

## 10-28-2014

### Gap filling

* Done patching JSav 2013 from wireless and 30 min data
    - Filled  3/20-4/17 and 4/24-5/16 gaps with wireless data, but the 3/20-4/17 part is very sparse (intermittent irga problems?)
    - Also filled some gaps in October with wireless data
    - Filled 3/27- 4/1, 7/20-7/24 and 11/27 from 30min data (`UNM_30min_flux_processor_Tim`)
    - Couldn't find wireless or 30 min data to fill missing periods from Jan 1 - 16 (irga down) and July 25-29 (irga and sonic down?)
* Done patching SLand 2013
    - Patched 1/1 - 1/16, 2/13-2/15, 3/15-3/19 with wireless data.
    - Filled 1/1, 3/2, 8/28, 9/28, 10/28 with 30min data.
    - Couldn't find  wireless or 30min data to fill Aug 14-28.
* Done patching PJ_girdle
    - Patched 4/24-4/30 with wireless data - still seems to be empty, to the irga was probably down
    -  Couldn't find wireless or 30min data to patch Aug 14-21 or Nov 22-25

## 10-24-2014

Today I am filling missing 2013 data from wireless downloads. First step was to make a new TOA5 file for JSav 2013 (`TOA5_JSav_2013_04_24_1230.dat`) using a wireless download and vim. The data were missing due to a messed up card (I think) but were found on the wireless.

####Steps to create new TOA5 files from wireless data.

WARNING - Poorly formatted TOA5 files cause big problems. Be careful to follow all these steps. Also, this will overwrite old fluxall files. Make a backup!

1. Copy the desired wireless files (something like `NMUFN_{SITE}_CR5000_flux.dat.backup` file to the `FLUXROOT\{SITE}\wireless_data` directory.
2. Open the file in Excel and delete the 'Records' column (second column) from the second line to the end of the file.
3. Excel screws up date formatting, so select the dates and format to custom -> 'yyyy-mm-dd hh:mm:ss'
4 Save as a csv file with a filename that matches the startdate of the 30min period being patched (`TOA5_JSav_2013_4_24_1230.dat`).
5. Since Excel has screwed up the formatting, copy the correct headers (lines 2-4) over from the wireless backup data file, then remove the second headers in lines 2-4 (indicating "Record"). I normally do this in a diff program.
6. Open in vim (or another text editor) and delete all lines with timestamps outside the range needed to fill the gap.
7 Put quotes around the date string. In vim do this with:
    - `%s/^2013-/"2013-/g`
    - `%s/:00,/:00",/g`
    - These should make changes on all lines
8.  Excel has also changed "-INF" values to #NAME? so these need to be changed back with `%s/#NAME?/"-INF"/g`
9. Put the new TOA5 files in  `\wireless_data\toa5_patch`.

From here - copy the new files into the appropriate folder (`\toa5`), make a new cdp object and do `cdp.update_fluxall` (making sure it loads and processes correct TOA5 files).

####Steps to create new TOB1 files from wireless data.

WARNING - this will overwrite old fluxall files. Make a backup!

1. Copy the desired wireless files (something like `NMUFN_{SITE}_CR5000_ts_data.dat.backup` file to the `FLUXROOT\{SITE}\wireless_data` directory.
2. Change the extension of files you wish to convert to TOB1 format to `{FILENAME}.ts_data.dat`  (remove `backup` and change 2nd to last '_' to '.'
4. Run `[tsdata_convert_success, ts_data_fnames] = tsdata_2_TOB1(UNM_sites.JSav, fullfile(get_site_directory(UNM_sites.JSav), 'wireless_data'), 'wireless', true)`
   * This should go through the archived wireless file and make new TOB1 files and put them in `\wireless_data\ts_data_patch`.

From here - copy the new files into the appropriate folder, make a new cdp object and do `cdp.update_fluxall` (making sure it loads and processes correct TOB1 files).

## 10-22-2014
There are a few precipitation wiring and logging issues that have taken place at some sites over the years, and these need to be corrected during the flux processing. Currently these are only fixed on the way to making Ameriflux files (so fluxall and qc files are wrong) by `fix_incorrect_precip_factors.m`.  

The problems described below are fixed as of today (see Changeset 699 (dbf0805b78ad))

1.  PJC
    * The metric precip gauge was installed 1/15/2008
    * On 5/12/2010 the precip multiplier changed (vol per tip in mm or in) from .254 to 0.1 in `PINON_JUNIPER_051210.CR5`
    * The rain gauge has metric output (0.1 mm/tip), so this corrected incorrect logging of precip (was .254 since install)
    * This program was uploaded to the CR5000 on 5/31/2010 according to the logs
    * `fix_incorrect_precip_factors` corrected the earlier data for the Ameriflux files (but not other files), but the dates of the correction were wrong (started too early - May 12th) and extended too long (Randy extended to 2013).
    * 2010 Ameriflux file may need to be remade.

2. JSav
    * A metric rain gauge (.1mm/tip) was installed at the site on 1/15/2008 (though this was either verified or reinstalled on 1/11/2012).
    * The datalogger programs recorded each tip as .254 mm until January 10, 2014 (program `JSav_010714.CR5` sent to datalogger).
    * This was corrected in `fix_incorrect_precip_factors` for 2010-2013, but early 2014 precip still needed a correction

3. SLand
    * In 2008 a new TE525USW (inches - 0.01in/tip) gauge was installed.
    * The rain gauge at the site broke sometime in summer/fall of 2011.
    * It is not clear if it was fixed or was replaced with a US inches calibrated gauge (.254 mm/tip), around Nov/Dec of that year and there is a note that it was still not working on 11/22/2011
    * It was also changed to pulseport 1 on 11/22/2011
    * Jonathan notes the rain gauge was working again (after some troubleshooting) on 4/2/2014
    * Datalogger programs seem ok - conversion factor is 0.24
    * Doesn't really seem like anything needs fixing - it will just have to be filled in with another site.

4. GLand
    * In 2007ish a new TE525mm (metric - 0.1mm/tip) gauge was installed.
    * This was replaced on 8/21/2008 with a new gauge (same model?).
    * Precip multiplier was .254 until program `UPLAND_GRASS_011614.CR3`
    * New program (corrected multiplier to 0.1) was sent on 1/17/2014

5. New_GLand
    * On January 17, 2014 a new program was uploaded (`newgrass_011614.CR5`) which changed the precip measurement from pulse port 1 to port 2. The gauge, however, was still wired to pulse port 1, so no precipitation (all zeroes) was collected thereafter.
    * At the same time, the multiplier changed from .254 to 0.1 (wrong).
    * The gauge was rewired to pulse port 2 on 4/2/2014 and started working again, but the multiplier was still 0.1 (incorrect)
    * Correct multiplier (0.254) restored on 9/24/2014 when newgrass_092414.cr5 was loaded.
    * Note that we are MISSING PRECIP data up to 4/2/2014! These should be filled from another site, which will happen because earlier these data are now set to NaN by 'RemoveBadData.m`.

## 10-15-2014
There was a problem with the filling of data from nearby sites at PPine (see Rg filling for PPine 2013 when `UNM_fill_met_gaps_from_nearby_site.m` is run)

* The filled data was MUCH lower in magnitude than the original data, creating a mismatch
* This appears to be related to the linear fit that is applied to some data - see the `fill_variable` function in the script.
* FIXED: It was the linear fit, but it failed because there were zeroes in the Fluxall data (removed with RBD.m now see 
Changeset 694 (a0741548c5de))

## 08-29-2014
* Fixed matching timestamp problem in the combined 23x fluxall files I am making for laura. It has to do with the start and end date of the soil and fluxall files and whether they match.
    - see the comments in preprocess_PJ_soildata_DK1.m
    - There is still some manual fiddling required to make the files build that depends on what the fluxall files look like for that year
* Tweaked the JSav header resolutions file - now it does not work in the script - and will need more fixing?

## 08-27-2014
*  Made `UNM_Ameriflux_Filemaker.m` work
     - it needs all yearly Ameriflux datafiles to make the concatenated daily file, these are put in FluxOut by default
* There is a problem with the outputted file from PJG - no Rlong data. It is being removed by the `UNM_Ameriflux_prepare_output_data_TWH` script because it is out of range. This may not be a problem for other sites.
* Longwave radiation is negative when it comes in on cards - why?


