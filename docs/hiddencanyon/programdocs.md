# Program documentation for Hidden Canyon data analysis

## Data files

## Functions

## Scripts

### process_injectiondata.m

Takes datalogger output files from the CO~2~ injection system,
calibrates data using the cal tank values, and then calculates ppm of
unknown samples.

* **File Input:** datalogger .dat file from injection (GUI selection by user)
* **User Input:** 
  * Allows exclusion of one data period (GUI selection by user)
  * Numbered peaks can be excluded (enter integer list at command line) - Fixes issue with bad peaks after high (14000ppm) cal injections. See Feb 21 [log entry](analysislog_1.md).
* **Outputs** //2 Plots// - One with raw datalogger data, cumsum, and calculated peaks, and one with calibration RMS values. //1 datafile// with integrals and calibrated CO~2~ ppm
