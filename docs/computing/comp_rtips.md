# R tips

## Installing and using libraries

Packages are installed from a CRAN repository to a local library
directory. The default users library must be created at
*~/R/x86_64-pc-linux-gnu-library/{version#}*, but packages can also
be installed to */usr/local/lib/R/site-library* if permissions allow.

Install packages using:

  install.packages(c('nlme', 'lattice', 'knitr', 'ggplot2'))

This will prompt the user to select a CRAN mirror (and make a user
library if it is not already there).

Packages can then be loaded from a library with:

  library('ggplot2')

Sometimes the core R packages on Debian go out of date and need to be
updated. Start R with *sudo* and run:

  update.packages()

For other, user-installed R packages, run
*update.packages('{packagename}')*.

## knitr

Knitr allows literate programming with R - i.e. R code is written into
latex, markdown, or other text markup formats. Running *knitr* will then
convert the document by processing the markup, running the R code, and
embedding all the output into a PDF, HTML, or document. This
functionality is accessible from Rstudio also.

It's easiest (for me) to use knitr with markdown. This means creating
*file.Rmd* and embedding code in "chunks" that look like:

~~~
```{r}
  plot(y ~ x)
```
~~~

There are a number of options that can be put in the braces at the start
of the chunk to influence how the code is run and incorporated into the
output of the file. The resulting *.Rmd* file can be converted (from
within R), by running *knit2html*:

~~~{.r}
library(knitr)
knit2html(file.Rmd)
~~~

#### Stitch

Stitch is knitr's most basic way to output results from an R script:

~~~{.r}
library('knitr')
stitch_rhtml('scriptname.r')
~~~

This outputs an .html file that embeds all code and output (plots,
tables, objects, etc) in the document. Nicely viewable in a browser.
*stitch* can also do latex, but its not working for me yet.

 **Resources**

* [knitr github page](https://github.com/yihui/knitr#readme)\
* A nice [tutorial](http://biostat.mc.vanderbilt.edu/wiki/Main/KnitrHowto)\
* Another nice, but basic, [tutorial](http://gforge.se/2012/08/getting-started-with-knitr-and-sweave/) on Sweave and Knitr.`
