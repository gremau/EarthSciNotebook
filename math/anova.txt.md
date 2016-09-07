###### Analysis of Variance (ANOVA)

-   -   General resources \*\*

<!-- -->

-   [ A
    tutorial](http://www.psych.upenn.edu/~baron/rpsych/rpsych.html#htoc50 "wikilink")
    geared towards psychology research.

##### One Way

##### Two Way

##### Repeated Measures

In R, repeated measures ANOVA needs to be fit using *aov*, so that a
multi-stratum error term can be a part of the model (*lm* does not
support this). *lme* (from the nlme library'') can also be used for this
purpose, specifying the error terms in the *random=* argument.

` * `[`A` `compendium` `of`
`resources`](http://www.r-statistics.com/2010/04/repeated-measures-anova-with-r-tutorials/ "wikilink")\
` * `[`http://statistics.ats.ucla.edu/stat/r/seminars/Repeated_Measures/repeated_measures.htm`](http://statistics.ats.ucla.edu/stat/r/seminars/Repeated_Measures/repeated_measures.htm "wikilink")

##### Post-hoc analysis

If multiple treatments need to be compared after the experiment, a
couple types of post-hoc analyses can be used to test whether the means
of the treatments are significantly different. These are the Tukey range
test (also known as Tukey-Kramer, or Tukey HSD) and Scheffe's method.
