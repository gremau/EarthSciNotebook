# Niwot/Fraser girdling study data QC

 **See also:** [Activity log](niwot_activitylog_1.md)

## Soil CO2 data

We use two methods of finding and removing bad data in our soil CO~2~
dataset. The first is event-based, where datapoints generated on bad
sampling days, or bad instrument runs are flagged and removed. Usually
this removes a large block of samples from a particular date. These are
explained in the first three subheadings below. The second method is to
remove datapoints that fall far outside of the distribution of a
statistic describing our data (outliers). In this case, we use a
regression line and remove data that falls too far away from this
predicted line. Finding and removing problematic data and outliers, is
done in the `irga_gasbench_process.m` script.

#### Problematic sampling dates

Sometimes sampling dates have lots of outliers. There may be a known
reason for this, or not. These are removed by flagging the IRGA date in
which they were run. \^ Bad sample dates \^ Description \^ Reason \^
Action \^ IRGA date \^ | 120717 (NWT) | Enriched d13C | Rain storm? |
Removed | 121008 | | | | | | |

#### Problematic IRGA data

IRGA run quality is assessed using the RMS error of the calibration tank
measurements. Lower values are better. \^ Bad IRGA dates \^ Description
\^ Reason \^ Action \^ | 110928 | ? | Problem with Licor integration |
Removed | | 111004 | ? | Problem with Licor integration | Removed | |
111102 | High RMS error | Bad syringe | none | | 121008 | Enriched d13C
| Bad sampling date (see above) | Removed | | | | | |

#### Problematic gasbench data

Gasbench/IRMS run quality is assessed using its distance from a
reference line. In 2011, this was the regression line for gasbench date
111209 (see Niwot_gasbench_verX.m comments around line 262). We
retained this line for 2012, but it may make sense to make a new one. \^
Bad Gasbench dates \^ Description \^ Reason \^ Action \^ | 111025 | Off
the ref. line | | Removed | | 111130 | Off the ref. line | | Removed | |
120831 | Follows last years ref line | New sample loop installed after
this date | Still there (for now) | | 121119 | NWT samples have low peak
areas | These failed and were re-run by Brad | Removed (NWT only) |

#### Outlier detection/removal

In 2011, outliers were removed by distance from a regression line of
IRMS area on IRGA CO~2~. It looks like this regression line was created
before removing all the bad sampling/instrument dates (above). This is
documented in the old Niwot_gasbench_verX.m scripts, and in Dave
Bowling's lab notebook #5, pp 58-59. For 2012 this was refined by
adding two other methods of bad-data removal.

Currently, two regression relationships, **IRMS area vs. IRGA
CO~2~** and **δ13C vs. 1/IRGA CO~2~**, are generated for each site
in 2011 and 2012. A threshold distance is set for each line and
datapoints beyond this threshold are removed. This threshold is the same
in both years and for both sites. This technique should remove anomalies
for CO~2~ (leaky vials, bad injections, IRMS area problems) and δ13C
(diffusional wierdness and IRMS issues) data.

![media/niwot_girdling/nwt_forestd13co2.png?180|Niwot aboveground forest
air d13C vs CO2 concentration] There are also deep (>10cm depth)
measurements that have near-atmospheric δ13C values (> -12permil).
This is most likely a mistake because any atmospheric air (-8 to
-12permil - see fig at right) that is advected into the soil mixes with
much more depleted CO~2~. These values are also removed (value > -12
permil AND measurement deeper than OA horizon). This was formerly done
using depth/concentration thresholds in the soilCO2_tdist.m file.

## Final QC'd data

 **Number of samples removed, 2011**

\^ Problem \^ IRGA dates \^ GB dates \^ IRGA/IRMS CO2 \^ d13C/invCO2 \^
Enr. deep d13CO2 \^ Total 2011 \^ | NWT | 70 | 10 | 9 | 1 | 5 | 95 | |
FEF | 49 | 56 | 15 | 4 | 0 | 124 | 219 samples removed total

 **Number of samples removed, 2012**

\^ Problem \^ IRGA dates \^ GB dates \^ IRGA/IRMS CO2 \^ d13C/invCO2 \^
Enr. deep d13CO2 \^ Total 2012 \^ | NWT | 70 | 20 | 4 | 4 | 2 | 100 | |
FEF | 0 | 0 | 0 | 4 | 7 | 11 | 111 samples removed total

![media/niwot_girdling/girdling_baddata2011.png?400|Bad data removed
2011]![media/niwot_girdling/girdling_baddata2012.png?400 |Bad data
removed 2012 - note 2 sample lines from gasbench]
