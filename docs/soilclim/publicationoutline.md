## SNOTEL network soil temperature and moisture

[Project overview](overview.md)

## Introduction

* Overview of SNOTEL network and its suitability for understanding ST and SM across the landscape.
* Papers - Goodrich, Bartlett papers.

## Methods

We examined data from soil sensor profiles at 252 SNOTEL sites in
Arizona, Colorado, Idaho, Montana, Nevada, New Mexico, Utah, and
Wyoming. Measurements of snow water equivalent (SWE), precipitation, and
air temperature were also used in this analysis. Data were downloaded
directly from the NRCS Snow Survey/SNOTEL website
(http://http://www.wcc.nrcs.usda.gov/snow/)in delimited text format.

## Figures

### Figure A

![media/west_stationdata:figa.png?200|] Data distributions for selected
variables discussed in this paper. They are plotted for the entire
SNOTEL network of the interior western U.S. (Black bars - 551 sites in
AZ, CO, ID, MT, NM, NV, UT, WY) and the subset of those sites that have
soil sensor profiles installed (Gray bars - 252 sites). Data for all
available wateryears from 2001 to 2011 are included here, except where
soil sensor installation occurred earlier, in which case a longer record
is present. Mean of each distribution is plotted with a dashed vertical
line in the same color.

### Figure B - Seasonal soil temperature and vwc patterns

![media/west_stationdata:figb.png?200|] Time series of SWE, T~soil~, and
soil VWC from multiple years at the Currant Creek SNOTEL site (UT). All
available wateryears for each variable are plotted in light gray, and a
mean of all water years is plotted in black. Mean air temperature over
the same time period is also plotted in the middle panel (dashed black
line) to illustrate that T~soil~ is decoupled from T~air~ and remains
near zero C when a snowpack is present.

* Include a low elevation/low snowpack site in this (2 site comparison)?

### Figure C - Elevational soil temperature gradients

![media/west_stationdata:figc.png?200|] Mean January and July T~soil~
(20cm depth) plotted against site elevation at all Utah SNOTEL sites.
Each point is a multi-year mean of the site's January or July
temperature measurements from all available wateryears. T~soil~ remains
near zero at all SNOTEL sites along an elevation transect during winter
months. This is in contrast to the same transect of sites in July, where
T~soil~ roughly follows the atmospheric temperature lapse rate.

* Combine with Fig D in 2 panel?
* These are actually a mean of all the wateryear means - might check the quality of this.

### Figure D - Air-soil temperature offsets across the landscape

![media/west_stationdata:figd.png?200|] Mean January T~soil~ (20cm depth)
and T~air~ plotted against site elevation at all Utah SNOTEL sites. Each
point is a multi-year mean of the site's January temperature
measurements from all available wateryears. T~soil~ is plotted with bars
showing 1 StdDev. An example point showing the mean StdDev of T~air~ is
also plotted (inset). Wintertime offsets between air and soil
temperature increase with elevation.

* FIXME - maybe the offset/elevation plot should be calculated for all 12 months
* These are actually a mean of all the wateryear means - might check the quality of this.

### Figure E - Snowpack effect on mean annual soil temperature

![media/west_stationdata:mast_mat_gradients.png?200|]
![media/west_stationdata:mast_diff_snowpackreg.png?200|]
Comparison of mean
annual T~soil~ (MAST) and mean annual T~air~ (MAT) across all SNOTEL
sites (with soil sensor profiles. Each point is MAST (grey) or MAT
(blue) for one site during one wateryear. MAST is higher than MAT, and
this difference is related to snowpack duration. Lines are linear
regression.

* FIXME - probably only need the duration plot, and may be more clear with boxplots or regressions lines.
* Needs error bars

### Figure F - Inter-annual variability in snowpack/soil temp

![media/west_stationdata:figf.png?200|] T~soil~, T~air~, and SWE at Mosby
Mountain SNOTEL site (UT) during two contrasting water years. In water
year 2005, a large snowpack (SWE) accumulated early, leading to stable,
near-zero T~soil~ during the remainder of the snowcovered period. In
water year 2010, a small early-season snowpack led to colder T~soil~ for
much of the snowcovered period.

* Should there be a similar figure with spring snowmelt/soil temps?

### Figure G - Early season snowpack and soil temperature

![media/west_stationdata:figg.png?200|] Mean monthly T~soil~ plotted
against SWE. Each point is the mean T~soil~ for one month at an
individual SNOTEL site. Two sensor depths are plotted for each site in
December and January of all available water years. The solid lines are
the least-squares fit to a bounded exponential function. Low early
season T~soil~ occurs more frequently at sites or during water years
that have a small snowpack. A dotted line at zero degrees C is plotted
for reference.

### Figure H - Effect of snowpack variability on growing season soil moisture

![media/west_stationdata:gsvwc_snowpack.png?100|]{{
:west_stationdata:gsvwc_snowrain.png?200|] Melt timing has a greater
effect on growing season soil moisture than snowpack size.

* Panel A: Mean July, August, September soil moisture plotted versus the peak SWE of the prior spring snowpack.
* Panel B: Mean July, August, September soil moisture plotted versus the wateryear melt day of the prior spring snowpack.

* FIXME - still some fixing to do - perhaps all 3 depths can go on one plot, and then have SWE and meltday side by side.

### Figure I - Stability of winter soil moisture

![media/west_stationdata:figi.png?120|] Winter month soil VWC plotted
against mean VWC of the 2 weeks period prior to snowpack onset. Soil VWC
data is normalized to a value between 0 and 1. A one month datapoint for
all sites and wateryears has been averaged into VWC units of 0.1 and
plotted with the StdDev of this average. A 1:1 line (dotted) is also
shown for reference. Soil VWC below a snowpack is closely related to
soil VWC immediately prior to the onset of snowcover, and it remains
stable until the beginning of the snowmelt cycle.

### Figure J - Soil moisture histograms at 4 contrasting sites

![media/west_stationdata:figj.png?200|] Histograms of soil water content
(normalized to between 0 and 1) for four SNOTEL sites with contrasting
profiles of elevation and mean snowpack size. Mean snowpack size is
determined from NRCS 30-year mean datasets for the site. The same six
years of data, 2006-2011, are shown for all sites. There are 4
histograms per site, representing the 4 quarters of the wateryear. Mean
T~soil~ is for each quarter is plotted with a dashed vertical
line.

## Optional/Redundant figures

### Figure

![media/west_stationdata:monthlysoiltempgradient2.png?150|] Monthly avg
soil-air T offset by elevation

* FIXME - this figure might be redundant, could be combined with air-soil T offsets (for 12 months)?
