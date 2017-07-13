# RemoveBadData.m primer

This is a brief tour of the `UNM_RemoveBadData.m` script that filters all our flux data. I am making this so I can figure out how to improve this script.

Script settings (L67-106)
--------------------------------
Reads in arguments, prepares input and output filenames, switches on or off various analyses and outputs.

Note that this is where iteration number is set. Its default is 6, which means all iterations are run

Site/Year parameter setting (L107-275)
---------------------------------------------------
For each site set the ustar threshold, standard deviation filter,  hi/low values for met and micromat variables.
Some sites have changing parameters for different years.

Parse fluxall, shift timestamps, assign variables (L276-538)
------------------------------------------------------------------------------
1.  Parse the fluxall file (`UNM_parse_fluxall_txt_file.m`) and pull out size, etc.
2.  Shift the timestamp data in the file using `UNM_fix_datalogger_timestamps.m`
3. Assign a bunch of met and micromet variables from the fluxall data.
4. There are also a few unit conversions in this section.

Soil data assignments (L539-665)
------------------------------------------------------------------------------
This section mainly assigns the proper soil header to the a particular variable and applies conversions and calibration factors.

Radiation corrections (L666-704)
--------------------------------------------
1. Calibrate radiation measurements with `UNM_RBD_apply_radiation_calibration_factors.m`
2. `UNM_RBD_calculate_net_radiation`
3. `normalize_PAR_wrapper`

Burba correction (L705-773)
--------------------------------------
This code applies the Burba 2008 correction for sensible heat conducted from a LiCor 7500 during flux measurements.

Iteration 1 - Coarse CO2 flux filters and ustar (L775-900)
-------------------------------------------------------------------
Sets up qc flags and removes bad data periods for:

1. Precipitation
2. Wind direction
3. Night time negative fluxes
4. Night time cold air drainage (PPine only)
5. Bizarre periods at SLand and Grassland in 2007 and 2009

Also makes a plot that can be used to decide the ustar threshold. This should then be entered in the site/year parameter block above (Check this!).

Iteration 2 - Ustar threshold filter (L902-918)
--------------------------------------------------------
Remove periods below ustar threshold above.

Iteration 3 - Min and Max CO2 flux values (L920-973)
-----------------------------------------------------------------
1. Remove a variety of problems at particular sites and years with `remove_specific_problem_periods` function.
2. Select some daily max and min CO2 values using `get_daily_maxmin` and the monthly CO2 thresholds specified above.
3. Allow exceptions to this filter with `specify_siteyear_filter_exceptions` function.
4. Remove and tally the max/min CO2 periods.

Iteration 4 - High and low CO2 concentration filter (L975-1015)
------------------------------------------------------------------------------
1. Find high CO2 values ( >450ppm )
2. Specify some exceptions to this filter with `specify_siteyear_co2_conc_filter_exceptions`
3. Remove some site-specific low CO2 periods

Iteration 5 - Apply running StdDev filter (L1017-1183)
------------------------------------------------------------------
Appears to be a 1 day StdDev period

Plot the entire NEE series with filter results (L1185-1126)
-----------------------------------------------------------------------
Plot with `plot_NEE_with_QC_results'

Filter sensible heat (L1127-1272)
-----------------------------------------

Filter other variables (L1273-1381)
-------------------------------------------
* Latent heat gets corrected then filtered
* Then filter temp (sonic), rH, h2o mean, pressure, soil heat fluxes.
* There are also some site/year specific data removals at the end of this section.

Print number of removals (L1382-1399)
--------------------------------------------------
To screen, but should probably go into a log also.


Prepare and write `for_gap_filling` file (L1400-1511)
------------------------------------------------------------------
There is some funky data removal at the end of this section also.

Prepare and write `_qc` file (L1512-1629)
-----------------------------------------------------

Mysterious outfile preparation (L1631-1747)
--------------------------------------------------------
Seems to tally removed data, but cannot tell if it actually is output at some point.

Functions (L1749 ->)
--------------------------
1. `normalize_PPine_NEE`
2. `get_daily_maxmin`
3. `remove_specific_problem_periods` (this is huge L1799-2059)
4. `specify_siteyear_filter_exceptions` (also large L2060-2422)
5. `co2_conc_filter_exceptions` L2423-2478
6. `format_SHF_labels` L2481:end
