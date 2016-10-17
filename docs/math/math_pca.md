# Principal components analysis

* Excellent for high-dimensional (multivariate) datasets that exhibit some collinearity. 
* Most useful for hypothesis generation, not hypothesis testing.
* No division of dataset into dependent and independent variables.
* Reduces the dimensionality of complex data.
* There is no significance value or test of a null hypotheses given by the technique.
* Not necessarily an end in itself, but best followed with further inferential tests, such as ANOVA or regression on the first and second principal components.

## Procedure

### 1. Choose variables to include

  * In descriptive studies it is often best to include all numerical variables measured.
  * Probably best to leave out the dependent variables you are interested in.
  * Check each variable for normality ([see here](http://www.r-bloggers.com/normality-tests-don%E2%80%99t-do-what-you-think-they-do/))?
  * Log transform each variable?
  * Sometimes rare observations can be excluded.

### 2. PCA calculations

The basic steps in this process are:

- Center and scale all variables (Often the PCA software will do this automatically).
- Calculate a correlation matrix for the chosen variables.
- Calculate the eigenvalues (% variance explained) and eigenvectors (loadings) of the correlation matrix.
- Calculate singular values from the square root of the eigenvalues (StdDev).
- Calculate axis scores for each observation on each axis.

### 3. Examine variance explained by the principal components

A set of principal components, as many as there are explanatory
variables, are then produced. The first two or three principal
components explain most of the variance in the data, and are therefore
the most informative. There are a few common tests of which components
to retain. The first is to reject any whose percent variance explained
is less than $100/N$, where $N$ is the number of variables. Another
method, called the broken stick model, calculates expected values for
percentage variance given the number of variables. Axes with less
variance than expected are excluded. Another, more simplistic method is
subjective visual selection of components using a scree plot:

Sometimes, a threshold at which percent variance explained drops is
visible on the screeplot as an elbow among the bars. Axes below the
elbow are rejected.

### 4. Examine eigenvector loadings on selected components

Once the number of principal components is selected, examine the
eigenvector loadings. Loadings for each component indicate each
variable's correlation with the component, so a high positive or
negative loading indicates that the component describes some aspect of
that variable's range.

### 5. Plot ordination diagrams

It is probably wise to plot scattergraphs of the first and second
principal component scores of all the rows (observations) in the data
matrix. If other principal components are to be used, then also plot
these scores in combination with the first two. This way, observations
that cluster together can be seen.

### 6. Biplots

Biplots are a nice way to summarize an ordination like PCA. They show
the tendencies in the data, but they are not an inferential test in any
way. They consist of two components:

- A scattergraph of ordination scores for observations (rows) in the matrix, like the ordination diagram above.
- A set of vectors representing the eigenvector loadings for each variable. These are arrows drawn from the origin to the designated coordinate.

## Inferential statistics following PCA

Principal components scores can be used like measured variables, i.e.,
they can be analyzed with statistics such as regression or ANOVA. There
are 2 criterion to use before doing this. First, the axes must be
normally distributed, which is easily checked with standard [normality
tests](math_normalitytests.md). If an axis is not normally
distributed, different inferential statistical tests, such as
non-parametric methods like Spearmans correlation or Kruskal Wallace
ANOVA can be used (see [here](math_correlation.md)). Also,
Monte-Carlo tests can be used, comparing the results of a correlation
test, with the same test run on a large number of randomized versions of
the data. The second criteria is that there should be no a priori
connection between the dependent and independent (the axes) variables in
your test. Therefore, when setting up the PCA, be sure to leave out the
classifying/dependent variables that you will be testing against the
ordination axes.

## Some resources

* [Short tutorial](http://www.iiap.res.in/astrostat/tuts/pca.html)
* An [in-depth tutorial](http://strata.uga.edu/software/pdf/pcaTutorial.pdf)using R.
* An [in-depth tutorial](http://www.snl.salk.edu/~shlens/pca.pdf) with MATLAB code.
* Another [in-depth tutorial](http://scholar.google.com/scholar_url?hl=en&q=http://www.sccg.sk/~haladova/principal_components.pdf&sa=X&scisig=AAGBfm3brQ976aczTJEORvef-6Eq4UZEFg&oi=scholarr)with MATLAB code.
* Much of this page is summarized from *Multivariate Statistics for the Environmental Sciences* by Peter J. A. Shaw.
