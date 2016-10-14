# Soil temperature analysis log

This log mainly covers analysis of SNOTEL soil profile data.

 **See also:** The [project
        overview](west_stationdata:overview).

------------------------------------------------------------------------

 **3/26/2013**

Looking for sites to use as example sites in multiple regression.

* 366 (brighton)or 521 for winter Tsoil vs onset date.
* 334 or 368 for winter VWC vs Dec SWE
* 334 or 392 for growing season VWC vs peak SWE`

 **2/5/2013**

* I made a change to the sigma filter which it fixes the ends of the running mean. This fixes some erroneous data rejection at the beginnings and ends of the timeseries. Re-running summarize_wateryear.m, and this may have an effect on some of the analysis, so plots should be rerun.
* Have mostly finished up the pca work, just need to figure out how to summarize and present it.
* Added may precipitation to the climatesummary data file (made a change in summarize_wateryear.m to do this)

 **1/20/2013**

I'm going to merge this log with the soil moisture log because it
doesn't make sense to me to maintain 2 anymore. The content that was at
that log is shown below.

<file>

 **Oct 14, 2012**

A question: Is it valid to take the mean of all monthly means from a
site? It should be fine if the months are the same length, but in the
case of missing data during a month, these means wouldn't be valid.

 **Oct 10, 2012**

Have spent lots of time recently removing bad data and improving
filtering. A couple of current problems

* There were times when the sigma filter would not work. This occurred because the runningStd calculation sometimes produced an all NaN series after trying to calculate Std. deviation on the filled series (from interpseries.m). This only happened with timeseries that began or ended with NaNs and is the result of the interpseries ignoring the ends of a series if they are NaNs. I'm trying to figure out how to fix this.`

 **Feb 21, 2012** - A couple ideas:

* Mean soil moisture the week before snowpack onset and the day of snowpack onset.
  * Does this correlate with winter soil moisture? Until when (relative to peak snowpack or snowmelt)?
* Does day of snowmelt correlate with late summer soil moisture?
  * In monsoon vs non-monsoon areas? Perhaps monsoon areas are more correlated with summer precip?`

 **Feb 16, 2012** - Have done lots in the last few days:

* **New 30-year mean data** (SNOTEL SWE, SNOTEL Precip, and SnowCourse SWE) downloaded from NRCS website, error checked, and tabulated in a new spreadsheet. See `rawdata/longterm_averages/SnowSurvey_7100Avg_Master.gnumeric`.
  * Makes some older spreadsheets obsolete, though there are some old copies.
  * SWE and precip data are exported as .csv files to the curated data folder for use in data-analysis scripts
* **New station inventory spreadsheet** is located at `rawdata/station_inventory/NRCS_inventory_MASTER.gnumeric`.
  * Created by downloading and editing .csv files from the NRCS [data`
`search](http://www.wcc.nrcs.usda.gov/nwcc/inventory)webpage.
  * This file is being used to keep track of what SNOTEL/Scan/SnowCourse data is available for snowpack and soil profiles, and what data has been downloaded already.
  * Might replace the other inventory .csv files in this directory (some scripts still rely on these though).
* Both of these files have some documentation available in the first sheet.
* Some general reorganizing and cleaning out of old data and scripts in the rawdata, and data_analysis folders that contain this project.
  * `obsolete_scripts` holds old SNOTEL network analysis scripts that may still be useful but are being replaced by new ones. There is a corresponding collection of data files in the rawdata directory.
  * `curated_data` holds textfiles that are output from spreadsheets or scripts that operate on raw data (as it might be useful to version these).
* New script to calculate many metrics of climate and interannual variability (in snow, precip, temp) from the daily data. It outputs a large dataset to the `curated_data` directory and is read by plotting scripts. **Will be documented [here](programdocs)**
* Downloaded a large amount of new data from the NRCS website to `allsensors_daily`, and `soilsensors_hourly` directories.
  * Now have daily data for all SNOTEL sites with soil profiles from install to 2010 (working on 2011)
  * AZ, NM, UT, and CO have complete sets of the SNOTEL soil profile data (NV, WY, ID, MT to go still).
* Met with Dave today, and we agreed that **more daily data is needed** - preferably all of it for the last 10 years or so.`

 **Feb 3, 2012**

![media/west_stationdata:plot_4sites_distrib.png?300|Sites in each column
are Trial Lake, BL Trail, Chepeta, Little Grassy (Right to left)]

* plot_monthly_sm_distrib.m has been reworked and renamed to plot_soilsensor_distrib.m. It is a bit more generic and will plot soil temperature data in the same fashion.
* Have been working on some case-study type plots comparing high/low elevation/swe sites (in a factorial way). Results for Trial Lake, Ben Lomond Trail, Chepeta, and Little Grassy are **to the right** ->. Chepeta seems to defy expectations a bit by being highly variable in spring. (Plot generated by plot_4sites_distrib.m)
* Met with Dave today and we agreed that a main message of this analysis so far is that soil moisture is highly variable inter-annually, between sites. and even within seasons. There are a few somewhat predictable patterns though: 
  * Low elevation sites seem to show more summer drought
  * Soil moisture stays constant below winter snowpacks, but there is large inter-annual variability between winters. This probably depends on year-to-year differences in antecedent (fall) precip.
  * In general, soil moisture variability is higher at low elevation sites (especially outside summer months). This could be shown with a CV vs elevation plot perhaps.
* **TO DO:**
  * Explore the soil moisture CV vs elevation relationship (see above)
  * Need greater power for analysing case studies, including binning sites into climate-space envelopes. First this requires that we define ranges in elevation, MAT, MAP, SWE, melt timing, summer precip, etc, across the SNOTEL network. Second, how could we group sites according to particular criteria (High elevation sites with low snowpacks for instance.)
    * Such data could be used to select appropriate sites for case studies (such as replacing Chepeta in the figure at right).
  * Some of the temperature data from PRISM should probably be used in climate-space analysis rather than SNOTEL temp data.
  * There may be some interesting soil moisture patterns at monsoon sites that should be explored. The shape of the precip accumulation line might be useful for defining sites w/ summer rain.
  * Collect data from more sites - MT, AZ, NM are left.`

 **Jan 28, 2012**

* There are now some new testing functions in the SNOTELdata project. One that plots two datasets to view changes (useful for comparing filtered/unfiltered, or transformed/untransformed datasets) and one that will generate SNOTEL datsets with original values, or with missing columns or dummy values.
* The plot_monthly_sm_distrib.m file has been updated to show an all-years plot.
* Dave and I discussed doing some side-by-side comparisons of the quarterly histograms from several sites that would illustrate low/high elevation and snowpack scenarios.`

 **Jan 21-26, 2012**

{{
:west_stationdata:plot_monthly_sm_distrib-828wy2010.png?300|plot_monthly_sm_distrib.m
output for Trial Lake, WY2010]

* Created plot_monthly_sm_distrib.m to print a site's monthly histograms of all soil moisture data for each year in the analysis.
* Have been working on some testing functions for loadsnotel.m and the data cleaning/filtering routines.
* Possible test cases that involve replacement/addition of sensors between years are site 396 (Ts -2 disappears after 2004), and 435 (Ts -20 disappears after 2004).`

 **Jan 18, 2012** - Some initial goals:

* Each sensor needs to be normalized to 0-1 (after data cleaning)
* Plot histograms of the data during different time periods(months) of the year (some will be bi-modal)
* size of histogram modes indicate time sensor spends at particular value
* try plotting in 3d - see figure 6 in bowling_11 paper
* Next week - soil moisture distributions for 1 site, all months, 1 sensor depth.`

</file>

 **10/24/2012**

Stuff that would be good:

* summary file that has averages not based on wateryear, but based on all data
* summary file that includes integrals of monthly/yearly temperatures and vwcs (probably using interpolation to fill gaps).`

 **10/18/2012**

Things to try for comparing mean annual air temp and mean annual soil
temp:

* Integrating the timeseries of each, for a wateryear, and comparing them and the difference between them.
  * Maybe this could be done with cumsum or trapz in MATLAB - but data will need to be interpolated and we need to make sure each wateryear is the same length.
* Calculate degree days - not sure how yet.`

 **2/21/2012**

Couple ideas:

* Mean soil temp the week before snowpack onset and the day of snowpack onset.
  * Does this correlate with winter soil temp - especially early season?
* Mean air temp the week before, and after snowmelt day.
  * or offset b/t air and soil temps during spring.
  * what are the differences between early and late melt years?`

 **2/9/2012**

* Read the [Gubler`et`al`
`2011](http://www.the-cryosphere.net/5/431/2011/tc-5-431-2011.html)paper today.
  * Cool boxplots for site data might be a good way to summarize data
  * They have some interesting analysis of topography and elevation effects on ground surface temp, and we might be able to do something similar with our mean annual soil temps (year to year or aggregated by site).
  * Almost all their data is of MAGST - Mean annual ground surface temperature - maybe we need to look at means more.
  * Definitely see the Bartlett paper referenced here.`

 **2/03/2012**

![media/west_stationdata:828_distrib_allyrs.png?300|Trial Lake,
histograms from all water years combined.]

* Plotting of soil temperature distributions is now done in plot_soilsensor_distrib.m, replacing the program that created ``. The new output (for Trial Lake) is at right. This program plots histograms for individual water years, and all years combined.
* There is also a program that will combine quarterly distributions from several sites into one display for comparison of case-study scenarios (plot_4sites_distrib.m).
* Working on compiling SNOTEL climate-space data, including temperature, snowpack, etc, into a form that is usable for comparing contrasting sites, or groups of sites.`

 **12/9/2011**

* Figures from AGU 2011 poster:`

 **11/29/2011**

* Added a _baddata.txt to allsensors_daily file. Data is marked by site and year (calendar) mostly based on whether outliers showed up in the plot_ts_vs_snowpack.m plots. I looked closely at all data I marked to be certain that there were actual sensor irregularities (not just outlier data).
* Filtered out these datasets in plot_ts_vs_snowpack.m.`

 **11/23/2011**

* Should I plot some of these vs time? Show temp offset in each month, then year to year?
* At a site, what is the difference in mean below-snow or monthly below-snow soil temperature between years? Are these differences correlated with any snowpack characteristics (onset, depth, SWE, air T)?
* Is there a generalized soilT timeseries shape that varies according to snowpack (onset, depth, SWE, airT)?`

 **11/17/2011**

![media/west_stationdata:soiltvssnowpack_wu.png?300|February soil temps vs
snowpack at 2 depths in the Wasatch and Uinta mountains]

* Might make sense to create a function that generates lists of sites based on certain criteria like: mountain range, state, elevation, latitude, etc.
* Created plot_ts_vs_snowpack.m to examine the monthly relationship between soil temp, SWE, and snow depth in individual years (data are not averaged across years). Also examines wasatch vs uintas.
* Looks like soil temp needs some additional filtering routines.`

 **11/11/2011**

* Some thoughts about where to go from here
  * Complete what was  said in part 1 above (10-7)
  * There are equations that describe the sinusoidal pattern of seasonal temperature and we could probably base these on air temperature for SNOTEL sites - how do these differ for a snow-dominated and non-snow dominated soil
  * Winter soil temps are only half of a sinusoid, so maybe there is a way to model seasonal soil temp in both snow-free and snowcovered periods separately.
  * How does that seasonal pattern change when you change snowpack parameters (depth, accumulation timing, meltout, etc) and can we model that accross our sites?
* For Moisture:
  * Does damping depth vary seasonally and interannually and is this controlled by moisture content?
  * How far out of phase are precip and soil moisture recharge? - maybe for this investigate that elbow between winter and summer in accumulated precip you can see in SNOTEL data.
  * Where does summer rain come in (again, those accumulated precip graphs, especially their slope, might be useful)

 **10/7/2011**

* Need to separate different years of data for each site and evaluate influence of snowpack at each site - identify whether low-snowpack years (or late snowpack years) are correlated with low soil temps (for a month or the entire year), length of time with stable winter soil temps
* But say sites show varying influence of snowpack size or timing - how do we demonstrate the importance of this dependence across the landscape?`

 **9/13/2011**

![media/west_stationdata:snotelsoiltvssnowpack.png?300|]

* It appears that there is a relationship between soil T and snowpack that is present in February - sites with low snowpacks (in depth or SWE) have colder temperatures and temperatures increase as snowpack increases. The strength of this relationship seems to drop off as soils reach 1-2°C. The graph at right illustrates this. Note that these datapoints are aggregated data for all soil and snowpack data from the selected months for a site. Individual years may show a stronger pattern.`

 **9/6/2011**

* A next step for temperature analysis: what is MAT for soils vs air temp along an elevation gradient?
* Can we add PRISM MAP and MAT to this analysis?`

 **8/24/2011**

* Added daily, all-sensor data from ID, WY, and CO to the analysis
* Generated a file with all long term(71-00) SWE and Precip values for UT, NV, MT, ID, WY, CO, NM, AZ. This amounts to 494 sites total.
* Now need mean soil and air temperatures for different months to go with the 71-00 averages above.
* Working to produce a graph of Lom`

 **8/10/2011**

* Figures from my commitee meeting (that have to do with SNOTEL data analysis)

 **8/9/2011**

* New file: //filterseriestest_scr.m// should be able to test different filtering regimes and show the changes in data
* New [file://tempswegradient_scr.m//](file://tempswegradient_scr.m//)plots February soil temps against a variety of things including SWE, Snow depth, and elevation.`

 **8/5/2011 - TO DO **list for west_stationdata programs:

* //loadsnotel.m//
  * Decide what to do with quality control arrays
  * What filtering should be included, some of the bad data removal seems redundant, and might be better put in filterseries.m
* //filterseries.m//
  * Filtering thresholds should probably be set here, or there should be an option that pops up for each filter pass.
  * There could also be a way of determining the optimum filter threshold for each sensor (separate from this program).
  * Filtering thresholds should also be different for winter or summer
* //swe_snowcover.m//
  * Should probably be changed to reflect that this is a daily-hourly conversion - and it may be useful for more than snow data
* //sitesoiltempvariability_scr.m//:
* //monthlysoiltempgradients_scr.m//:`

 **8/4/2011**

![media/west_stationdata:monthlysoiltempgradient2.png?350|]

* //sitesoiltempvariability_scr.m//:
  * Added routine to convert daily SWE data to hourly values matching the hourly soil data. This can then be used to create a logical snowcover test.
* //swe_snowcover.m// - **New** - Uses routine developed above to take hourly decday vector and SNOTEL site id and returns a logical snowcover array for the data.
* //monthlysoiltempgradients_scr.m//:
  * using swe_snowcover.m to test for snowcover now
  * adding site data and a "havedata" routine to the program to use this data. Should be more extensible.
  * Common error: if hourly datasets begin prior to daily datasets there is an empty matrix error in the daily-to-hourly snowpack conversion searches based on hourly data first.
  * Still missing data in September - and this may be due to the filtering used (it was pretty restrictive when the figure above was produced).`

 **8/3/2011**

* //loadsnotel.m//: 
  * No longer removing data marked in qc column because it removes too much good data, just leaving qc for reference. Other filters should do a good enough job of getting rid of this problematic data.
  * Inserting routine for removing repeated, non-daily rows from daily datafiles
* //filterseries.m//:
  * Fixed this so that mean and shift diff filters should both work - but needs checking
* //sitesoiltempvariability_scr.m// Experimenting with different filtering calls and making sure they work ok. Need to decide on one that works for the most sites.`

 **6/14-15/2011**

* Downloaded lots of new daily datafiles from NRCS site
* Created a filelist (filelist.txt) and a bash script to create this list (filelistgenerator.sh). The textfile lists the site number once for each yearly datafile in the directory. Thus it can be read to inventory how many sites have data, and how many years of data each site has.
* Created a new spreadsheet with 30-year average SNOTEL data (SWE and precip) and exported a textfile to the SNOTEL_data folder for use in scripts (see below).
* Created a new script (for now called tempsweelev_scr.m) to plot air temps (MAX and AVG), soil temps, average SWE, and average precip for July and January and plot them across the elevation gradients chosen.`

 **5/18/2011**

* The Snowbird(766) -2in sensor is messed up - during summer its ranging from 45 to 10 degrees C. Maybe the sun hits it or there is a heat conduction problem or something.`

 **4/29/2011**

* Filtering routines (in sitesoiltempvariability_scr.m) moved to filterseries.m, and added interpolation after the filtering
* sitesoiltempvariability_scr.m still checks mean differences and shifted differences to test the effectiveness of filtering
* Interpolation should come before filtering since filtering generates a runmean with larger gaps.
* Interpolation takes place in sitesoiltempvariability_scr (to Ts) then after filtering in filterprofileseries.m
* FIXME There is missing data in Sept in monthlysoiltempgradients_scr.m outputs - why?
* FIXME Interpolated data leads to low standard deviations in the running calculation, so these need to be corrected somehow 
  * This can lead to errors in separating snowcover from snowfree periods
* Perhaps a logical matrix that accumulates interpolated datapoints should follow the Tsoil array around.
* FIXME Also, there are still periods in winter that read as snow-free, so maybe a test that adds pillow SWE readings to determine snowcover.
* FIXME Shift difference filter doesn't seem to be working right (see histograms compare unfiltered and filtered data)

 **Apr 26, 2011 - Fixing runmean nan problem **{{
        :west_stationdata:ts_interp.png?250|Interpolated points (red)
        in Ts data]

* Interpolate the data using interp1
* generate the mean with something besides filter (something with better nan handling) - can't get these to work well.
* Have added a routine to soilTvar.m that can interpolate missing data in a soil temp timeseries - see figure to right. This is better than interpolating the runmean. Should probably add this to NWCC_load.m or create a separate function to call so that programs could be run with or without interpolation
* Doesn't seem to work well for some sites (run with 972) - seems to interpolate to values that aren't there.
* These wierd interpolations happen at the beginning of dataseries if the data starts with long stretches of bad data.
* **Filtering routines:**
  - remove sub-hourly rows - loadsnotel
  - remove datalogger error signals -99,9 and -273 (via qc column) - loadsnotel
  - FIXME - this often removes good data (see 971 or 972)
  - remove SM values that are 0 in winter(via qc column) - loadsnotel
  - mean difference filter (Ts-run mean > ???) - loadsnotel
  - remove Ts values greater than 30 and less than -10 - loadsnotel`

 **TO DO for 4-27-11 meeting:**

- Separate filtering functions - loadsnotel.m removes errors, filter function uses mean and shift filters on a data series.
- Make soilTvar present data for unfiltered data, and both filters separately and together
- Get an interpolation function working (must remove or handle leading NaNs)
- Then run soilTelev with new filtering routines.`

 **Feb 23, 2011**

![media/west_stationdata:828_soildist.png?250|Trial Lake -2cm soil temp
distributions at various time periods (~2002-2010)]

* Downloaded and edited [inventory`files`for`NWCC`
`SCAN/SNOTEL`
`stations](http://www.wcc.nrcs.usda.gov/nwcc/inventory)in Intermountain west states (those listed above)
* First figures came from plot_seasonal_ts_distrib.m program. Figure for Trial Lake snotel site at right 
* **soilTvar helps with:**
  * Selecting thresholds for distinguishing snow and snow-free periods
  * Choosing thresholds for diff filtering
  * Choosing thresholds for shift filtering
* **PROBLEMS**{{  :west_stationdata:ts-snowtestfailinwinter.png?300|]
  * The program doesn't appear to separate snowcovered from snowfree periods very well. This might be because of NANs in the running standard deviation array used to create a logical test.
  * There are also imaginary numbers in runstd. These result from taking the square root of a variance array that includes negative numbers. Variance should always be positive (it is the sum of squared values), but apparently there can be problems when calculating variances over large arrays of near-zero numbers, or numbers that are similar (see [here](http://www.johndcook.com/standard_deviation.html)or [here](http://en.wikipedia.org/wiki/Algorithms_for_calculating_variance)). So, I need a better algorithm for calculating variance of winter Ts and then its StdDev.
  * Maybe... RUN A TEST AGAINST THE IMAGINARY NUMBERS AND SET TO NAN... didn't seem to do much. Looks like imaginary numbers test as less than the threshold (0+0.342i < 0.1 = true), so they should be flagged as snowcovered anyways.
* Setting nans to be snowcovered periods helped, but now there is "snowcovered" data where there are NaNs in summertime.
* NaN's always test as not snowcovered (NaN < 0.1 = false), so this would explain why there are "snow-free" periods in winter - its the NaN's that are flagged as snow-free no matter what.
* ** Ways to fix this:**
  * There are nans in snowcovered and snowfree seasons, so need at least two logical tests - one for nans in each season.
  * Test out nans in snow season only
  * Create a logical test matrix for nans and then backfill the nans into the Ts array after running the test.
  * Reduce the number of nans
  * RUNMEAN function generates lots of nans from a few in the soil temperature array! FIXME!!!`
