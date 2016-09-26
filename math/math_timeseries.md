# Time series analysis

Time series analysis is applied to data coming from a dynamical system,
ie, where a variable changes over time. The goal is to understand the
dynamical system (with a model) using the noisy data you have.

 **Resources **

<!-- -->

-   [Shumway and Stouffer's
    book](http://www.stat.pitt.edu/stoffer/tsa3/) on time
    series analysis.

## Moving window statistics

These are calculated by selecting a window size for the statistic, then
calculating the statistic for each point using that window. Three things
to remember when coding these:

* First, the calculated statistic will likely be out of phase with the original timeseries by half the moving window size. Therefore, the statistic should be calculated with an odd number of points, and can then be shifted back into phase with the original data. 
* Second, the calculated statistic will have a smaller window size at the edges of the timeseries, and is therefore less reliable in these areas. This may not be a significant problem if the dataset is large compared to the moving window.
* Third, missing data (NaN's) in a location will be propagated to the entire moving window. The simpler way to deal with this is to interpolate over the missing elements first. The other way is to exclude the missing elements, and thus use a variable number of points in calculating the statistic.`

### Mean

* Use `*`filter`*in MATLAB if there is no missing data.
* [moving_average](http://www.mathworks.com/matlabcentral/fileexchange/12276-movingaverage-v3-1-mar-2008)MATLAB`

### Median

* Use `*`medfilt1`*in MATLAB if there is not missing data.`

### Variance

### Standard Deviation

* A [MATLAB`
`implementation](http://www.mathworks.com/matlabcentral/fileexchange/9428-moving-window-standard-deviation)

## Filtering/smoothing

Links:
------

  * Hampel filter [implementation`in`
`Matlab](http://www.mathworks.com/matlabcentral/fileexchange/34795-outlier-detection-and-removal-hampel)(on Matlab Central).
  * [Robert`Pearson's`
`blog](http://exploringdatablog.blogspot.com/search/label/data%20cleaning)posts on data cleaning, particularly the Hampel filter.
  * Another [article`by`Ron`
`Pearson](http://www.edn.com/design/systems-design/4340430/Scrub-data-with-scale-invariant-nonlinear-digital-filters)on different non-linear filtering methods.`

## Mean of multiple timeseries (aggregate)

This is useful when similar timeseries need to be averaged, such as
one-year timeseries data for multiple sites, or generating an average
timeseries from multiple years.

* In MATLAB, `*`accumarray()*seems to work for this.
* In R, there are a few ways: `*`aggregate()*`, and maybe some functions in the `*`doBy`*package.`

## Autocorrelation

Is the value at some time (t) in the series statistically dependent on
the value at another time (s)? Put another way, is there a time lag
effect, or a memory effect, or does today depend on yesterday?

* the Autocorrelation function ('acf') can be applied in R.
* ARMA and ARIMA models are also useful.`

## Spectral analysis

## Decomposition

Method for deconstructing a time series into notional components:

* a Trend Component
* Seasonal components - reflect seasonality
* Cyclical components - repeated, but non-periodic fluctuations
* Irregular components - random or stochastic influences - often a residual of the timeseries.`

## Prediction and forecasting

## Multivariate models

*[TSA`package`for`
`R](http://cran.r-project.org/web/packages/TSA/)\
*A bunch of resources in [this](http://stackoverflow.com/questions/1714280/multivariate-time-series-modelling-in-r)and [this](http://stats.stackexchange.com/questions/18375/how-to-fit-an-arimax-model-with-r)SE question]]`

## Time series regression

This is a way of construction a multiple regression model in which
values of the dependent and/or independent variables at a previous
timestep become independent variables in the model.

* [http://www.sciencedirect.com/science/article/pii/S0038071712002970](http://www.sciencedirect.com/science/article/pii/S0038071712002970)

## R packages

* [forecast](http://cran.r-project.org/web/packages/forecast/index.html)\
* [TSA`
`package](http://cran.r-project.org/web/packages/TSA/)
