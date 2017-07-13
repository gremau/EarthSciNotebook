# NMEG FluxProc Priorities

1. Gapfill and partition the PJC and PJG datafiles
    * May require regenerating the "for_gapfilling" files with VPD (in hectapascals?) and a qc column.

4. What to do with separate Met and Li8100 data?
    * Archive raw card data for now.

5. Fluxflag scripts?

6. Temperature corrected longwave radiation does not make it to ameriflux files - seems that the uncorrected values are going into the files instead

7. Fluxall files are inconsistent in the dates that they contain. Some start at year/1/1 00:00 (last half hour of previous year), some start a half hour later. Some end a half hour early. This cause problems when combining the data with other dataloggers. Need to address this and create some timestamp conversion tools.

8. An unburned grassland (New_GLand) card may have been processed as GLand on 8/5/2014 (see incorrect datalogger id in the 7z file)

10. Where does the Air temperature in the for_gapfilling file come from - it is not from the qc file (see pj and pj girdle Dec 8, 2011 at 5pm)
    * It is actually derived from Tdry (dry bulb temperature in Kelvin) and converted to C.
    * but where does Tdry come from - it comes in with the flux data.
    * This is sonic air temperature (Ts), and it is corrected to be "dry temperature" by the "dry_air_conversion" file.

11. RBD file assigns the last header matching a list to air_temp_hmp and rH. At sites with multiple sensors this is often wrong - look at air temp at PJC.

12. There is no hmp RH data from PJ girdle for 2011 and 2012 (not in FLUXALL file), but something does get put in the qc and for gapfilling files - what is this? 
    * It is calculated from other hmp variables found in FLUXALL FILE

13. Rounding errors for PAR in Ameriflux Daily files  - see PJ Daily AF files (PAR rounded to thousands place)

14. There are 2 UNM_Ameriflux_filemaker  pipelines (regular and "_TWH"). The TWH version uses the output from the MPI online flux partitioning tool (old version). The new one uses the REddyProc R scripts (Accessed with UNM_run_gapfiller.m).

15. PJ Girdle 2014 fluxall file is missing a bunch of data - mostly the 10hz data

16. JSav 2013 Fluxall has lots of NAN columns in the TOB1 data - need to finish making Amflux files
    * apparently these exist in the TOB1 data also - maybe they can be filled with wireless data?

17. Soil data headers, including soilT, SWC and shf data are renamed from the incoming raw data  by the `UNM_Assign_soil_data_labels.m` script.
    * This interferes with the header resolution scripts, and it may make more sense to remove this and replace it with the header resolution system
        - Soil header changes would be put into the header resolution file (or maybe just for 2013 on?)
    *  Also, there is a separate file that deals with JSav 2009 - which seems like unnecessary code overlap



24. Variable names in old fluxall files (starting in around 2010) are different.
    * I have changed 'u_mean' to 'u_mean_unrot' in 2010 fluxall files from some sites.
    * I have changed 'windDirection(theta)' to 'wind_direction' in some 2010 fluxall files

25. Something is wrong with PAR at JSav in 2014. It is all getting normalized to zero.

26. PPine 2013 Ameriflux file
    * Fix UNM_fill_met_gaps_from_nearby_site.m so that it uses the correct data for PPine.
    * This should eliminate gaps in precip and shitty VPD gapfilling.

27. Add criteria and data removal for atmospheric stability parameters  and advection at sites
    * For stability and advection calculations see chapter in Lee, Massman, and Law book.
    * This will be done in RemoveBadData for now.

28. JSav 2013 Ameriflux problems.
    * Fluxes Reco, GPP, FC seem very low (magnitude and variability) between days 60-170.
    * Is there an incorrect hard cap on R, GPP, or FC for the springtime period in 2013? 
    * Is there a diurnal StdDev check that isn't functioning?

29. Make ameriflux file spit out Tsoil so we can test whether this makes for better flux filling/partitioning?

30. In the ameriflux files, there is no way to tell what values were locally gapfilled. This can be a problem if values calculated (in RBD, say) from missing met data end up as NaN, but the missing met data is later filled in with local or gapfiller data.

31. New precip problem at PJ Girdled from 1/1/2009 to 6/2/2009 (or a little earlier)
    * Data (no of tips) copied from PJC, then converted with the PJG multiplier (so precip is doubled)
