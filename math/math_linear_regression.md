# Linear Regression

Bivariate (simple) and multiple regression models.

In MATLAB, the backslash operator can be used, or functions such as
polyfit and regress. See
[here](http://chemwiki.ucdavis.edu/VV:_Mathematical_Concepts/Linear_Regression_in_Matlab)

## Bivariate regression (simple linear regression)

## Multiple regression

` * `[`This`
`paper`](http://journals.ametsoc.org/doi/abs/10.1175/2009JCLI2951.1)` has an interesting approach (and references) for using multiple regression in climate trend analysis.`

#### Collinearity

One of the worst pitfalls of multiple regression is in using the
technique for multivariate datasets in which some or all of the
independent variables are correlated. Collinearity is a VERY common
phenomenon in environmental data. In this case, regression coefficients
estimated in the model are generally not usable in describing the effect
of the independent variables, even though the model may fit the data
well. Interpretation of the model coefficients and hypothesis testing
becomes difficult or impossible in this situation. Some resources on
detecting and dealing with this situation:

` * **Detecting collinearity**
`   * Relationships between independent variables can be assessed with `[`correlation`
`tests`](correlation)` or simple linear regression.
` * **Dealing with collinearity**
`   * Remove predictor variables
`   * Use `[`principal`
`components`](pca)` as indpendent variables in the model (they are orthogonal).
`     * `[`Principal` `components`
`regression`](math:pcr)` can estimate coefficients for the original independent variables.
`   * Partial least squares regression
`   * Ridge regression.`

## Variations

` * **Time-series multiple regression** (see `[`this`
`page`](timeseries)`): Values of the dependent and/or independent variables at a previous timestep are incorporated into the model.`
