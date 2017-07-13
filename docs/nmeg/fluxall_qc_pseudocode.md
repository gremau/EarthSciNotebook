# Pseudocode for new fluxall qc processing

These are new scripts that will make up the new fluxall qc processing pipeline. This is run by site/year. Should enable showing corrections and gapfilling in diagnostic plots.

## General workflow

1. load fluxall file for site/year and create fluxall_raw

2. correct_and_calibrate
    1. input fluxall table (fluxall_raw)
    2. fix_datalogger_timestamps
    3. Apply radiation corrections/calibrations
    4. Precip fixes
    5. Correct flux data.
        - Burba
    6. Output corrected fluxall table (fluxall_qc)

3. remove_bad_data
    1. input  corrected fluxall table (fluxall_qc)
    2. fix_specific_problem_periods
    3. flag flux data
        - ustar, wind, etc
    4. exceptions
    5. Output rbd table (fluxall_qc_rbd)

4. gapfill_fluxall_qc
    1. input corrected, rbd table (fluxall_qc_rbd)
    2. fill fluxes from 30min
    3. fill flux from local (regression fit from another NMEG site)
    4. fill met gaps from nearby site
    5. Output gapfilled fluxall table (fluxall_qc_rbd_gf)

5. write output files
    1. site_year_fluxall_qc.txt output from fluxall_qc_rbd table
    2. site_year_fluxall_qc_gf.txt output from fluxall_qc_rbd_gf table.
    3. Possibly create and output a standardized 'for_gapfilling' file

## 2 types of plots

These can be toggled with a flag in master scripts

* QC/RBD plots - show all changes to data as they happen - data removed, corrections, etc.
* Summary plots - summaraize the data in a nice way, may indicate corrections to make of bad data to remove.

