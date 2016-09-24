# Niwot Girdling Activity log

This log mainly covers ...

 **See also:\*\* [Data QC](data_qc), [Soil analysis
        methods](soilanalysis)

------------------------------------------------------------------------

 **3/7/2014\*\*

` * Approaching a workable method for soil extracts. More testing next week.`

 **1/6-7/2014\*\*

` * Did QC of final dogbone samples from Nicole - they seem ok (see 2013 output from irga_gasbench_process.m).
` * 2011 bulk soil samples (from flask sampling) were sent to Sirfer`

 **6/25/2013\*\*

` * Subsamples (~3ml) of all extracts were sent to Kiowa lab today for TOC/TN analysis. Coordinating with Holly Hughes.`

 **4/25/2013\*\*

` * Have begun grinding flask soils from July 1, 2011
` * Working on method for %C and 13C of soil extractions (fumigated and non-fumigated). See `[`here`](soilanalysis)

 **4/11/2013\*\*

Now have data for soil and flask data.

` * Need to plot soils with flask data.
` * Also try plotting values of respiration/bulk d13C components (from Sean Schaeffer)?`

 **2/12/2013\*\*

Have finished making a bad data removal routine for the soil CO2 data.
See the [data QC page](niwot_girdling:data_qc).

 **2/11/2013\*\*

I am making local copies of my scripts, and giving them my own naming
system. I will place them under version control with
[Mercurial](procedures:mercurial).

 **2/7/2013\*\*

` * We now have all the soil CO2 data back from Brad and it all plots fine in MATLAB.
` * I'm making a `[`data` `QC`
`page`](niwot_girdling:data_qc)` to keep track of how we clean this dataset.`

 **1/31/2013\*\*

` * Got a new script going - Niwot_2011_dogbone_workup_130130.m. This makes the 2 plots from the poster for either 2011 or 2012. Will rename.
` * There is still bad data being plotted though, and I think this will need to be addressed in the Niwot_gasbench_ver3GM.m file with some input from one of Dave's workbooks.
` * Note that in the compiled.GB.data.130130peak1.xls file, the 13C number for sirfer#12-11224 comes from peak 2, because peak 1 was too low. Can't seem to make that note without screwing up xlsread in matlab`

 **1/28/2013\*\*

` * Ran another set of vials - FEF 9/21/2013.
` * That is the last set.`

 **1/25/2013\*\*

` * Ran another set of vials - NWT 9/24/2013.
` * Replaced all septa`

 **1/24/2013\*\*

` * Ran another set of vials last night and took them to Brad - FEF 9/4/2012.
` * Met with Dave and for next week I need to- 
`   * Finish the exetainers
`   * Run the data for 2012 through niwot dogbone workup script and reproduce last year's poster plots for 2012.
`   * Remember to use time since disturbance as the x axis rather than year of disturbance.`

 **1/20/2013\*\*

` * Ran another set of vials - FEF 8/8/2012.
` * Replaced all septa`

 **1/17/2013\*\*

` * Ran another set of vials - NWT 8/27/2012.
` * Met with Dave. We have 4 more sets of vials to run at SIRFER. When these are done the next priorities are
`   * Work up the data for 2011 and 2012 (dogbone_workup file)
`   * Run one sampling date of bulk organic samples (24 organic and 24 mineral soil samples) at sirfer for %C and 13C.
`   * Work out a method for running the extracts - %C, %N, and 13C`

 **1/10/2013\*\*

` * Ran another set of vials - FEF 6/14/2012.
` * Replaced all septa`

 **1/4/2013\*\*

` * Ran another set of vials - NWT 7/2/2012 and took this and NWT 6/18 to Brad.
` * Data is looking mostly fine at this point.`

 **12/20-28/2012\*\*

` * Ran 2 sets of vials:
`   * FEF 6/26/2012 - all went well
`   * NWT 6/18/2012 - Had to replace an injection needle and there were problems with standards following this. 4 peaks were removed from the compiled CO2 file. 
` * Replaced all septa.`

 **12/17/2012\*\*

` * TO DO:
`   * Create 2 new datafiles - One with mean peaks for 2012, one with only peak one
`   * Also, get rid of 2011 "reanalyzed" column. Its a legacy of 2011 and we can use that all the time now.
`   * Plot 2012 data (13Cvs area) over QC'd data from 2011.
` * Found some duplicate vials for the 120724 FEF sampling date. There 2 vials each for 110-0, 110-161, and 110-488. Not sure why, but I suspect that one set is from a different plot and they were mixed up. Not sure which other plot appears to be missing yet.
` * It is looking like all the wierdly enriched samples came from NWT on 7-17-2012 - this may not be a sirfer problem.`

 **12/10/2012\*\*

Got some data from Brad (4 sets of vials). Currently working it over.

` * Some vials are being re-run more than once this year, and that is creating some problems with the script I am using. Can separate these out using the run number.
` * At the sampling on 7-24-2012 (FEF) plot 110 was sampled twice. Either this, or it is mismarked. Mismarked is a possibility because plot 104 is missing in this set. Not sure what to do here. Will look at the vials, but I think it will be hard to figure out what happened here. For now I have marked them as run 2 to keep them separate.
` * Have made some changes to the compiled.CO2 and compiled.GB data files. Added a run # field to CO2 and standard deviation and peak amplitude to GB data files. These are reflected in the new version of the scripts that read those files.`

 **11/12/2012\*\*

Met with Brad and Dave to discuss a way forward with the OA(surface)
dogbone samples that have high 13C standard deviations.

` * According to Brad, the main option we have is to run all the CO2 in an exetainer at once (by cryotrapping and sending it all to mass-spec). This would give us a larger peak, which should be more accurate. However, we can only do one measurement per sample (so no StDev).
` * For now, we will have Brad process 4 more dates (2 from NWT and 2 from FEF) and then do some analysis of those to see how the OA samples look
` * Also need to compare data from dogbones to TDL data from 2011 and 2012. Dave sent data in a .mat file.
` * Plotting changes:
`   * Change order of histograms to reflect depth (top plot = shallow dogbones) in dogbone workup script.
`   * Do some plotting of `^`13`^`C StdDev and mass spec peak area.`

 **10/29/2012\*\*

Ran another injection series with the IRGA (FEF 120823).

` * Changed all septa.
` * This time I turned up delivery pressure and cleaned the syringe. RMSE looks about the same, and the bad RMSE is probably due to just one or two injections that are much higher than the rest. 
` * Maybe I will try a new syringe next time?
` * Also ran the Niwot test samples that Nicole sent (6 samples, taken during radiocarbon sampling).`

Also, received one set of data from Brad. It looks like the surface
samples produce small peaks, and therefore high standard deviations for
13C. I asked Brad if it would be better to run larger samples for these.

 **10/15/2012\*\*

Looked at data from the first two gasbench sample sets, and all IRGA
dates (up to 10/9). Met with Dave about this.

` * Gasbench data look ok, but there have been some x-axis shifts in the calibration. Peak area given by the mass spec has changed, and its relationship to 13C appears to have changed. Will meet with Brad about this.
` * IRGA data has a bit higher RMSE than last year (~10). It appears that the A tank (~390ppm) is reading a bit inconsistently when injected into the IRGA. Two things to try:
`   * Clean the syringe plunger
`   * Turn up the delivery pressure on the cal tank regulators. `

 **10/9/2012\*\*

Ran a bunch of FEF samples on the IRGA today. Some of the A cal
injections were below the 100ppm threshold for the processing program to
count them as peaks. Could this be because the pressure is low in the A
tank? Or are the samples becoming a bit more moist and it is water vapor
causing this problem. The IRGA seems to be wandering a bit more overall,
so perhaps I need to check for leaks or something.
