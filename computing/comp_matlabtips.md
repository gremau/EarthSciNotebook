# Matlab tips

Notes for using Matlab effectively for data analysis. **See also:**
[General programming](programming), [Sensor data
tips](sensordata_tips) pages

## Put date ticklabels on an X-axis

When plotting a timeseries it is often hard to tell when the data is
from because it is easier to plot against a sequential or decimal day,
rather than month, day, year, etc. This puts useful tickmarks and labels
on a timeseries plot: `%`datenum_h`is`a`vector`of`
`sequential`datenum`days`-`divide`up`this`series`into`
`20`tickmarks`ticklocations`=`linspace(min(datenum_h),`
`max(datenum_h),`20);`%`plot`against`the`datevec_h`
`sequence`plot(datenum_h,`sm(:,`i),`'k');`%`after`
`plotting`put`the`tick`marks`and`labels`in`the`
`correct`locations`set(gca,`'XTick',`ticklocations);`set(gca,`
`'XTickLabel',`ticklocations);`%`Call`the`datetick`function`
`with`'keepticks'`to`convert`the`label`on`each`tick`
`location`to`a`date.`datetick('x',`12,`'keepticks');`
