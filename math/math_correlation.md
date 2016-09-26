# Correlation

Data analysis often calls for testing whether two or more sets of
numbers are related in some way (see
[wp>Correlation_and_dependence](wp>Correlation_and_dependence)).
Here are some methods to test for or describe a relationship (usually a
linear one) between random variables, or two sets of data.

 **Resources**

* [John`Cook's`
`take](http://www.johndcook.com/blog/2008/11/05/how-to-calculate-pearson-correlation-accurately/)

## Parametric

#### Pearson's product-moment correlation test

This is a common test for a linear relationship between two variables
which yields a correlation coefficient between 1 and -1. This test
should give the same significance (p-value) as a simple linear
regression on the same data.

* Use `cor.test` in R.
* Use `scipy.stats.pearsonr` or `pandas.DataFrame.corr(method='pearson')*in python`

#### Simple linear regression

Linear regression is related to correlation and a sample correlation can
be calculated as the square root of the R^2^
([wp>Coefficient_of_determination](wp>Coefficient_of_determination)),
with the sign of the slope of the regression line (the coefficient of
x).

* Use `lm` in R
* Use `regress` in MATLAB.
* Numpy has `polyfit` and Scipy has `linregress` \
* See other notes [here](linear_regression).`

## Non-parametric

If the relationship is non-linear or variance is not normally
distributed, these may be useful. Both of the tests below can be used
with *cor.test* in R. Python pandas also has these tests in
*pandas.DataFrame.corr(method='spearman OR kendall')* in python

#### Spearman's rank test

Ranks x and y datapoints and then does a correlation test between the
ranked data. May demonstrate a correlation when a Pearson or linear
model test do not.

#### Kendall's Tau

Looks at pairs of data points and tests how frequently the relationship
between the pair goes in one direction or the other.

[This
paper](http://journals.ametsoc.org/doi/abs/10.1175/2009JCLI2951.1)
uses Kendall's Tau for analyzing climate trends.

## Corrections for significance

It can be hard to get a good significance value if you are doing
multiple comparisons. Lots of people recommend against this, but the
**Bonferroni** correction can be applied. Also, it may be useful to
construct 95% confidence intervals around a correlation, and use that
instead (does it include 0?).

 **Further reading on this**

* Gotelli and Ellison, Chapter 10
* [SE`
`question](http://stats.stackexchange.com/questions/5750/look-and-you-shall-find-a-correlation)
