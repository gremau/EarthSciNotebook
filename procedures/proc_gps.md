# Georeferencing with GPS

It is essential to know where things are - research locales and
instrumentation, organisms or populations, geographic features, good
lunch spots, etc - here are some tips on assigning coordinates to them
in the field.

## Datum and coordinate conventions

The WGS84 datum seems to be generally accepted for ecological research
around the world and is the reference coordinate system used by the GPS
system. The primary, and most accurate geodetic datum in North America
is NAD83. So for survey grade work, it is best to use NAD83 in North
America. For standard accuracy work (handheld GPS) WGS84 and NAD83
should be interchangeable in North America.

Decimal degrees are usually the easiest to use, but UTM is also common.
Utah is in UTM zone 12N.

## Handheld GPS

Most handheld GPS systems are capable of around 3m horizontal position
accuracy.

## Differential GPS (DGPS)

For survey grade georeferencing (<1m horizontal accuracy), a DGPS can
be used. In these systems there is a base station that records a static
GPS position and a GPS rover that references its positions to the base
station. On occasion we have borrowed a Trimble 4700 DGPS system from
Geology and Geophysics at the U. of Utah. Information on its use is
provided by them at:
<http://thermal.gg.utah.edu/facilities/gps/index.shtml> (we used the RTK
method).

See the [Hidden Canyon
georeferencing](hiddencanyon/hc_georeferencing) page for info on
how we used this system.

## Data formats

Unfortunately there is no standard output data format for GPS data among
the many makers of GPS units. Luckily there are some open and
interchangeable geodata formats and software tools to do the conversion.

* [The`GPX`data`
`format](http://www.topografix.com/gpx.asp)\
* [GPSBabel`
`software](http://www.gpsbabel.org/)- excellent for converting data formats.
* FIXME - currently have no idea how to use Trimble DGPS data with any other software besides Trimble Geomatics Office.`
