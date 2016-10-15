# SNOTEL soil climate statistics

This is a place to collect the statistical approach, as well as specific statistical methods, for analysis of data from the SNOTEL soil climate project.

**See also:** [Project overview](soilclim_overview.md), [Data analysis log](soilclim_analysislog_1.md)

## Hypotheses

The (working) hypotheses are something like this (see the [publication
outline](soilclim_publicationoutline.md) for more):

- Seasonal snowpacks dampen elevational gradients in Tsoil.
- Snowpack variability leads to biologically important variability in Tsoil .
- Winter VWC is dependent on antecedent fall conditions and exhibits temporal stability until the beginning of snowmelt. 
- Inter-annual variability in growing season soil moisture is correlated with snowpack size and snowmelt timing.

## Multiple regression

The original approach was to take the desired dependent variables and
fit them to a multiple regression model of several environmental
variables as predictors using forward model selection. There were three
dependent variables: mean below-snow temperature, winter (jan, feb, mar)
soil moisture, and growing season (Jul, Aug, Sep) soil moisture. There
were any number of candidate independent variables that could be used as
predictors in the models for the three dependent variables. It was
difficult to know which predictors to add during the forward selection
process, and unfortunately, many, if not most, of the independent
variables are collinear. So, in short, though some useful information
was gleaned from this, it is not a great statistical approach to testing
our hypotheses.

For more on this see:

* The four R scripts, two for vwc (`_simplelm.r` and `_multiplelm.r`) and two for mast_ (`_simplelm.r`and `_multiplelm.r`).
* A summary of these results in table form - `regstats.gnumeric`.

## PCA

The current approach uses [principal components analysis](/math/math_pca.md). Briefly:

- Create matrices of environmental variables that may predict each the three dependent variables of interest (mean below-snow temperature, mean Jan+Feb+March soil moisture, and mean Jul+Aug+Sep soil moisture). These can be fairly large and include monthly means of the variables of interest (Tair, Precip, SWE, etc) as well as longer means (multiple months).
- Run a PCA analyses on these matrices and select the first few principal components based on variance explained.
- Try to summarize the variable loadings on these axes in a coherent way, if possible.
- Assemble a multiple regression model that uses the scores from these principal components as the independent variables.

### Below-snow PCA results

Have run this for all years and for 2007, 2009 and 2011 individually. In
general, the first 3 principal components are the most informative. The
loadings and interpretations are something like:

* PC1
  * Total snow-covered days, snow-free date load the highest.
  * Apr and May SWE is important for all sites.
  * In some years, individual months of SWE or Tair load high.
  * Interpretation: **Spring snowmelt axis**. Warm temps (positive values) mean less snow, earlier melt, shorter snow duration.

* PC2
  * Snow-covered Tair loads consistently high.
  * Other winter SWE and Tair variables load high in some years.
  * Peak SWE also loads pretty high
  * Interpretation: **Winter temperature axis**, with some interaction with winter SWE.

* PC3
  * Onset day loads positive
  * Pre-onset Tair and Tsoil load negative.
  * Interpretation: **Pre-snowpack axis**. Pre-onset temperatures and snowpack onset timing are closely related.

* PC4
  * This doesn't account for much variance, but its StdDev is over 1 in 2 of the 4 PCAs (all and 2007)
  * For all years PCA, Oct and Nov SWE load highest.
  * For 2007-11 pre-onset Tair, Tsoil, and VWC load highest, but in different combinations in different years.
  * Not sure whether to include this in regression analysis.

### Growing Season PCA results

Have run this for all years and for 2007, 2009 and 2011 individually.
The loadings and interpretations are something like:

* PC1
  * April through September Tair load with high positive values (in all years)
  * Elevation is negative
  * Melt day and total snowcovered days load negative, but are minor
  * Interpretation: **Growing season Tair axis**
* PC2
  * Growing season precip loads positive or negative depending on year.
  * Melt day and peak SWE load either positive or negative depending on year.
  * Interpretation: **Growing season precip and SWE/snowmelt timing axis**
* PC3
  * Winter soil temperature, soil moisture, and summer precip load positive or negative depending on year.
  * Interpretation: **Winter Tsoil and VWC, and growing season precip**

### Hypothesis tests with PC axes

I used the principal components axes described above as independent
variables for multiple regression predicting below-snow Tsoil and VWC,
and growing season VWC. All 3 axes are significant when predicting all
years of data. For individual years (2007. 2009, 0r 2011), their value
varies.

## Landscape patterns in Tsoil and VWC variability

Also am trying to make sense of patterns of variability across the
landscape. For example:

* StdDev and CV of mean JFM soil VWC with elevation
* StdDev and CV of mean snow-covered Tsoil with elevation

~~~{.r}
cv <- soilTData$snowcovTs20sd/soilTData$snowcovTs20mean
plot(cv ~ climData.sub$elev)
~~~
