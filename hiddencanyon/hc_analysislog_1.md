###### Hidden Canyon data analysis

This log mainly covers analysis of Hidden Canyon ecohydrology experiment
data [(Project overview)](hc_ecohydrology:overview).

 **See also:\*\* The [Data program
        documentation](hc_ecohydrology:programdocs), and the
        Hidden Canyon [site
        description](hiddencanyon:sitedescription).

------------------------------------------------------------------------

 **03-20-2012\*\*

Re-analyzing photos from 4/24/2012 (swe locations before leafout) again.
In addition to the standard settings (see <procedures:canopyphotos>) I
am using these settings.

` * This time am using growing season Mar. 1 to June 30.`\
` * Using HCfullmask.msk.`\
` * Using the blue color plane filter.`\
` * Pixel count around 140-190, usually around 160`

 **12-14-2012\*\*

` * Have been working on analyzing the snowmelt data from Hidden Canyon using a linear mixed effects model. Here are a few items to remember to try when I come back to this after Xmas:`\
`   * Plot "ΔSWE" for individual SWE measurement locations, and for control/dust-addition blocks (in python or R). I'm curious as to whether these are linear over time, and whether my linear model might need to be adjusted (should it be non-linear?).`

 **May 16\*\*

` * Went through calibration data and removed bad peaks. There were many for 2-21 injections. This lowered the error for the runs, but I wonder if it really makes the data any better. If the calibration injections were off, then it is likely that the sample injections are too. Would it be best to just remove 2-21 injection and only use the 3-13 injections for the same samples?`\
` * I5 caltank injections still seem to be calculated as high ppm values, and I'm not sure why this is. Could it be the linear fit equation? Maybe the fit isn't linear across the 15000ppm range and the calculated values at low ppm are affected more?`\
`   * Indeed - ran some injection data with a second order polynomial (in process_injectiondata.m) and the fit is much better (3-28 data - first order = 19.7rms, second order = 3.8rms). So, change all or some of the injection runs to second order fits?`\
` * Made the call to use first or second order for each run based on what gave a lower rms error. Currently this data is the data in processed_data/snowinlets.csv.`\
` * Also removed inlet samples for 2/21 run from analysis and am relying on the 3/13 repeats (because 2/21 run was so bad). However, I left the atmospheric samples in for calculating fluxes.`

 **May 15\*\*

` * Inlet data is now plotted with plot_inlets.py`\
` * Make sure all datalogger data (Met1 at least) is up to date.`\
` * One bad peak for 3-13 run: [50]`\
` * Something is up with calibrations, especially for I5 tank, and looking at the qc plots generated with process_injectiondata.m, it seems like several injection dates are pretty noisy. Check this and figure out why. `\
` * Probably would be a good approach to plot calibration data over the entire 2011 and 2012 year in plot_inlets.py, then mark bad calibration injections in the datasheet/csv.`

 **March 14, 2012\*\*

` * Added a way to remove bad peaks from while running process_injectiondata.m. It is now necessary to look at the second plot and figure out which peaks are erroneous and then enter them at the command line. Still not sure why they are there, but it looks to have something to do with my injection technique.`\
` * Need to do some serious data/error checking in the injection to ppm to respiration rate calculations.`\
` * Last set of injections (2-21) look pretty bad, so I reran the samples from that day and will hopefully have better numbers.`\
` * When I run the 2-21 samples, the bad peaks that need to be selected are [22, 24, 35, 42, 43, 47, 51]`

 **Feb 21, 2012\*\*

` * Did a new run on the injection system and then ran the data through process_injectiondata.m and it failed. Apparently there are little mini-peaks after the injection peaks that Matlab is reading as separate injections. Will need to fix this and run the data again.`\
`   * The mini peaks occur after the highest standard injections (14,000 ppm) and may be the result of a faulty syringe (though I have no idea why...).`\
`   * The culprit is the CV method of discovering peaks vs inter-peak readings (which are flat).`

 **Feb 9, 2012\*\*

` * Created scripts to convert Forest1 v3 and v4 datafiles to a format compatible with v6 (in py/fileconverters/), and put the resulting files in the rawdata folder for the project.`\
` * Created a parsefile for both dataloggers that provides variable names based on the datalogger program output (Met1, and Forest1 v3, 4, and 6). This is used in file converters and the check_hc_datalogger.py programs (and others in the future).`\
` * Updated loaddata/loadDatalogger program to load Forest1 v6 data, as well as the new converted files correctly. Also tweaked the way it removes bad data.`\
` * check_hc_dataloggers.py has also been rewritten to plot output from all sensors, and it has better datetime handling (using a new function in loaddata module.`\
` * **TO DO:**`\
`   * Make Sentek sensors at profile 10 work - will probably require a tweaked datalogger program.`\
`   * Locate and remove more bad data - probably need a "bad data log" file somewhere to read.`\
`   * Make a function to convert Decagon outputs to actual temp and vwc numbers (in loaddata?).`\
`   * Convert snowpack CO2 measurements to fluxes.`

 **Jan 31, 2012\*\*

` * Have compiled all data from the dataloggers into a couple of files that correspond to the datalogger programs they come from. There is a v3 and v4 datafile from Forest1, and the current data from v6 program is being appended to HC_F1_append.dat.`\
` * Now trying to figure out how to view this data effectively with all these different versions.`

 **Jan 9, 2012\*\*

` * Wrote process_injectiondata.m to process datafiles and calibrate peak areas from the new CO`~`2`~` injection system.`\
` * New datafiles from injection runs will go in rawdata/hiddencanyon/co2injections. Once processed, the data from these files must be merged into the injection datasheets.`\
` * data_analysis/hiddencanyon is now fairly well organized, except for trees/ directory.`
