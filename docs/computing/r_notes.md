# R notes

## Installing and updating

**On Debian**

To install R:

    sudo apt-get install r-base r-base-dev

**On MacOS**

    brew install r

### Package management

Install packages using `install.packages()`. Whenever R has a new update in the distribution (3.4 to 3.5, for example), packages will generally need to be reinstalled also. The location they are installed to can vary and R may ask.

Often R complains about missing Debian packages (curl, ssl) and may fail if miniconda/anaconda is already installed (may want to change dir name).

**On Debian**

Packages are installed from a CRAN repository to a local library
directory. The default users library must be created at
`~/R/x86_64-pc-linux-gnu-library/{version#}`, but packages can also
be installed to `/usr/local/lib/R/site-library` if permissions allow.

**On MacOS**

Packages are installed to `/Library/Frameworks/R.framework/Versions/3.6/Resources/library`

### Package list

 My usual list of packages to update is:

  install.packages(c('tidyverse', 'xts', 'rgdal', 'data.table', 'automap', 'forecast', 'ggmap', 'cowplot', 'raster', 'SPEI', 'lubridate'))

Sometimes the core R packages on Debian go out of date and need to be
updated. Start R with *sudo* and run:

  update.packages()

## Jupyter R notebooks

To run R in Jupyter notebooks install [IRKernel](https://irkernel.github.io/installation/#linux-panel) using the linux source method (libzmq3-dev first).

