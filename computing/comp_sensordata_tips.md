###### Tips for working with sensor data

Collected tips for analyzing data in datalogger output files, SNOTEL
site datasets, or other continuous timeseries data.

 **See also:\*\* [General programming](programming),
        [Matlab tips](matlabtips), and [Python
        tips](pythontips) pages.

##### Normalizing sensor timeseries

I am experimenting with a number of ways to normalize the data from
sensors:

` * max-min normalization`\
` * minimum normalization`\
` * datetime minimum normalization`

An example MATLAB function to normalize the data several ways:
<code matlab normalize.m> % 0-1 normalization (0=min and 1=max for
series) if normtype == 1

`   in_max = max(in);`\
`   in_min = min(in);`\
`   norm = (in - in_min)./(in_max-in_min);`

% subtract min value, all series have a zero point (problem if there are
% negative values) elseif normtype == 2

`   in_min = min(in);`\
`   norm = (in - in_min);`\
`   `

% normalize by setting min to value at specific time (index given as
arg3) elseif normtype == 3

`   in_min = in(varargin{1});`\
`   norm = (in - in_min);`

~~~

##### Creating decimal day arrays from datalogger output

Campbell dataloggers typically give several date/time columns in a
datlogger file (depending of output commands), a year, a sequential day
(doy), and a 4 digit timestamp. Here is a way to convert that into a
decimal day array: <code python decday.py>

1.  create decimal day

year = m\[:,1\] day = m\[:,2\] \# a sequential day of 1-365 (or 366 in
leapyear) hhmm = m\[:,3\] \# timestamp formatted as hhmm hh = floor(hhmm
/ 100) mm = hhmm - hh \* 100 dd = day + (hh + (mm / 60)) / 24

1.  create a cumulative decimal day

year\_cum = year - 2009 \# the starting year is arbitrary dd\_cum =
(year\_cum \* 365) + dd ~~~

##### Data filtering, interpolation, and moving window statistics

Many techniques for filtering and smoothing timeseries data are
explicitly mathematical using moving means, variances, standard
deviations or other statistics.

See the [timeseries analysis page](math:timeseries) for more,
and for examples.
