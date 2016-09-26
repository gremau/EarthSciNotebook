# EA-IRMS analysis at SIRFER (U of U)

This protocol was adapted from Brad Erkkila's and Abby Howell-Dinger's
descriptions of how to run samples on the EA-IRMS systems at the
University of Utah's [SIRFER
facility](http://sirfer.utah.edu). It mainly addresses C and
N analysis (% and 13C/15N) of soil samples, but could be adapted for
other uses.

## Instruments

There are two IRMS units that have elemental analyzer (EA) front ends
available, Madeye Moody, and Saltbush Bill. Madeye has a larger peak
area range and is therefore more suitable for soils (which vary
radically in C & N concentrations). The following protocol is suitable
for both units, but there are some slight adjustments depending on which
machine is being used.

* Reference gases (which are selected through the Conflo interface) are plumbed differently
  * Saltbush reference 1 = N`~`2`~`, reference 2 = CO`~`2`~\
  * Madeye is reversed - reference 1 = CO`~`2`~`, reference 2 = N`~`2`~\
* Valve placement is a bit different
  * The autoloader He pressure valve is directly under the autosampler on Madeye, and behind the EA instrument on Saltbush.`

## Protocol

- Close the isolation valve below the autosampler.
- Loosen the three screws holding the top of autosampler and open the door. If it won't open after the screws are moved away, briefly pressurize the autosampler chamber with He gas (then turn off).
- Make sure that well 50 is aligned over the hole into the combustion chamber, and that wheel advances such that samples will not be able to hang in the wheel.
  - It may be necessary to advance the wheel a half turn manually (using manual advance box to right of sampler).
  - Use the manual advance button, with the toggle at 50 or 100 samples, as needed to check this.
- Load the samples into the sample wheel in sequential order (1-50, or 1-100 depending on which wheel is being used).
- Close the sampler and replace and tighten the screws.
- Open the vacuum to the autosampler using the green valve behind it.
- Tighten the screws on the autosampler door again. //The autosampler chamber will continue to be evacuated as the next steps are completed//.
- Fill out the `elog` with the data for this EA-IRMS run (name, job #, etc). The `elog` is an excel file found on the desktop of the unit.
- Open the EA loader spreadsheet and enter sample ID and weight information.
  - Open MS Excel > recently used documents > more, and open either the 50 or 100 sample EA_loader.xls file.
  - Enter sample ID's in column A, starting with row 16 (the first 15 are conditioners).
  - Enter sample weights in column B :?: using micrograms. These will be automatically converted to milligrams in the next column to the right.
- Now open the IsoDat Acquisition software, located in the Windows XP quick launch bar (lower left of desktop).
- In Acquisition, we must open a measurement instruction sequence.
  - These are located in the Sequences tab on the lower left window of the interface.
  - For CN analysis we choose `N2_CO2+He_1.seq`:?:
  - This should open a datasheet window and some other stuff.
- **If the instrument has recently been used with another front end** it will need to be changed back to the EA Conflo interface.
  - This is done using a cluster of valves below the left side of the mass spec.
  - Close the pinvalve marked Otto (on Madeye :?:).
  - Open the EA pinvalve.
  - Make sure the green MS valve is open.
- Now copy and paste the sample ID's and weights from the EA_loader.xls file to the Acquisition datasheet. Column A (IDs) should go in Acquisition's `Identifier`
`1` column, and Column D (weights) should be copied to the `Amount` column.
- Make sure that the column to the right of Identifier 1 correctly shows which samples are samples, which are references (with an RM), and which are other types of samples.
- Also make sure that the Methods column lists the correct method for all the samples (N2_CO2+He_1.seq).
- Fill out the Comments column - this collects quality control and calibration data for every run.
  - List the pressure (to the nearest 100psi) of all the reference gases
    - Primary He (Orange)
    - Secondary He (Orange - regulator marked secondary)
    - N`~`2`~(Blue)
    - CO`~`2`~(Silver)
    - O`~`2`~(Green - in middle of room).
  - Fill in mV value for a peak center on N`~`2`~(mass 28) and CO`~`2`~(mass 44).
    - Select N`~`2`~in the dropdown on the lower left of the interface
    - Open the Conflo interface (middle left window of interface) and turn off all reference gases other than N`~`2`~`.
    - Push the peak center button (green bell curve on upper far left).
    - Do the same process for CO`~`2`~(first changing dropdown).
    - There is also the possibility to do a jump calibration (ask Abby or Leslie Chesson).
  - Check the background values for N`~`2`~\
    - Switch dropdown menu to N`~`2`~\
    - Turn off all reference gases in the Conflo interface
    - Record mV for mass 28 and 29.
  - Time to jump
    - Open methods tab (lower left of interface)
    - Go to the method being used N2_CO2....
    - Go to time events
    - Add together the CO`~`2`~switch time and the wait time (should be something like 290).
  - Record the number of samples on the combustion column (counter on front of EA).
  - Record the furnace temperature
- Now close the vacuum valve.
- Pressurize the autosampler chamber with He gas, gradually letting the pressure rise to the mark on the chamber gauge.
- Open the isolation valve.
- In the IsoDat Acquisition interface, highlight the datasheet rows containing the samples to be run.
- Open the `Acquisition` menu and select `Start`.
- In the dialogue that opens,
  - Add a folder name (usually the job number)
  - Delete acquisition from the filename field.
  - Export the file name to job #.
  - Check the background (should show low N2 background #s) before hitting OK
- The job is now running - watch the first samples go through
  - there should be a flat-topped reference gas set of peaks, then 2 peaks for N, a blip related to the IRMS jump, then 3  peaks for C, and another flat topped reference peak.`

## Data reduction

- Download data from the EA-IRMS computer.
  - Link to EA-IRMS results on the desktop.
  - Datafile will be in the directory full of Excel files.
- Open the CHNOS template. This spreadsheet has:
  - Two sheets for raw data (Sample gas 1= N, Sample gas 2 = C).
  - Two data correction template sheets.
- Copy the first gas (N) and second gas (C) raw data and header row over to appropriate raw data sheets. Again, N is sample gas 1, and C is sample gas 2.
- Make sure that the headers match what is in the CHNOS template, then delete the extra header.
- Sort the rows by peak number, so that sample peaks are at the top of each sample gas sheet.
  - Peak 1 = reference peak
  - Peak 2 = N peak
  - Peak 3 = C peak
  - Peak 4 = reference peak
- Insert 5 blank rows between peaks 1 and 2 (Sample gas 1 sheet), and between peaks 4 and 3 (Sample gas 2 sheet).
- Select primary and secondary references from the dropdown menus in the upper left of the data correction template.
- Enter the start row and end row in the correction sheet for each gas. The correction sheet should then populate with the correct values from the sample gas sheets.
- Count the number of lines.
  - Are they the same for each gas (were any peaks too small)?
  - Does it match the number of samples?
- Enter the latest jump value in its cell - usually this is 290 for CN analysis.
- Enter the values for the secondary reference material (mean and sigma). All secondary reference results (right side of correction sheet) should then populate with the number of standard deviations. Consider discarding any over 2.
- For each of the sample gases:
  - Plot the reference gas peaks
  - Plot the background values
  - Look for peak areas less than 15 (N) - these are likely too small.
- The chromatograms (peaks) can also be examined on the machine itself (the entire run is saved).
  - Open the `Workspace` program.
  - Open the directory named with the job number.
  - All chromatograms are saved according to number, double click to open.
  - There is a table under the chromatogram with a column for `Area`
`All` with volt-seconds units.
  - For N peaks, peak areas less than 15 volt-seconds are too small.
  - For C peaks, large samples will result in squared-off peaks (sensor maxed out).
- Check whether any corrections are justified.
- Import the references into the filemaker database.`
