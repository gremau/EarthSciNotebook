# Active research projects

Each research project has its own directory. Within these
project directories there are overview pages, methods pages (usually
site-specific methods), project logs, and results pages. Overview pages
describe the project objectives, hypotheses, and research approach, and
should link to all other pages in the project namespace.

New Mexico Elevation Gradient flux processing
---------------------------------------------

* NMEG [[flux code|nmeg_fluxcode]]

Hidden Canyon ecohydrology (hc_ecohydrology)
---------------------------------------------

* [[Overview|hc_overview]]
* Experimental design: [[Snowmelt manipulation|hc_snowmeltdesign]], [[Soil profiles|hc_soilprofiles]]
* Methods: [[Dust|westerndust]], [[Dust on snow|procedures/proc_dustonsnow]], [[Snowpack sublimation|proc_snowpacksublimation]], [[Xylem pressure|proc_xylempressure]], [[Below-snow soil resp|proc_belowsnow_soilresp]], [[Warm season resp|proc_manual_soilresp]], [[Litter bags|proc_litterbags]]
* Measurement logs (preliminary results): [[Snowmelt|hc_snowmeltlog_1]], [[Ecosystem water|hc_ecosystemwaterlog_1]] (soil moisture and xylem water potential), [[Soil respiration:hc_soilresplog_1]], [[Litter bags|hc_litterbaglog_1]]
* [[Hidden Canyon activity logs|hc_sitedescription]], [[data
analysis log|hc_analysislog_1]]

Western U.S. soil carbon cycling (west_carboncycle)
----------------------------------------------------

* [[Overview|snotelC_overview]]
* Methods: [[Protocol for SNOTEL visits|snotelC_snotelfieldprotocol]], [[Initial sample processing|snotelC_snotelsampleprocessing]]
* Logs: [[SNOTEL visits|snotelC_snotellog_1]], [[Sample processing|snotelC_sampleprocessinglog_1]], [[Data analysis|snotelC_analysislog_1]], [[Sample processing tables|snotelC_sampletables]].

Niwot girdling study (niwot_girdling)
--------------------------------------

* Methods: [[Data QC|niwot_data_qc]], [[Soil analysis|niwot_soilanalysis]], [[Soil extract 13C procedure|proc_soilextract_13c]]
* [[Activity log|niwot_activitylog_1]]

# Procedures

Protocols for making measurements in the field or the lab, processing
samples for analysis, or analyzing data. Intended as a general
reference, but site or experiment-specific info can be appended as
necessary.

Laboratory protocols
--------------------

* [[Measuring exetainer gas samples|proc_exetainer_co2]] for CO~2~ and C isotopes
* [[Acid treatment of soils|proc_soilacidtreatment]] to remove carbonates.
* [[Soil sample prep for EA-IRMS analysis|proc_ea-irms_soilprep]] at SIRFER.
* [[Graphitization of soils|proc_14c_graphitization]] for AMS ^14^C analysis
* [[Preparing and taking data from tree cores|proc_treecores]]
* [[Snowpack dust loading|proc_snowpackdustloading]]
* [[δ13C analysis of soil extracts|proc_soilextract_13c]]

Field protocols
---------------

* [[Manual soil respiration measurements|proc_manual_soilresp]] (Hidden Canyon)
* [[Below-snow respiration measurements|proc_belowsnow_soilresp]](Hidden Canyon)
* [[procedures:litterbags|proc_litterbags]]
* [[Dust deposition on snowpacks|proc_dustonsnow]] (Hidden Canyon)
* [[procedures:measuringswe|proc_measuringswe]]
* [[procedures:xylempressure|proc_xylempressure]]
* [[procedures:snowpacksublimation|proc_snowpacksublimation]]
* [[Canopy photography|proc_canopyphotos]]
* [[Georeferencing with GPS|proc_gps]]

Data analysis and instrumentation programming
---------------------------------------------

* [[Data analysis programming|comp_programming]]: General info for using Python/MATLAB/Octave/R for data analysis
* [[Python tips|comp_pythontips]], [[Numpy tips|comp_numpytips]], [[Using IPython|comp_ipython]]
* [[Matlab tips|comp_matlabtips]]
* [[Shell scripts|comp_shellscripts]], [[AWK|comp_awk]], [[Vim|comp_vimtips]], and [[assorted textfile tips|comp_textfiles]]
* [[mercurial|comp_mercurial]], and [[git|comp_git]]: 2 version control systems.
* [[Tips for analyzing sensor timeseries|comp_sensordata_tips]]
* [[Workflow for data analysis|comp_data_analysis_workflow]]
* [[Geospatial data analysis|comp_geospatial]]

Research writing
----------------

* [[Text file tips|comp_textfiles]]
* [[Pandoc|comp_pandoc]] document converter and markup syntax.
* [[LaTeX tips|comp_latextips]]

# Math

Pages covering statistical and mathematical concepts, or numerical
methods used in data analysis. Some of these pages are composed
primarily of links to further information on the subject.

* [[Computation toolboxes|math_toolboxes]] - tools for computing math and statistics.
* [[Time series analysis|math_timeseries]] - assorted methods for analyzing time series data to extract meaningful statistics.
* [[ANOVA|math_anova]] - analysis of variance for various experimental designs.
* [[Reversing calibration equations|math_quadratic_eq_calib]] - using the quadratic equation to back out sensor output from calibrated data (if calibration is known).
* [[Principal components analysis|math_pca]] and [Principal components regression|math_pcr]]
* [[Correlation|math_correlation]]
* [[Testing for normality|math_normalitytests]]
* [[Linear regression|math_linear_regression]] - Bivariate (one independent variable) and multiple regression (>1 ind. variable).
* [[ Multilevel/Mixed/Heirarchical statistical models|math_multilevel_models]]
* [[Integration|math_integration]] - of functions, or sampled data such as a timeseries
* [[Decay and turnover|math_decay_turnover]] functions.

# Instruments

Contain documentation for operating, calibrating, and maintaining field
and lab instruments, sensors, etc. There are also notes on programs,
calibration constants, and conversion coefficients for instruments
currently in use.

* [[Li-Cor Quantum sensor (LI-190)|inst_li-190]]
* Notes, conventions, and code for [[EDLOG programming|inst_edlog]] (Campbell datalogger control)
* [[Li-Cor 6400 portable soil respiration system|inst_li-6400]] (in use at Hidden Canyon)
* [[Campbell cr10 dataloggers|inst_cr10dataloggers]] (several old ones in Red Butte Canyon)
* [[Sentek EnviroSCAN soil moisture profiles|inst_sentek_enviroscan]] (there are a couple at Hidden Canyon).
* [[EA-IRMS protocol|inst_ea-irms_sirfer]] at the SIRFER lab.

# Research Sites

Research sites (or networks) have their own namespace. Pages in a site
namespace should have descriptive information about the sites
themselves, research instrumentation, or researcher activities there.
For example: site maps, research plot layouts, technical info and
schematics for research installations (weather stations, etc.),
activity/maintenance logs, etc.

Hidden Canyon
-------------

* [[Site description|hc_sitedescription]], [[Tree location data|hc_trees]]
* Instrumentation: [hc_communicationsystem|hc_communicationsystem]], [[hc_dataloggers|hc_dataloggers]], [[hc_mettowers|hc_mettowers]], [[hc_soilprofiles|hc_soilprofiles]], [[hc_georeferencing|hc_georeferencing]]
* [[2010 activity log|hc_2010_log]], [[2011 activity log|hc_2011_log]], [[2012 activity log|hc_2012_log]], [[data analysis log|hc_analysislog_1]]

Red Butte Canyon
----------------

* Above the University of Utah campus. There is a weather station network there.
* [[RBC Weather Station info|rb_weatherstations]], [[WS maintenance log|rb_weather_log]], [[Using cr10 dataloggers|inst_cr10dataloggers]]

NRCS Snow Survey sites
----------------------

* A network of mountain sites in the western U.S. where manual (snow courses) and automated (SNOTEL sites) measurements of snowpack (SWE) are taken for water supply forecasting. Manual measurements date back to the 1930's.
* [[Official site|http://www.wcc.nrcs.usda.gov/]]

Niwot Ridge LTER
----------------

* A high elevation [LTER|http://www.lternet.edu/]] and [[Ameriflux|http://public.ornl.gov/ameriflux/) site in Colorado.
* Extensive research on tundra and forest ecology has been in progress here for a long time. The Bowling lab has instrumentation that measures biosphere-atmosphere interactions (CO~2~ mainly).

# Inactive research projects

These are either completed or on hold.

* [[ Niwot Ridge label decomposition - overview|niwot_labeldecomp_overview]] ON HOLD --- //[Greg Maurer|primaryproductivity@gmail.com]] 2010/08/09 13:11//

Ion deposition in snow (snowdep)
--------------------------------

* Methods: [Snow sampling and cleanliness procedures|snowdep_sampling]], [[Processing snow samples for analysis|snowdep_labprocessing]], [[Mixing ion standards|snowdep_standards]]
* [[Data analysis log|snowdep_analysislog_1]]
* [[Activity log (not used)|snowdep_activitylog_1]]

Western U.S. soil climate analysis (west_stationdata)
------------------------------------------------------

* [[Overview|soilclim_overview]]
* Methods: [[Data collection and prep|soilclim_data]], [[Data programming
documentation|soilclim_programdocs]], [[Data QC (cleaning)|soilclim_data_qc]], [[Statistical approach & methods|soilclim_statistics]]
* Logs: [[Data analysis log|soilclim_analysislog_1]]
* [[Publication outline|soilclim_publicationoutline]]
* Paper at [ Water Resources Research|http://dx.doi.org/10.1002/2013WR014452]]
