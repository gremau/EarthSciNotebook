# Using HDF and NetCDF files

## HDF-EOS files

MODIS data, and other NASA data comes packaged as .hdf files. These are HDF-EOS files, specified by NASA and based on the HDF4 specification. [More info here](http://www.hdfeos.org/index.php), and there are code examples for using HDF-EOS files with different languages [here](http://hdfeos.org/zoo/index.php). For a MOD17 example see [here](http://hdfeos.org/zoo/index_openLPDAAC_Examples.php#MOD).

Since HDF5 is the current and most supported HDF format, it may be easiest to first convert HDF-EOS files to HDF5 files using a [conversion tool](http://www.hdfgroup.org/h4toh5/download.html). Download and unpack then `cd` into that directory and run `./h4toh5 ~/path/to/file.hdf`. 

### Reading with python

If using a HDF5 files, [h5py](http://docs.h5py.org/en/latest/index.html) or [PyTables](http://www.pytables.org/index.html) can be used to access the data in the file.

If using HDF4 data with python, check these resources:

* [PyHDF info](http://www.hdfeos.org/software/pyhdf.php)
* In anaconda, you may want the [the conda-forge package](https://anaconda.org/conda-forge/pyhdf)
* [hdf4](https://github.com/fhs/python-hdf4) also seems to work

Also - maybe check this out:

* http://www.pymodis.org/


### Reprojecting the data

Usually these come in the a standard sinusoidal projection and there may or may not be lat/lon data provided in the file. If there is no lat/lon data it must be created using the file metadata (corner coordinates of the tile, cell size, etc). It is possible to do this and reproject with GDAL (which can find the file metadata using GetGeoTransform) and Basemap in Python (see [examples here](http://hdfeos.org/zoo/index.php))

If using only pyhdf, this:

https://lpdaac.usgs.gov/tools/modis_reprojection_tool

or this may help:

http://hdfeos.org/software/eos2dump.php

## NetCDF files

### Reading the file
Some of this cribbed from:

http://www.hydro.washington.edu/~jhamman/hydro-logic/blog/2013/10/12/plot-netcdf-data/

They can be opened by GDAL (though potentially a little tricky)

    ds = gdal.Open(mstmip_dir + 'BIOME-BGC_BG1_Monthly_NEP.nc4')

Or you can just use the ncdf-python module directly

    ncdf2 = Dataset(mstmip_dir + 'BIOME-BGC_BG1_Monthly_NEP.nc4')
    # Then pull out relevant variables
    nep = ncdf2.variables['NEP'][-1] # data for one day month
    lats = ncdf2.variables['lat'][:]
    lons = ncdf2.variables['lon'][:]
    ncdftime = ncdf2.variables['time'][:]
    nep_units = ncdf2.variables['NEP'].units


### Timestamps

You can use the time converter in the ncdftime module

    time_conv = utime('days since 1700-01-01 00:00:00')
    times = time_conv.num2date(ncdftime)
    print(times[num])

Or just create a numpy array
    td = np.array([np.timedelta64(int(i), 'D') for i in ncdftime ])
    times = td + np.datetime64('1700-01-01 00:00:00')
    print(times[-1])
