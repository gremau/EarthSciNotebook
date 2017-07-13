
# NMEG flux processing workflow (MATLAB version)

These are the basic steps/scripts for generating 30-minute averages and calculating fluxes from our 10hz data at each site.

1. `UNM_process_10hz_main.m` is the primary script for processing 10hz data in TOB1 files.
    * Generates list of daily TOB1 files (in 30 day chunks by default) for processing by `process_TOB1_chunk.m`
    * Concatenates the resulting data.
    * Default sonic rotation is 3d (3-axis or double rotation)

2. `process_TOB1_chunk.m`
    * Read TOB1 files in each 30 day chunk, break into 30min blocks
    * Send each 30min block to `UNM_30min_TS_averager.m` and then concatenate resulting data.

3. `UNM_30min_TS_averager.m`
    * Calculates average values for 30 minute blocks of 10hz data, including calculated fluxes. In the process of doing this it calls:
        - `UNM_dry_air_conversions.m` which calculates Tdry, despikes pressure data, and does other conversions.
        - `UNM_csat3.m` which despikes u, v, w wind data, adjusts THETA using the site-specific sonic orientation, and calculates 30min averages of wind data.
        - `UNM_coordrot.m` which provides the coordinate rotation for flux calculations. Default is 3d, which is not ideal, but there is a method for planar rotation here too.
        - `UNM_flux_031010` which calculates the covariance matrices for wind and scalar data, performs raw flux calculations and corrections (see sub-bullets). This code can loop using different lag times, but the default is no lag. It returns a 30 minute flux observation. The corrections called are:
            * `UNM_WPLMassman.m` which calls `UNM_Massman.m`. These two scripts perform the high frequency loss correction (Massman method), and the Webb, Pearman, Leuning density corrections (in that order).
            * Linear detrending of variables has in the past occurred in the `UNM_Massman.m` code, but it appears that this is no longer the case.
            * The WPL correction may actually be done at the very end of this script (needs to be checked) and that becomes the 'FC_corr/raw_massman_ourwpl.m' flux.
    * The `UNM_30min_TS_averager.m` then puts these together and returns met and flux averages for the 30 minute period.

The steps above create a dataset that is merged into the SITE_fluxall.dat file. There are additional steps that occur in the `RemoveBadData.m` script. These are:

1.  Burba correction (T below 0 C)
2. Lots of hi/low filtering, flux removal based on precip, behind tower wind, nighttime negative fluxes, low ustar values, outlier removal,
        
