# MODIS NPP (MOD17)

It seems there are 2 versions of this product: 1) The original datasets produced by NASA, and 2) an improved version by the U. Montana NTSD group that reduces the amount of "cloud contamination" and improves the underlying climate dataset.

* [Main NTSD website](http://www.ntsg.umt.edu/project/mod17), see also the [NASA site](https://lpdaac.usgs.gov/dataset_discovery/modis/modis_products_table/mod17a3)

* [User guide](http://www.ntsg.umt.edu/sites/ntsg.umt.edu/files/modis/MOD17UsersGuide2015_v3.pdf)

* [Original, uncorrected data](http://e4ftl01.cr.usgs.gov/MOLT/)

* [Version 55](ftp://ftp.ntsg.umt.edu/pub/MODIS/NTSG_Products/MOD17/), available in several time formats:
    - Annual (A3, MOD17A3 directory) data
    - Monthly (Monthly A2, Monthly_MOD17A2 directory), in year and month subdirectories
    - 8 day (A2, MOD17A2 directory) in year and day of year subdirectories
    - In each subdirectory there is one .hdf file for each tile (see projection and tiling info below)
    


## References

[Improvements of the MODIS terrestrial gross and net primary production global data set](http://dx.doi.org/10.1016/j.rse.2004.12.011)

[Sensitivity of Moderate Resolution Imaging Spectroradiometer (MODIS) terrestrial primary production to the accuracy of meteorological reanalyses](http://dx.doi.org/10.1029/2004JG000004)

[Drought-Induced Reduction in GlobalTerrestrial Net Primary Production from 2000 Through 2009](http://dx.doi.org/10.1126/science.1192666) and [Supplemental Material](http://www.sciencemag.org/cgi/content/full/329/5994/940/DC1)


## Getting the data

1. Go to the links listed above and navigate to the correct directory
2. MODIS data comes in spatial extent tiles following the ["MODIS Sinusoidal tiling system"](https://lpdaac.usgs.gov/dataset_discovery/modis)
    - For New Mexico the correct tiles are is H8V5 and H9V5
