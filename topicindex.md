# Active research projects

Each research project has its own directory. Within these
project directories there are overview pages, methods pages (usually
site-specific methods), project logs, and results pages. Overview pages
describe the project objectives, hypotheses, and research approach, and
should link to all other pages in the project namespace.

New Mexico Elevation Gradient flux processing
---------------------------------------------

* NMEG [flux code](nmeg:fluxcode)

Hidden Canyon ecohydrology (hc_ecohydrology)
---------------------------------------------

* [Overview](/hc_ecohydrology/overview)
* Experimental design: [hiddencanyon/snowmeltdesign](hiddencanyon/snowmeltdesign), [/hiddencanyon/soilprofiles](/hiddencanyon/soilprofiles)
* Methods: [westerndust](westerndust), [procedures:dustonsnow](/procedures/dustonsnow), [/procedures/snowpacksublimation](/procedures/snowpacksublimation), [procedures:xylempressure](/procedures/xylempressure), [procedures:belowsnow_soilresp](/procedures/belowsnow_soilresp), [procedures:manual_soilresp](/procedures/manual_soilresp), [procedures:litterbags](/procedures/litterbags)
* Measurement logs (preliminary results): [Snowmelt](/hc_ecohydrology/snowmeltlog_1), [Ecosystem water](/hc_ecohydrology/ecosystemwaterlog_1) (soil moisture and xylem water potential), [Soil respiration](/hc_ecohydrology/soilresplog_1), [Litter bags](/hc_ecohydrology/litterbaglog_1)
* [Hidden Canyon activity logs](/hiddencanyon/sitedescription#Site_logs), [data
analysis log](/hiddencanyon/analysislog_1)

Western U.S. soil carbon cycling (west_carboncycle)
----------------------------------------------------

* [Overview](/west_carboncycle/overview)
* Methods: [Protocol for SNOTEL visits](/west_carboncycle/snotelfieldprotocol), [Initial sample processing](/west_carboncycle/snotelsampleprocessing)
* Logs: [SNOTEL visits](/west_carboncycle/snotellog_1), [Sample processing](/west_carboncycle/sampleprocessinglog_1), [Data analysis](/west_carboncycle/analysislog_1), [Sample processing tables](/west_carboncycle/sampletables).

Niwot girdling study (niwot_girdling)
--------------------------------------

* Methods: [Data QC](/niwot_girdling/data_qc), [Soil analysis](/niwot_girdling/soilanalysis), [Soil extract 13C procedure](/procedures/soilextract_13c)
* [Activity log](/niwot_girdling/activitylog_1)

# Procedures

Protocols for making measurements in the field or the lab, processing
samples for analysis, or analyzing data. Intended as a general
reference, but site or experiment-specific info can be appended as
necessary.

Laboratory protocols
--------------------

* [Measuring exetainer gas samples](/procedures/exetainer_co2) for CO~2~ and C isotopes
* [Acid treatment of soils](/procedures/soilacidtreatment) to remove carbonates.
* [Soil sample prep for EA-IRMS analysis](/procedures/ea-irms_soilprep) at SIRFER.
* [Graphitization of soils](/procedures/14c_graphitization) for AMS ^14^C analysis
* [Preparing and taking data from tree cores](/procedures/treecores)
* [Snowpack dust loading](/procedures/snowpackdustloading)
* [δ13C analysis of soil extracts](/procedures/soilextract_13c)

Field protocols
---------------

* [Manual soil respiration measurements](/procedures/manual_soilresp) (Hidden Canyon)
* [Below-snow respiration measurements](/procedures/belowsnow_soilresp)(Hidden Canyon)
* [procedures:litterbags](/procedures/litterbags)
* [Dust deposition on snowpacks](/procedures/dustonsnow) (Hidden Canyon)
* [procedures:measuringswe](/procedures/measuringswe)
* [procedures:xylempressure](/procedures/xylempressure)
* [procedures:snowpacksublimation](/procedures/snowpacksublimation)
* [Canopy photography](/procedures/canopyphotos)
* [Georeferencing with GPS](/procedures/gps)

Data analysis and instrumentation programming
---------------------------------------------

* [Data analysis programming](/procedures/programming): General info for using Python/MATLAB/Octave/R for data analysis
* [Python tips](/procedures/pythontips), [Numpy tips](/procedures/numpytips), [Using IPython](/procedures/ipython)
* [Matlab tips](/procedures/matlabtips)
* [Shell scripts](/procedures/shellscripts), [AWK](/procedures/awk), [Vim](/procedures/vimtips), and [assorted textfile tips](/procedures/textfiles)
* [mercurial](/procedures/mercurial), and [git](/procedures/git): 2 version control systems.
* [Tips for analyzing sensor timeseries](/procedures/sensordata_tips)
* [Workflow for data analysis](/procedures/data_analysis_workflow)
* [Geospatial data analysis](/procedures/geospatial)

Research writing
----------------

* [Text file tips](/procedures/textfiles)
* [Pandoc](/procedures/pandoc) document converter and markup syntax.
* [LaTeX tips](/procedures/latextips)

# Math

Pages covering statistical and mathematical concepts, or numerical
methods used in data analysis. Some of these pages are composed
primarily of links to further information on the subject.

* [Computation toolboxes](/math/toolboxes) - tools for computing math and statistics.
* [Time series analysis](/math/timeseries) - assorted methods for analyzing time series data to extract meaningful statistics.
* [ANOVA](/math/anova) - analysis of variance for various experimental designs.
* [Reversing calibration equations](/math/quadratic_eq_calib) - using the quadratic equation to back out sensor output from calibrated data (if calibration is known).
* [Principal components analysis](/math/pca) and [Principal components regression](/math/pcr)
* [Correlation](/math/correlation)
* [Testing for normality](/math/normalitytests)
* [Linear regression](/math/linear_regression) - Bivariate (one independent variable) and multiple regression (>1 ind. variable).
* [ Multilevel/Mixed/Heirarchical statistical models](/math/multilevel_models)
* [Integration](/math/integration) - of functions, or sampled data such as a timeseries
* [Decay and turnover](/math/decay_turnover) functions.

# Instruments

Contain documentation for operating, calibrating, and maintaining field
and lab instruments, sensors, etc. There are also notes on programs,
calibration constants, and conversion coefficients for instruments
currently in use.

* [Li-Cor Quantum sensor (LI-190)](/instruments/li-190)
* Notes, conventions, and code for [EDLOG programming](/instruments/edlog) (Campbell datalogger control)
* [Li-Cor 6400 portable soil respiration system](/instruments/li-6400) (in use at Hidden Canyon)
* [Campbell cr10 dataloggers](/instruments/cr10dataloggers) (several old ones in Red Butte Canyon)
* [Sentek EnviroSCAN soil moisture profiles](/instruments/sentek_enviroscan) (there are a couple at Hidden Canyon).
* [EA-IRMS protocol](/instruments/ea-irms_sirfer) at the SIRFER lab.

# Research Sites

Research sites (or networks) have their own namespace. Pages in a site
namespace should have descriptive information about the sites
themselves, research instrumentation, or researcher activities there.
For example: site maps, research plot layouts, technical info and
schematics for research installations (weather stations, etc.),
activity/maintenance logs, etc.

Hidden Canyon
-------------

* [Site description](/hiddencanyon/sitedescription), [Tree location data](/hiddencanyon/trees)
* Instrumentation: [/hiddencanyon/communicationsystem](/hiddencanyon/communicationsystem), [/hiddencanyon/dataloggers](/hiddencanyon/dataloggers), [/hiddencanyon/mettowers](/hiddencanyon/mettowers), [/hiddencanyon/soilprofiles](/hiddencanyon/soilprofiles), [/hiddencanyon/georeferencing](/hiddencanyon/georeferencing)
* [2010 activity log](/hiddencanyon/hc2010_log), [2011 activity log](/hiddencanyon/hc2011_log), [2012 activity log](/hiddencanyon/hc2012_log), [data analysis log](/hiddencanyon/analysislog_1)

Red Butte Canyon
----------------

* Above the University of Utah campus. There is a weather station network there.
* [RBC Weather Station info](/redbutte/weatherstations), [WS maintenance log](/redbutte/rbweather_log), [Using cr10 dataloggers](/instruments/cr10dataloggers)

NRCS Snow Survey sites
----------------------

* A network of mountain sites in the western U.S. where manual (snow courses) and automated (SNOTEL sites) measurements of snowpack (SWE) are taken for water supply forecasting. Manual measurements date back to the 1930's.
* [Official site](http://www.wcc.nrcs.usda.gov/)

Niwot Ridge LTER
----------------

* A high elevation [LTER](http://www.lternet.edu/) and [Ameriflux](http://public.ornl.gov/ameriflux/) site in Colorado.
* Extensive research on tundra and forest ecology has been in progress here for a long time. The Bowling lab has instrumentation that measures biosphere-atmosphere interactions (CO~2~ mainly).

# Inactive research projects

These are either completed or on hold.

* [ Niwot Ridge label decomposition - overview](niwot_labeldecomp_overview) ON HOLD --- //[Greg Maurer](primaryproductivity@gmail.com) 2010/08/09 13:11//

Ion deposition in snow (snowdep)
--------------------------------

* Methods: [Snow sampling and cleanliness procedures](wasatchsnowdep:sampling), [Processing snow samples for analysis](wasatchsnowdep:labprocessing), [Mixing ion standards](wasatchsnowdep:standards)
* [Data analysis log](wasatchsnowdep:analysislog_1)
* [Activity log (not used)](wasatchsnowdep:activitylog_1)

Western U.S. soil climate analysis (west_stationdata)
------------------------------------------------------

* [Overview](west_stationdata:overview)
* Methods: [Data collection and prep](west_stationdata:data), [Data programming
documentation](west_stationdata:programdocs), [Data QC (cleaning)](west_stationdata:data_qc), [Statistical approach & methods](west_stationdata:statistics)
* Logs: [Data analysis log](west_stationdata:analysislog_1)
* [Publication outline](west_stationdata:publicationoutline)
* Paper at [ Water Resources Research](http://dx.doi.org/10.1002/2013WR014452)
