[_TOC_](levels = 3)

# Active research projects

Each research project has its own directory. Within these
project directories there are overview pages, methods pages (usually
site-specific methods), project logs, and results pages. Overview pages
describe the project objectives, hypotheses, and research approach, and
should link to all other pages in the project namespace.

## Hidden Canyon ecohydrology (hiddencanyon/hc_ecohydrology)

* [Overview](hiddencanyon/hc_overview.md)
* Experimental design: [Snowmelt manipulation](hiddencanyon/hc_snowmeltdesign.md), [Soil profiles](hiddencanyon/hc_soilprofiles.md)
* Methods: [Dust](westerndust.md), [Dust on snow](procedures/proc_dustonsnow.md), [Snowpack sublimation](procedures/proc_snowpacksublimation.md), [Xylem pressure](procedures/proc_xylempressure.md), [Below-snow soil resp](procedures/proc_belowsnow_soilresp.md), [Warm season resp](procedures/proc_manual_soilresp.md), [Litter bags](procedures/proc_litterbags.md)
* Measurement logs (preliminary results.md): [Snowmelt](hiddencanyon/hc_snowmeltlog_1.md), [Ecosystem water](hiddencanyon/hc_ecosystemwaterlog_1.md) (soil moisture and xylem water potential), [Soil respiration](hiddencanyon/hc_soilresplog_1.md), [Litter bags](hiddencanyon/hc_litterbaglog_1.md)
* [Hidden Canyon activity logs](hiddencanyon/hc_sitedescription.md), [data
analysis log](hiddencanyon/hc_analysislog_1.md)

## Western U.S. soil carbon cycling (west_carboncycle)

* [Overview](snotelC/snotelC_overview.md)
* Methods: [Protocol for SNOTEL visits](snotelC/snotelC_fieldprotocol.md), [Initial sample processing](snotelC/snotelC_sampleprocessing.md)
* Logs: [SNOTEL visits](snotelC/snotelC_log1.md), [Sample processing](snotelC/snotelC_sampleprocessinglog_1.md), [Data analysis](snotelC/snotelC_analysislog_1.md), [Sample processing tables](snotelC/snotelC_sampletables.md).

## Niwot girdling study (niwot_girdling/niwot_girdling)

* Methods: [Data QC](niwot_girdling/niwot_data_qc.md), [Soil analysis](niwot_girdling/niwot_soilanalysis.md), [Soil extract 13C procedure](procedures/proc_soilextract_13c.md)
* [Activity log](niwot_girdling/niwot_activitylog_1.md)

# Procedures

Protocols for making measurements in the field or the lab, processing
samples for analysis, or analyzing data. Intended as a general
reference, but site or experiment-specific info can be appended as
necessary.

## Laboratory protocols

* [Measuring exetainer gas samples](procedures/proc_exetainer_co2.md) for CO~2~ and C isotopes
* [Acid treatment of soils](procedures/proc_soilacidtreatment.md) to remove carbonates.
* [Soil sample prep for EA-IRMS analysis](procedures/proc_ea-irms_soilprep.md) at SIRFER.
* [Graphitization of soils](procedures/proc_14c_graphitization.md) for AMS ^14^C analysis
* [Preparing and taking data from tree cores](procedures/proc_treecores.md)
* [Snowpack dust loading](procedures/proc_snowpackdustloading.md)
* [δ13C analysis of soil extracts](procedures/proc_soilextract_13c.md)

## Field protocols

* [Manual soil respiration measurements](procedures/proc_manual_soilresp.md) (Hidden Canyon)
* [Below-snow respiration measurements](procedures/proc_belowsnow_soilresp.md)(Hidden Canyon)
* [procedures/litterbags](procedures/proc_litterbags.md)
* [Dust deposition on snowpacks](procedures/proc_dustonsnow.md) (Hidden Canyon)
* [procedures/measuringswe](procedures/proc_measuringswe.md)
* [procedures/xylempressure](procedures/proc_xylempressure.md)
* [procedures/snowpacksublimation](procedures/proc_snowpacksublimation.md)
* [Canopy photography](procedures/proc_canopyphotos.md)
* [Georeferencing with GPS](procedures/proc_gps.md)

## Data analysis and instrumentation programming

* [Data analysis programming](computing/comp_programming.md): General info for using Python/MATLAB/Octave/R for data analysis
* [Python tips](computing/comp_pythontips.md), [Numpy tips](computing/comp_numpytips.md), [Using IPython](computing/comp_ipython.md)
* [Matlab tips](computing/comp_matlabtips.md)
* [Shell scripts](computing/comp_shellscripts.md), [AWK](computing/comp_awk.md), [Vim](computing/comp_vimtips.md), and [assorted textfile tips](computing/comp_textfiles.md)
* [mercurial](computing/comp_mercurial.md), and [git](computing/comp_git.md): 2 version control systems.
* [Tips for analyzing sensor timeseries](computing/comp_sensordata_tips.md)
* [Workflow for data analysis](computing/comp_data_analysis_workflow.md)
* [Geospatial data analysis](computing/comp_geospatial.md)

## Research writing

* [Text file tips](computing/comp_textfiles.md)
* [Pandoc](computing/comp_pandoc.md) document converter and markup syntax.
* [LaTeX tips](computing/comp_latextips.md)

# Math

Pages covering statistical and mathematical concepts, or numerical
methods used in data analysis. Some of these pages are composed
primarily of links to further information on the subject.

* [Computation toolboxes](math/math_toolboxes.md) - tools for computing math and statistics.
* [Time series analysis](math/math_timeseries.md) - assorted methods for analyzing time series data to extract meaningful statistics.
* [ANOVA](math/math_anova.md) - analysis of variance for various experimental designs.
* [Reverse calibration equations](math/math_quadratic_eq_calib.md) - using the quadratic equation to back out sensor output from calibrated data (if calibration is known).
* [Principal components analysis](math/math_pca.md) and [Principal components regression](math/math_pcr)
* [Correlation](math/math_correlation.md)
* [Testing for normality](math/math_normalitytests.md)
* [Linear regression](math/math_linear_regression.md) - Bivariate (one independent variable) and multiple regression (>1 ind. variable).
* [ Multilevel/Mixed/Heirarchical statistical models](math/math_multilevel_models.md)
* [Integration](math/math_integration.md) - of functions, or sampled data such as a timeseries
* [Decay and turnover](math/math_decay_turnover.md) functions.

# Instruments

Contain documentation for operating, calibrating, and maintaining field
and lab instruments, sensors, etc. There are also notes on programs,
calibration constants, and conversion coefficients for instruments
currently in use.

* [Li-Cor Quantum sensor (LI-190.md)](instruments/inst_li-190.md)
* Notes, conventions, and code for [EDLOG programming](instruments/inst_edlog.md) (Campbell datalogger control)
* [Li-Cor 6400 portable soil respiration system](instruments/inst_li-6400.md) (in use at Hidden Canyon)
* [Campbell cr10 dataloggers](instruments/inst_cr10dataloggers.md) (several old ones in Red Butte Canyon)
* [Sentek EnviroSCAN soil moisture profiles](instruments/inst_sentek_enviroscan.md) (there are a couple at Hidden Canyon).
* [EA-IRMS protocol](instruments/inst_ea-irms_sirfer.md) at the SIRFER lab.

# Research Sites

Research sites (or networks) have their own namespace. Pages in a site
namespace should have descriptive information about the sites
themselves, research instrumentation, or researcher activities there.
For example: site maps, research plot layouts, technical info and
schematics for research installations (weather stations, etc.),
activity/maintenance logs, etc.

## Hidden Canyon

* [Site description](hiddencanyon/hc_sitedescription.md), [Tree location data](hiddencanyon/hc_trees.md)
* Instrumentation: [hc_communicationsystem](hiddencanyon/hc_communicationsystem.md), [hc_dataloggers](hiddencanyon/hc_dataloggers.md), [hc_mettowers](hiddencanyon/hc_mettowers.md), [hc_soilprofiles](hiddencanyon/hc_soilprofiles.md), [hc_georeferencing](hiddencanyon/hc_georeferencing.md)
* [2010 activity log](hiddencanyon/hc_2010_log.md), [2011 activity log](hiddencanyon/hc_2011_log.md), [2012 activity log](hiddencanyon/hc_2012_log.md), [data analysis log](hiddencanyon/hc_analysislog_1.md)

## Red Butte Canyon

* Above the University of Utah campus. There is a weather station network there.
* [RBC Weather Station info](redbutte/rb_weatherstations.md), [WS maintenance log](redbutte/rb_weather_log.md), [Using cr10 dataloggers](instruments/inst_cr10dataloggers.md)

## NRCS Snow Survey sites

* A network of mountain sites in the western U.S. where manual (snow courses) and automated (SNOTEL sites) measurements of snowpack (SWE) are taken for water supply forecasting. Manual measurements date back to the 1930's.
* [Official site](http://www.wcc.nrcs.usda.gov/)

## Niwot Ridge LTER

* A high elevation [LTER](http://www.lternet.edu/) and [Ameriflux](http://public.ornl.gov/ameriflux/) site in Colorado.
* Extensive research on tundra and forest ecology has been in progress here for a long time. The Bowling lab has instrumentation that measures biosphere-atmosphere interactions (CO~2~ mainly).

# Inactive research projects

These are either completed or on hold.

* [ Niwot Ridge label decomposition - overview](niwot_girdling/niwot_labeldecomp_overview.md) ON HOLD --- //[Greg Maurer](primaryproductivity@gmail.com) 2010/08/09 13:11//

## Ion deposition in snow (snowdep)

* Methods: [Snow sampling and cleanliness procedures](wasatchsnowdep/snowdep_sampling.md), [Processing snow samples for analysis](wasatchsnowdep/snowdep_labprocessing.md), [Mixing ion standards](wasatchsnowdep/snowdep_standards.md)
* [Data analysis log](wasatchsnowdep/snowdep_analysislog_1.md)
* [Activity log (not used)](wasatchsnowdep/snowdep_activitylog_1.md)

## Western U.S. soil climate analysis (west_stationdata)

* [Overview](soilclim/soilclim_overview.md)
* Methods: [Data collection and prep](soilclim/soilclim_data.md), [Data programming
documentation](soilclim/soilclim_programdocs.md), [Data QC (cleaning)](soilclim/soilclim_data_qc.md), [Statistical approach & methods](soilclim/soilclim_statistics.md)
* Logs: [Data analysis log](soilclim/soilclim_analysislog_1.md)
* [Publication outline](soilclim/soilclim_publicationoutline.md)
* Paper at [Water Resources Research](http://dx.doi.org/10.1002/2013WR014452)
