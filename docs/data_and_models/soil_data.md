# Soil data sources

## Coterminous U.S.

SSURGO [description here](https://www.nrcs.usda.gov/wps/portal/nrcs/detail/soils/survey/geo/?cid=nrcs142p2_053627)

It exists in shapefile and gridded form (SSURGO and gSSURGO)

STATSGO - [description here](https://www.nrcs.usda.gov/wps/portal/nrcs/detail/soils/survey/geo/?cid=nrcs142p2_053629)



There are a variety of ways to get these data:

1. [Web Soil Survey](https://websoilsurvey.sc.egov.usda.gov/App/HomePage.htm) is a web-based download system that allows users to select a region of interest and download soil data layers. ROIs have to be pretty small.

2. [Geospatial Data Gateway](https://gdg.sc.egov.usda.gov/) allows downloads of gSSURGO, SSURGO, STATSGO2, by state or more specific areas.

3. [Soil Data Access](http://www.nrcs.usda.gov/wps/portal/nrcs/detail/soils/survey/geo/?cid=nrcs142p2_053627 ) is sort of an API to the NRCS database. Info on how to query this database can be found [here](https://sdmdataaccess.nrcs.usda.gov/QueryHelp.aspx). There are also some projects to allow access from R:
   
    - [Algorithms for Quantitative Pedology project page](https://ncss-tech.github.io/AQP/) has created multiple R packages for soil data access and analysis
    - [Tutorial 1](https://ncss-tech.github.io/AQP/soilDB/soilDB-Intro.html)
    - [Tutorial 2](https://ncss-tech.github.io/AQP/soilDB/SDA-tutorial.html)

4. [NASIS](https://www.nrcs.usda.gov/wps/portal/nrcs/detail/soils/survey/tools/?cid=nrcs142p2_053552) may be another option
