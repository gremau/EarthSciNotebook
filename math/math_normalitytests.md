###### Testing for Normality

Many inferential statistical procedures require that data be normally
distributed. Here are a few ways to check if this is the case.

 **Note\*\* that the conventional wisdom that these tests must be
        applied before using normal theory statistical procedures is
        debated (see
        [here](http://www.r-bloggers.com/normality-tests-don%E2%80%99t-do-what-you-think-they-do/)
        and
        [here](http://stackoverflow.com/questions/7781798/seeing-if-data-is-normally-distributed-in-r/)).
        Unless the sample size is very small, it is probably best to
        proceed with the statistical procedures when the data are
        //approximately// normal. Assessing //approximate// normality
        might best be accomplished using the graphical methods below.

##### Graphical methods

Q-Q plots

p-p plots

Histograms or density plots

##### Formal tests

These test AGAINST the null hypothesis that the data tested are normal.
Low p values reject the null hypothesis, meaning that the data cannot be
assumed to be normal. High p values fail to reject the null, and the
data may (or may not) be normally distributed.

#### Shapiro-Wilks

#### Anderson-Darling

#### Kolmogorov-Smirnov

##### Resources

` * `[ `Tutorial` `using`
`R`](http://www.u.arizona.edu/~kuchi/Courses/MAT167/Files/LH_LEC.0450.RandVars.AssesNorm.pdf)
