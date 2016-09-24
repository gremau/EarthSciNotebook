###### Program documentation for western U.S. station data analysis

These are program file descriptions for programs used to analyze data
supplied by the NRCS. Analysis of soil profiles at these data stations
relies heavily on techniques [described
here](procedures:sensordata_tips).

 **See also:\*\* [Project overview](overview), [Data
        collection/prep](west_stationdata:data), [Data
        analysis log](west_stationdata:analysislog_1), [Data
        quality control](west_stationdata:data_qc)

##### Scripts

Run as a list of commands that result in some data analysis result. They
generate plots or some kind of report output that interprets the data in
some way. They usually call functions (like those below) to accomplish
this.

### soildataQC.m

FIXME - NEEDS TESTING

Plots data and 24hr standard deviations for 5cm soil temperature.
Performs statistics on these data and 2 filter types. Useful for
checking data filtering/filling procedures, determining snowpack
presence thresholds, and filtering thresholds.

` * **File inputs:** Loads hourly and daily data for a selected site.`\
` * **User Input:** Takes one user input: site ID (integer)`\
` * **Output:** ??`\
` * **Other:** formerly plot_site_ts_variability.m`

### summarize\_wateryear.m

Takes daily raw data files, and long term averages for all sites,
calculates a variety of climatic metrics for each water year, and
summarizes these data in a text output file.

` * **File input:** Reads `*`rawdata/allsensors_daily/sitelist.txt`*`, and `*`rawdata/soilsensors_hourly/sitelist.txt`*`, `*`7100Avg_SWEmm.csv`*`, `*`7100Avg_Precipmm`*`, and `*`SNOTELinventory.csv`*` in processed_data directory.`\
` * **User input:** The user selects whether to run with hourly/daily data, and normalized/non-normalized soil VWC data. `\
` * **Output:** `*`wyear_climatesummary.txt`*`, `*`wyear_soiltempsummary_XXX.txt`*`, `*`wyear_soilwatersummary_XXX.txt`*`, and `*`wyear_soilwatersummary_XXX_smnorm.txt`*` (XXX = `*`daily`*` or `*`hourly`*`).`\
` * **Associated files:** I use the `*`headersXXX.txt`*` files to keep track of what the headers for the output files should be.`\

### plot\_snotel\_summary.m

Reads the outputs from summarize\_wateryear.m (see above)and makes a
number of plots characterizing variability in soil moisture and soil
temperature in the SNOTEL network.

` * **Input files:** `*`wyear_climatesummary.txt`*`, `*`wyear_soiltempsummary_XXX.txt`*`, etc.`\
` * **User input:** The user selects whether to run with normalized/non-normalized soil VWC data. `

### plot\_soilsensor\_distrib.m

Plots distributions of soil sensor data for one site in individual
months and years. Data for all years (available) is represented.

` * **File inputs:** Loads hourly data for a selected site.`\
` * **User Input:** Takes three user inputs: site id, sensor type (vwc or temp), and sensor depth (1=5cm, 2=20cm, 3=50cm).`\
` * **Output:** First produces a plot with timeseries of selected site sensor data at each available depth, then a 16 panel plot for each wateyear, and one using data for all years. Each 16 panel plot has 4 quarterly histograms and 12 monthly histograms of the soil sensor data selected.`\
` * **Other:** Can optionally be run in normalized soil moisture mode (make selection in code).`

### plot\_examplesites.m

This makes a number of figures that highlight snow-soil interactions at
particular sites.

` * **File input:** The first 4 figures directly load hourly or daily data. The last 2 use the summary files`\
` * **User input:** User can select different sites to plot in figs 2, 4, 5, 6 in the code`\
` * **Output:** Produces 6 figures, all are ready for publication:`\
`   * Fig 1 = 2 year SWE/temp comparison at Mosby Mtn.`\
`   * Fig 2 = Multi-year SWE/Tsoil/VWC time series at a site (changeable)`\
`   * Fig 3 = Full VWC timeseries of 4 sites - the data for Fig 4 `\
`   * Fig 4 = VWC Frequency histograms for 4 contrasting sites (changeable)`\
`   * Fig 5 = Scatterplot/Regression of snowcovered Tsoil vs pre-onset T at 1 site (changeable)`\
`   * Fig 6 = Scatterplot/Regression of summer (JAS) VWC vs meltday at 1 site (changeable)`

### plot\_t\_elevgradient.m

Plots elevational gradients in air and soil temperature, and the offset
between the two, including comparisons of growing season vs winter
months

` * **Input files:** Reads `*`filelist.txt`*` from the daily and hourly rawdata directories, climate and Tsoil summary files, and SNOTELinventory.csv`\
` * **Output:** Many plots are produced, some for publication.`

### plot\_belowsnow\_ts.m

Plots Tsoil and Tsoil-Tair vs SWE for SNOTEL sites (and subsets of
SNOTELS), and fits some lines to the data.

` * **Input files:** Reads `*`filelist.txt`*` from the daily and hourly rawdata directories, climate and Tsoil summary files, and SNOTELrangelists.`\
` * **User input:** None`\
` * **Output:** About 7 plots are produced, some ready for publication`

### plot\_belowsnow\_sm.m

Plots below-snow soil VWC vs pre-onset VWC, snowpack, etc for SNOTEL
sites (and subsets of SNOTELS), and fits some lines to the data.

` * **Input files:** Reads `*`filelist.txt`*` from the daily and hourly rawdata directories, climate and VWC summary files, and SNOTELrangelists.`\
` * **User input:** `\
` * **Output:**`

### plot\_growseas\_sm.m

Reads SNOTEL data files and makes plots characterizing growing season
variability in soil VWC (entire network or individual sites), and its
relationship to snowpack.

 **-   Input files:\*\* Reads climate and VWC summary files.

 **-   User input:\*\* None, but individual site plotting can
            be changed.

 **-   Output:\*\* About 8 plots are produced

##### Functions

Do things to the data: load it from file, filter it, calculate
statistics or other values, generate secondary data to the original data
downloaded from the NRCS. They usually take input arguments and generate
an output, and can be called from scripts or other functions.

### loadsnotel('interval', siteID)

Parses headers and loads desired fields from NWCC (SNOTEL/SCAN) yearly
datafiles into one standardized array, removes bad data, returns array +
headers.

`   * Needs a column order/number check routine...DONE --- //`[`Greg`
`Maurer`](primaryproductivity@gmail.com)` 2011/03/24 21:18//`\
`   * FIXME - Needs a method to verify incoming data files for sample interval, and whether the file is complete (0ct1-Sept30).`

### load7100Avg(desiredAvg)

Loads long-term average SWE or Precip data for all sites using a curated
datafile and returns the array.

` * **Arguments:** `*`desiredAvg`*` = 'swe' or 'precip'`\
` * **Input files:** Reads `*`curated_data/7100Avg_Precipmm.csv`*` or `*`7100Avg_SWEmm.csv`*\
` * **Output:** Outputs an array with site ID, elevation, monthly/bimonthly precip or SWE, and total precip/maxSWE (see input files).`

### filterseries(array, type, threshold)

Filters soil profile data series using a difference from the mean, or
difference from neighbor

` * **Arguments**`\
`   * `*`array`*` = input data series`\
`   * `*`type`*` = 'mean', 'median', 'shift', 'sigma', or 'hampel' filter type`\
`   * `*`threshold`*` = threshold difference above which datapoint is set to nan`

### interpseries(array)

Interpolates over gaps in a timeseries. It should fill all NaN's with an
interpolated value. The actual interpolation is done by the Matlab
*interp1* function using the "pchip" algorithm. This can be useful for
running mean and variance calculations which tend to propagate NaN
values in a timeseries (see documentation for *filterseries.m*). Ignores
trailing and leading NaN. Adapted from FIXGAPS routine on Matlab Central
file exchange, by R. Pawlowicz 6/Nov/99

` * **Arguments**`\
`   * `*`array`*` = input data series`\
` * **WARNING:** If array contains only NaN's, interp1 throws an error.`

### soiltemp\_snowcover.m

Takes soil temp array and returns a logical matrix indicating snowcover
for the site (for all years with available data).

### swe\_snowcover.m

Takes SWE array and returns a logical matrix indicating snowcover for
the site (for all years with available data).

##### Testing

### testfiles.m

Tests all SNOTEL data files in a directory (hourly or daily) and
determines how many measurements are missing in each file. If too many
datapoints are missing, the file is listed in an "exclude" file that is
then read by other scripts.

` * **Input:** all SNOTEL .csv files in a directory`\
` * **Output:** Histograms of the data, and `*`excludefiles.txt`*` file`

### testsensors.m

Open all SNOTEL data files in a directory (hourly or daily), creates
plots of each sensor timeseries, and waits for user input. User input is
appended to a file (*excludesensors.txt*) that can be used by other
scripts to remove bad sensor data during data analysis.

` * **Input:** all SNOTEL .csv files in a directory`\
` * **Output:** Sensor timeseries plots, and an `*`excludesensors.txt`*` file`

### test\_loadsnotel.m(interval, siteID, varargin)

Loads a snotel site data in the same fashion as *loadsnotel.m*, but does
not remove any data. Also has some facilities to test missing columns
and introducing dummy data.

` * **Arguments**`\
`   * `*`interval`*` = 'hourly' or 'daily' string`\
`   * `*`siteID`*` = integer site number`\
`   * `*`varargin`*` = = cell array containing a test type ('delete' or 'dummyvalues') and a column number referring to the desired header/column number (1-20)`\
` * **Input:** Reads data files from `*`rawdata/allsensors_daily/`*`, or `*`rawdata/soilsensors_hourly`*`. No user input.`\
` * **Output:** A data matrix, no data removed.`

### plot\_snoteltests.m(interval, siteID)

Loads data for chosen site into two arrays, one with raw data (using
test\_loadsnotel.m) and one with bad data removed (using loaddata.m).
Then plots columns for these arrays with raw data in red and cleaned
data in black to show what was removed by loaddata.m.
