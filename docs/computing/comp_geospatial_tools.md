# Geospatial data tools

This page is a placeholder for procedures that involve geospatial data.
There are a few links. That is all.


## General tools

* [Open Source Geospation Foundation (OSGeo)](http://www.osgeo.org/)- provides a portal to many open source geospatial software projects, like:
  * [GRASS desktop GIS](http://grass.osgeo.org/)- geospatial data management and analysis, image processing, graphics/maps production, spatial modeling, and visualization.
  * [Qgis](http://qgis.osgeo.org/)- a more user friendly desktop GIS that supports vector, raster, and database formats and offers integration with GRASS.
  * [GDAL libraries](http://www.gdal.org/)- translator library for many raster geospatial data formats (Geospatial Data Abstraction Library)
  * [OGR libraries](http://www.gdal.org/ogr/index.html)- translator library for simple features vector data (nowadays a subset of GDAL).
* [NCO](http://nco.sourceforge.net/)- a collection of utilities that aid manipulation and analysis of gridded scientific data (like climate/circulation data)

## Python tools

* [GDAL/OGR bindings for Python](https://pypi.python.org/pypi/GDAL/) - the bindings to allow Python to call GDAL and OGR (syntax mostly follows the C++ class definitions)
    - [This site](https://pcjericks.github.io/py-gdalogr-cookbook/index.html) provides some examples of how to use the bindings)
* [Basemap](http://matplotlib.org/basemap/users/intro.html) - a library for 2D mapping (in Anaconda)
    - NOTE - the current version of Basemap in Anaconda requires an old version of GEOS that causes some GDAL import issues. A workaround is to install basemap (with conda or from the [conda-forge package](https://anaconda.org/conda-forge/basemap)) and let `conda` downgrade GDAL, libgdal, and GEOS. May need to make symbolic links to any missing dynamic libraries in the correct environment path ([See here](http://stackoverflow.com/questions/36268322/ddg#36295620))
