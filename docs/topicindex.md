# Active research projects

Each research project has its own directory. Within these
project directories there are overview pages, methods pages (usually
site-specific methods), project logs, and results pages. Overview pages
describe the project objectives, hypotheses, and research approach, and
should link to all other pages in the project namespace.

## Hidden Canyon ecohydrology

* [Overview](hiddencanyon/overview.md)
* Experimental design: [Snowmelt manipulation](hiddencanyon/snowmeltdesign.md), [Soil profiles](hiddencanyon/soilprofiles.md)
* Methods: [Dust](westerndust.md), [Dust on snow](procedures/dustonsnow.md), [Snowpack sublimation](procedures/snowpacksublimation.md), [Xylem pressure](procedures/xylempressure.md), [Below-snow soil resp](procedures/belowsnow_soilresp.md), [Warm season resp](procedures/manual_soilresp.md), [Litter bags](procedures/litterbags.md)
* Measurement logs: [Snowmelt](hiddencanyon/snowmeltlog_1.md), [Soil respiration](hiddencanyon/soilresplog_1.md), [Litter bags](hiddencanyon/litterbaglog_1.md)
* [Hidden Canyon activity logs](hiddencanyon/sitedescription.md), [data
analysis log](hiddencanyon/analysislog_1.md)

## Western U.S. soil carbon cycling

* [Overview](snotelC/overview.md)
* Methods: [Protocol for SNOTEL visits](snotelC/fieldprotocol.md), [Initial sample processing](snotelC/sampleprocessing.md)
* Logs: [SNOTEL visits](snotelC/log1.md), [Sample processing](snotelC/sampleprocessinglog_1.md), [Data analysis](snotelC/analysislog_1.md), [Sample processing tables](snotelC/sampletables.md).

## Niwot girdling study (niwot_girdling/girdling)

* Methods: [Data QC](niwot_girdling/data_qc.md), [Soil analysis](niwot_girdling/soilanalysis.md), [Soil extract 13C procedure](procedures/soilextract_13c.md)
* [Activity log](niwot_girdling/activitylog_1.md)

# Procedures

Protocols for making measurements in the field or the lab, processing
samples for analysis, or analyzing data. Intended as a general
reference, but site or experiment-specific info can be appended as
necessary.

## Laboratory protocols

* [Measuring exetainer gas samples](procedures/exetainer_co2.md) for CO~2~ and C isotopes
* [Acid treatment of soils](procedures/soilacidtreatment.md) to remove carbonates.
* [Soil sample prep for EA-IRMS analysis](procedures/ea-irms_soilprep.md) at SIRFER.
* [Graphitization of soils](procedures/14c_graphitization.md) for AMS ^14^C analysis
* [Preparing and taking data from tree cores](procedures/treecores.md)
* [Snowpack dust loading](procedures/snowpackdustloading.md)
* [δ13C analysis of soil extracts](procedures/soilextract_13c.md)

## Field protocols

* [Manual soil respiration measurements](procedures/manual_soilresp.md) (Hidden Canyon)
* [Below-snow respiration measurements](procedures/belowsnow_soilresp.md)(Hidden Canyon)
* [procedures/litterbags](procedures/litterbags.md)
* [Dust deposition on snowpacks](procedures/dustonsnow.md) (Hidden Canyon)
* [procedures/measuringswe](procedures/measuringswe.md)
* [procedures/xylempressure](procedures/xylempressure.md)
* [procedures/snowpacksublimation](procedures/snowpacksublimation.md)
* [Canopy photography](procedures/canopyphotos.md)
* [Georeferencing with GPS](procedures/gps.md)

## Data analysis and instrumentation programming

* [Data analysis programming](computing/programming.md): General info for using Python/MATLAB/Octave/R for data analysis
* [Python tips](computing/pythontips.md), [Numpy tips](computing/numpytips.md), [Using IPython](computing/ipython.md)
* [Matlab tips](computing/matlabtips.md)
* [Shell scripts](computing/shellscripts.md), [AWK](computing/awk.md), [Vim](computing/vimtips.md), and [assorted textfile tips](computing/textfiles.md)
* [mercurial](computing/mercurial.md), and [git](computing/git.md): 2 version control systems.
* [Tips for analyzing sensor timeseries](computing/sensordata_tips.md)
* [Workflow for data analysis](computing/data_analysis_workflow.md)
* [Geospatial data analysis](computing/geospatial.md)

## Research writing

* [Text file tips](computing/textfiles.md)
* [Pandoc](computing/pandoc.md) document converter and markup syntax.
* [LaTeX tips](computing/latextips.md)

# Math

Pages covering statistical and mathematical concepts, or numerical
methods used in data analysis. Some of these pages are composed
primarily of links to further information on the subject.

* [Computation toolboxes](math/toolboxes.md) - tools for computing math and statistics.
* [Time series analysis](math/timeseries.md) - assorted methods for analyzing time series data to extract meaningful statistics.
* [ANOVA](math/anova.md) - analysis of variance for various experimental designs.
* [Reverse calibration equations](math/quadratic_eq_calib.md) - using the quadratic equation to back out sensor output from calibrated data (if calibration is known).
* [Principal components analysis](math/pca.md) and [Principal components regression](math/pcr)
* [Correlation](math/correlation.md)
* [Testing for normality](math/normalitytests.md)
* [Linear regression](math/linear_regression.md) - Bivariate (one independent variable) and multiple regression (>1 ind. variable).
* [ Multilevel/Mixed/Heirarchical statistical models](math/multilevel_models.md)
* [Integration](math/integration.md) - of functions, or sampled data such as a timeseries
* [Decay and turnover](math/decay_turnover.md) functions.

# Instruments

Contain documentation for operating, calibrating, and maintaining field
and lab instruments, sensors, etc. There are also notes on programs,
calibration constants, and conversion coefficients for instruments
currently in use.

* [Li-Cor Quantum sensor (LI-190.md)](instruments/li-190.md)
* Notes, conventions, and code for [EDLOG programming](instruments/edlog.md) (Campbell datalogger control)
* [Li-Cor 6400 portable soil respiration system](instruments/li-6400.md) (in use at Hidden Canyon)
* [Campbell cr10 dataloggers](instruments/cr10dataloggers.md) (several old ones in Red Butte Canyon)
* [Sentek EnviroSCAN soil moisture profiles](instruments/sentek_enviroscan.md) (there are a couple at Hidden Canyon).
* [EA-IRMS protocol](instruments/ea-irms_sirfer.md) at the SIRFER lab.

# Research Sites

Research sites (or networks) have their own namespace. Pages in a site
namespace should have descriptive information about the sites
themselves, research instrumentation, or researcher activities there.
For example: site maps, research plot layouts, technical info and
schematics for research installations (weather stations, etc.),
activity/maintenance logs, etc.

## Hidden Canyon

* [Site description](hiddencanyon/sitedescription.md), [Tree location data](hiddencanyon/trees.md)
* Instrumentation: [communicationsystem](hiddencanyon/communicationsystem.md), [dataloggers](hiddencanyon/dataloggers.md), [mettowers](hiddencanyon/mettowers.md), [soilprofiles](hiddencanyon/soilprofiles.md) 
* [2010 activity log](hiddencanyon/2010_log.md), [2011 activity log](hiddencanyon/2011_log.md), [2012 activity log](hiddencanyon/2012_log.md), [data analysis log](hiddencanyon/analysislog_1.md)

## Red Butte Canyon

* Above the University of Utah campus. There is a weather station network there.
* [RBC Weather Station info](redbutte/weatherstations.md), [WS maintenance log](redbutte/weather_log.md), [Using cr10 dataloggers](instruments/cr10dataloggers.md)

## NRCS Snow Survey sites

* A network of mountain sites in the western U.S. where manual (snow courses) and automated (SNOTEL sites) measurements of snowpack (SWE) are taken for water supply forecasting. Manual measurements date back to the 1930's.
* [Official site](http://www.wcc.nrcs.usda.gov/)

## Niwot Ridge LTER

* A high elevation [LTER](http://www.lternet.edu/) and [Ameriflux](http://public.ornl.gov/ameriflux/) site in Colorado.
* Extensive research on tundra and forest ecology has been in progress here for a long time. The Bowling lab has instrumentation that measures biosphere-atmosphere interactions (CO~2~ mainly).

# Inactive research projects

These are either completed or on hold.

* [ Niwot Ridge label decomposition - overview](niwot_girdling/labeldecomp_overview.md) ON HOLD --- //[Greg Maurer](primaryproductivity@gmail.com) 2010/08/09 13:11//

## Ion deposition in snow (snowdep)

* Methods: [Snow sampling and cleanliness procedures](wasatchsnowdep/sampling.md), [Processing snow samples for analysis](wasatchsnowdep/labprocessing.md), [Mixing ion standards](wasatchsnowdep/standards.md)
* [Data analysis log](wasatchsnowdep/analysislog_1.md)
* [Activity log (not used)](wasatchsnowdep/activitylog_1.md)

## Western U.S. soil climate analysis (west_stationdata)

* [Overview](soilclim/overview.md)
* Methods: [Data collection and prep](soilclim/data.md), [Data programming
documentation](soilclim/programdocs.md), [Data QC (cleaning)](soilclim/data_qc.md), [Statistical approach & methods](soilclim/statistics.md)
* Logs: [Data analysis log](soilclim/analysislog_1.md)
* [Publication outline](soilclim/publicationoutline.md)
* Paper at [Water Resources Research](http://dx.doi.org/10.1002/2013WR014452)
