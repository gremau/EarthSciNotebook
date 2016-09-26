# Exetainer Injection Method

This procedure is adapted from Nicole Trahan's and Andrew Moyes's
procedures for measuring CO~2~ in exetainers returned to the lab.
Concentration is measured on the LI-7000 IRGA, and CO~2~ isotope ratios
on the Campbell TDL in the Bowling lab using syringe injections from the
exetainers. The original method of measuring CO~2~ on the LI-7000 (still
shown below) developed by Nicole and Andrew was deprecated because it
was producing double peaks, and the sample integrals were often being
lost after injection of a sample. This was unacceptable for small
samples that also needed to be run for C isotopes. For this reason, the
LI-7000 was connected to a datalogger, and the injection integrals are
recorded by the datalogger now. The timeseries produced by this can now
be analyzed in MATLAB and bad peaks can be dealt with there.

Used for:
---------

* [Hidden`Canyon`soil`
`respiration](hc_ecohydrology:soilresplog_1)measurements (in winter)

(last revised on 120112 by Allison Chan)

#### LI-7000

- Turn on Li-7000 about 20-30 minutes before starting injections
- While it is warming up, press “Shift, 6” to change the bottom display on the Li-7000.  Press “Pump Off” and then change the septum.
- After the septum is replaced, press “Pump Fast” (a star should show up next to it).
- Change the bottom display back to the “Reference/Calibration” mode by pressing “Shift, 1” and press “2” to switch the top display to show integrals.
- Press “calib” on the bottom display and then choose “edit” (if “edit” is not an option, select “more”, until it becomes a choice in the bottom left corner).  In the edit menu, use the arrows to scroll down, select “make cell B match cell A”, and press “Ok”.  Then press “DoCO2” and “Done”.  On the top screen, the CO2 A and CO2 B concentrations should match.
  - **This calibration should be done as often as needed throughout the injections**.  The two cells should be within 0.01-0.03 μm/m.`

#### Datalogger

- Turn on the CR23X datalogger and connect to “Nebo” laptop (requires USB converter cord).  Open Loggernet, click on the “connect” icon and connect to datalogger.  
- Under the “Program” section of the Connect window, be sure the co2_inj_v1.dld program is selected, then press Send and agree to all further windows that pop up (this should overwrite the previous round of data collection)
  - **NOTE**: Resending the program doesn’t actually seem to erase the datalogger.  To manually erase the datalogger, press *A on the CR23X keypad and then press A 4 times to get to the Allocation Program Bytes screen.  Then enter 98765 and then A. (Not erasing the datalogger is only a problem in that will take longer to download data).
- After sending the program, press 1 next to Graphs.  At this point, begin injections.`

#### Injections

- Once the machine has warmed up, inject standards, using tanks that fit the CO2 range of the samples.  Tanks being used for the Niwot samples are 15 (395.78 ppm), J39 (3144 ppm), and J29 (14,051 ppm).  Change the septa on the tanks about every 75-100 samples.  After opening the tanks, flush the headspace with a 1.0 ml syringe with a sideport needle.
  - Be sure to support the needle when pushing into or pulling out of the septum to prevent the needle from bending.  Also be sure to hold the base of the needle when pulling out of the septum to prevent needle from being pulled off, and check periodically to make sure the plunger is screwed into the base.
- Use a 1.0 ml syringe with a sideport needle and flush it 3 times with the first standard using the open and close sliders on the syringe.  Then fill the syringe up to 1.0 ml, close the syringe, withdraw it from the septum and compress it to 0.6 ml.
- Bring the pressurized sample back to the Li-7000 and just before injecting into the septum, open the syringe and compress to 0.5 ml, then inject the 0.5 ml into the machine.  
- Inject one sample of each of the 3 standards before beginning injecting unknowns.  The three standards should be injected (in an alternating order) after about every 12-15 samples.  
- To inject unknowns, insert the needle into the exetainer and withdraw about 0.5 ml and flush.  Insert the needle again and flush about 3 times with the needle in the exetainer before pulling a 0.8 ml sample.  Close the syringe, withdraw the needle, and compress the sample to 0.6 ml.  As with the standards, open the syringe and compress to 0.5 ml and then inject 0.5 ml into the Li-7000.
- Finish with one injection of each of the 3 standards.
- To download the data, click Custom, under the Data Collection section of the Connect screen.  Name the data file and select location to save.  Then click Collect.`

## Old Li-Cor 7000/TDL-TGA Method (Nicole/Andrew's)

See note at top of page about why this method was deprecated.

- Collect Data if a program was running (not needed for concentration measurements on the LI-7000).
  - Open loggernet, click connect
  - If a program was running, collect the data before you start injections. Click custom under data collection in the connect screen.
  - If Lab_TGA_CR5000 (roof air data collection) was running (which usually it is if the laser is in the lab) check one.sec and ten.min. Highlight one.sec, click change file name, change the data to today’s date and click save. Do the same to ten.min. Make sure file format is Binary Table Data TOB1 and collect mode is set to All the Data. Then click start collection.
  - When all of the data has been collected (may be a while) click disconnect on the left hand corner of the connect screen.
- Start LI-7000 if the concentration of CO2 is desired
  - Turn on the LI-7000, allow to warm up for about 5 minutes.
  - While waiting, press 2 on the keypad on the right to move to the correct display screen. Press shift-6, turn the pump off.
  - With the pump off, change the septum. Be sure to screw in swage nuts gently and center washers. Turn pump back on, and make sure there is a star next to **pmp med**. Press shift then 1 to get back to the display screen.
  - Press calib on the bottom of the screen. Press edit, then use the arrows to highlight make cell B match cell A, press ok. Then press DoCO2 on the bottom of the screen. When CO2Aµm/m matches CO2Bµm/m (which should be zero) press done. 
    - **NOTE**: Do this anytime during the procedure when CO2Bµm/m is + or – 0.05 (or even ± 0.01-0.03). Check these values for drift before each injection.  Press 2 to return to the correct display screen when finished.
  - Pick 3 tanks to be standards. For example, Nicole’s samples range in concentration from 400-3000ppm so she uses tanks J26 (433ppm), J59 (1504ppm), and J39 (3144ppm) as standards. Change the septum on the tanks. Open tanks and flush the septum headspace with a double ended needle. 
    - **NOTE**: When using the syringe ALWAYS support the needle when pushing into or pulling out of the septa. If not the needle will bend. Also hold the needle base when pulling needle out of septa and check the syringe periodically to make sure the metal base with the plunger is tightly screwed in.
  - Take a 1.0ml syringe and flush it 3 times with your first standard using the open and close sliders on the syringe. Fill the syringe all the way up, close the syringe, withdraw it from the septum, and compress the standard gas until you feel resistance or until you get to 0.6ml. This pressurizes the syringe to avoid ambient contamination. 
  - Walk back to the LI-7000 and just before injecting into its septum, open the syringe and compress until you reach 0.5ml, then inject into the LI-7000. (**NOTE**: you will always inject 0.5ml into the LI-7000.)  Record the Integral value on the screen. Repeat this 3 times or more for each tank before you start and when you finish.  CO2 integral values should range within ± 5% of one another.
  - After injecting your standards you are ready to inject your unknowns. The procedure is similar, but less sample is flushed out of the vial. Insert the needle into the sample vial, fill the syringe to about 0.5, then withdraw and flush. Reinsert the syringe and flush several times **in the sample vial**. Then pull a 0.8ml sample, withdraw needle, compress to 0.6ml, inject 0.5ml and record the Integral as above.
    - ** Be mindful of how much sample you may need to do isotopes (up to 5ml) and keep that much in the vial.**
  - Before starting injections on the laser I usually get about 15-20 samples ahead on the LI-7000. (See page 6 for lab notebook set-up) 
- Starting syringe program on the laser
  - On the valve relay controller switch 5 on and 1-4, 6-16 off. Unscrew the cap that reads remove for zero and change the septum where the samples are injected.
  - Under stations on the connect screen highlight Syringe_CR5000 and press connect. Under program click send and highlight SYR_V10.CR5 then click open, then yes, then ok.
  - Make sure graph 1,2 and numeric display 1 appear. If not make them appear using data displays on the connect screen (you may have to hit ‘start’ manually).
  - Look at Numeric Display 2, use the checklist on the next page to make sure the laser is on the lines and running properly.
    - Checklist:
      - LaserTemp: 95.60,  If off, check for L N2, notify Andrew or Dave
      - RefDetTemp: 5
      - RefDetTemp: 5
      - RefDetTransA: around 47 (ranges between 40-50)
      - RefDetTransB: around 37 (should be roughly 10 units away from TransA) (ranges between 30-40)
      - DCCurrentA and DCCurrentB are exactly 4.5 units apart 
      - Cell T: about 30,  If off, heater may be off in box
      - TGA pressure: about 22 ,  If off pump may have issues
  - If the numbers on the screen do not match up with the criteria on the checklist there is something wrong with the laser. If DCCurrentA and DCCurrent B are not 4.5 units apart then the laser is most likely off the lines. Get Dave or Andrew to put the laser back on the lines.
  - Turn the handle from roof air to Inj zero.
  - Finish step 2.
- Running Injections on the Laser
  - Before starting syringe program make sure your notebook is set up properly (see page). Also make sure that you are at least 15-20 samples ahead if using LI-7000. 
    - **NOTE**: You will be using tanks T1 (J39), T2 (J46), and T3 (J48) as standards. Always inject them in that order: T1, T2, T3. Always start with and end with the standards. Inject the standards after injecting 3-6 gas samples (see page 6). The amount of sample injected depends upon the concentration of CO2 of the sample or the integral if using LI-7000 (see page 7). Always write the injection amount next to the sample ID in your notebook (see page 6). You will always inject 0.8mL for the standards (T1,T2, T3) because they are ~3000ppm. The type of syringe used depends on injection amount (see page 7).
  - Change septum on standard tanks T1 (-8‰), T2 (-20‰), and T3 (-31‰). Open tank valves. Use a two-ended needle through septum and valve to flush the area where the septum is. Always use the long end with the sharper tip to minimize damage to the septa.
  - Turn handle from roof air to Inj Zero.
  - Look at the clocks on the connect screen. Sometimes the two clocks do not match up, if this happens click set station clocks. (**NOTE** Andrew would prefer if this step is ignored for now). 
  - Send Syringe_CR5000 program about 1.5 minutes before X:00, X:10, X:20, X:30, X:40, or X:50. This will give you enough time to prepare your first injection which is T1 and the syringe program always starts the first injection in multiples of 10 minutes starting from :00, :10, :20, :30, :40, or :50.
  - You will inject every 2 minutes (120 sec.) There is a counter, Inj Time (Numeric Display 1), that counts up to 110 and then from -10 to 0. Keep your eye on Inj Time and always inject on time 0. You will see it count from 108, 109, -10, -9, -8, ……, -1, 0, 1.(At about -6 I open the syringe that contains the gas sample and push until I am at the injection size so that I can immediately inject the sample at 0). Pay attention to InjNumber, make sure it matches what is in your notebook (see pg 6).
    - **NOTE**: To collect the standard gas samples use the 5mL syringe. Flush the syringe with the standard at least 3 times. Then fill syringe all the way up and push down until you feel resistance. To collect a gas sample only flush the syringe once (if using the 5mL syringe only go up to 0.5 mL then flush) then fill the syringe all the way up and push down until you feel resistance.
    - **SYRINGE NOTES** 
      - 5mL Syringe: Used for injection amounts 0.5mL – max. Max (an integral < 45) is anything over 2.5mL. For max, flush the syringe like normal, then fill up the 5mL syringe. Press down just until it stops. From my experience that is usually around the 2.8-3.2mL mark. Do not open syringe prior to injecting just simply place needle in septum open syringe and inject.
      - 1mL Syringe: Used for injection amounts 0.1mL-0.5mL.
      - 0.5mL Syringe: Used for injection amounts 0.01mL-0.1mL.
    - **IMPORTANT**: Keep an eye on graph 2 and numeric display 1. If you see numbers drifting (especially the DC currents) stop immediately, the laseris off the lines.
  - At your last injection, which should be T3, do not start collecting data until that injection has run through (until injection number is 1 + your last injection).
- Finishing Injections
  - After you have let your last sample run through click custom under data collection. Check onesec, tenHZ, and tenmin. Highlight onesec, click change file name, change the date to todays date, click save. Repeat this for tenHZ and tenmin. Make sure collect mode is All the Data, File Mode is Append to End of File, and File Format is Binary Table Data TOB1. Click start collection.
  - After data has been collected click disconnect.
  - If Lab_TGA_CR5000 was running prior to injections switch 1-5 to auto and 6-16 off on the valve relay controller. (Alternately, leave 5 on, and 1-4 off- check with Andrew).
  - Turn handle from Inj zero to Roof air and place the cap back on.
  - Click on Lab_TGA_CR5000 in stations, click connect, click send. Highlight ASB_roof_V1.CR5. Click open, then yes, then ok.
  - **NOTE:** Remember to close all tanks that were used and turn off the LI-7000.  Leave lap top running.
- Running the Data File on MATLAB
  - Collect the file hzdate.dat in the injection folder on the desktop. The os and tm files are only used as a record of the laser’s performance. Save the file to you computer (or a computer that has MATLAB).
  - Open MATLAB. In the editor window open SYR_10Hz_Process_v11.m. You will find this here: \\Bowling_nas\Bowlinglab\backed up\matlab m files. This is the most current MATLAB program that will run your data file.
  - Go to line 37 and change datapath to where you have saved your hzdate.dat. Save.
  - In the command window type in or copy and paste the function SYR_10Hz_Process_v11.
  - The datapath will come up, select your hzdate.dat file.
  - Type in # of injections (use all injection times, even ones missed).
  - Type in the injection numbers of all the T1 injections in order (ex: [1;8;12;18;25])
  - If all injections aren’t good or injections are missed, comment out line 119 and uncomment out line 120 in the code. Specify the good sets of injections.
  - MATLAB will go through each injection individually and the output file will be an excel file.csv that will be in the same place as your input hzdate.dat file.`

## Notes for Hidden Canyon samples

* Tanks/concentrations used: J39/3144ppm, J59/1504ppm, J20/461.23ppm (used once), J25/395ppm, and the big red 6000ppm tank (6356.6ppm).
* Since isotopes are not being measured, I am flushing the syringe with 0.8ml of sample gas once before drawing the injection sample.
* Sample draw is to 0.8ml, which is then compressed to 0.6.
* Injection volume is still 0.5ml`
