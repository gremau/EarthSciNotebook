# Li-Cor 6400 with Soil Respiration Chamber

This instrument measures soil respiration fluxes at the soil surface. It
consists of the Li-Cor 6400 Portable Photosynthesis system, coupled to
the Li-Cor 6400-09 Soil CO~2~ Flux Chamber.

This system is currently in use measuring [soil respiration at Hidden
Canyon](hc_ecohydrology:soilresplog_1) and site-specific
additions to this protocol will be posted on the linked page.

## Measurement protocol

 **This protocol is adapted from the one compiled and edited by
        Claire Lunch and Suzanne Bethers in 2003 and 2004 for use at
        Corral Pocket.**

//Notes in italics signify parameters or settings that will change
depending on the site's flux rate or environmental conditions. See the
notes at the end of the protocol.//

- Connect tubing and electronics - see illustrations in 6400-09 manual.
- Turn on 6400
- Select `6400-09`Soil`
`Chamber` configuration and answer `Y` to `Is`chamber/IRGA`
`connected?` \
- Select `New`Msmnts` (F4) from main menu
- Select menu level 1 and press `Open`Log`File` (F1)
- Enter name of soil respiration file in form `SITE_yymmdd`, and press enter when asked for comments.
- Select menu level 3 (press 3 on keyboard) and press `Aux`OP`
`Param` (F2) and set prompts to the following:
  - `Extra`Draw`Down`
`(ppm)*= 0 (//or more at higher fluxes//)
  - `Flow`During`Draw`
`Down` = 350 (//or more at higher fluxes//)
  - `Dead`Time`(secs)*= 15 (//or more at higher fluxes//)
  - `Min`Measurement`Time`(secs)*= 30
- Select menu level 7, press `Log`Only`
`Final` (F4) and select `Everything` \
- Press `Esc` to return to main menu
- Allow instrument to warm up for about 20 minutes
- Zero the IRGA (Do this every time):
  - Disconnect the "Console Return" hose from the "Chamber Inlet" hose (both are marked with black shrink wrap).
  - Unscrew the plug from the "To-Sample" hose (at top of IRGA assembly, marked with black wrap) and plug the "Chamber Inlet" hose (disconnected from console in Step 1) with it.
  - Connect the "Console Return" hose to the "To-Sample" tube (black wrap to black wrap)
  - Turn scrub/bypass knobs (upper, larger knobs) on both chemicals to full scrub
  - From the main menu on the 6400 press `Calib`Menu` (F3)
  - Choose `IRGA`Zero`(CO2S,`
`H20S)*and say `Y` to the questions that follow
  - Wait for CO2S and H2OS to become stable close to zero (or just below). If they do not drop to zero check the scrub chemicals and knobs, and all plumbing. 
  - When numbers are stable choose `Zero`CO2&H20` (F3)
  - Press `Quit` (F5) to return to calibration menu
- Span (can be done in the lab periodically, with a small field cal tank, or with atmospheric air)
  - Disconnect the "Console Return" tube from the "To-Sample" tube
  - Connect the span gas tube (from toggle valve on cal tank) to the "To-Sample" tube
  - In calibration menu, choose `IRGA`
`Span` and say `Y` to the questions that follow
  - Throw toggle to open the cal tank valve
  - Wait for CO2S to become stable
  - Close the toggle valve on the cal tank and reconnect the "Console Return" tube to the "Chamber Inlet" tube (while flow is on, the "Console Return" tubing inlet acts as a vent; when flow is off, gas can diffuse back into the chamber through that vent)
  - Press `CO2S` (F2)
  - Use arrow keys to adjust CO2S to the cal tank value (measured)
  - Press `Done` (F5) to return to calibration menu
- Select `View,`Store,`Zeros`&`Spans` \
  - Press `Store` (F1)
  - Press `Quit` (F5) to return to calibration menu
  - Press `Esc` to return to main menu
- Re-plumb the system to measurement setup (see illustrations in manual) and remove the white cap from bottom of chamber
- Turn the knob on the CO`~`2`~scrub (soda-lime) //one half-turn away from full bypass// (It will probably be necessary to fiddle with this later -- watch the CO`~`2`~drop during scrubbing: it should fall steadily and overshoot `Target`
`-`Delta` slightly, but not my more than 5-10 ppm)
- Select `New`Msmnts` (F4) from the main menu
- Insert the soil temperature probe to //5-15cm depth// near soil collar **(Currently this probe is broken, and it sits on the chamber and measures chamber/air temperature. A separate probe is used to measure the soil at 5 & 15 cm depths)**
- Lay the chamber on its side close to the ground. Face away from the chamber or hold your breath. Wait for CO2S (Monitor in `New`
`Measurement` mode) to stabilize. This is `Target` (unlikely to change from plot to plot, but it is a good idea to check CO2S before each plot to make sure you haven't breathed in the chamber or hit a funny CO`~`2`~pocket)
- Measure the height of the soil collar rim above the interior soil level. Subtract 2cm, then multiply by -1. This is `Insertion`
`depth`.
- Select menu level 7 and press `Start` (F3)
- You will be prompted for:
  - `Target`: found in step 18
  - `Delta`: //1 is default for low flux rates, but this is the most useful parameter to adjust for varying conditions. When fluxes are high `Delta` of 2 or 3 may be necessary. When live plants are present in the collars, `Delta` = 5-10. See general comments below.//
  - `Plot`#`: enter the number of the plot being measured
  - `Insertion`Depth`: found in step 19
- The last prompt is `Append`to`current`log`file?`
`y/n`. Place soil chamber gently on collar (don't press down) and press `Y` \
- Write the following in the field book as the measurement cycles take place.
  - Time
  - Plot #
  - Insertion Depth
  - Target
  - Efflux for each of the 3 measurement cycles - the 6400 beeps during measurement and the instantaneous efflux is displayed. When the beeping stops and the machine pumps down for the next measurement, the final efflux value for the previous cycle is displayed. This number should be recorded (There will be 3 cycles per measurement).
  - Soil temp //at 5 & 15 cm depth// during the measurement
  - Air temp inside the chamber (at the end of the final measurement cycle), displayed under `Tsch_C` \
  - //Air temp outside the chamber (`Tsoil_C` while the Li-Cor probe is busted)//
  - Note anything unusual!!
- When the machine is done move to the next collar and repeat from step 17.`

Measurement notes
-----------------

- Steps 5-8 must be performed every time the 6400 is turned off and back on!
- Battery voltage is displayed on the main menu and also under display `g` in `New`
`Measurements` mode. It is a good idea to check this once in a while, but a good pair of batteries generally lasts 3-4 hours. Think about changing them when voltage drops below 12v.
- Keep the console out of direct sunlight, especially if it is hot. It must be shaded with something or else the screen will eventually go blank (LCD problem)

Site variability notes
----------------------

These directions were written for use at Corral Pocket, which has
extremely low CO~2~ fluxes. At higher productivity sites several things
will likely need changing:

- Turn up the soda-lime scrub knob
- Increase the flow during draw-down and/or add an extra draw-down
- Increase the dead time
- Increase `Delta` 

Increasing *Delta* ensures that [CO~2~] does not shoot through the
measurement range too fast. The other changes accomodate the need for a
overshoot of *Target-Delta*. There is an initial spike in [CO~2~]
following the scrub, which is physical rather than biological and should
not be measured. By extending the time and CO~2~ range before
measurement begins, you avoid including that spike.

At low fluxes, the most time-consuming part of the measurement can be
waiting around while CO~2~ rises after the scrub. Keeping the
scrub/bypass know on the soda-lime as close to bypass as possible is
helpful, as is a careful choice of *Delta* value. *Delta* should be
large enough so that rising from *Target-Delta* to *Target+Delta* takes
some time (the machine should beep a dozen times or so), but small
enough so that [CO~2~] actually reaches *Target+Delta* (or close to
it) before the machine stops the measurement automatically. If [CO~2~]
does not even reach *Target*, *Delta* is too large.

If the scrub seems to overshoot *Target-Delta* by a large margin, even
with the scrub turned low, try a different *Target*. For mysterious
reasons sometimes changing it by 1 or 2 ppm improves the situation. If
fluxes are painfully low and nothing speeds up the process, drop the
number of cycles from 3 to 2 (in *New Measurements* menu level 7)

## Downloading soil respiration data

- Connect the RS-232 cable to the right side of the 6400 console and to the serial port of the computer.
- Turn on the 6400 (chamber, soil probe, etc do not need to be attached).
- Select `Soil`
`Chamber` configuration and say `N` to the `Is`chamber/IRGA`
`connected?` question. It will tell you how to connect the IRGAs; press `Enter` \
- Select the `Utility`Menu` (F5) and chose `File`Exchange`
`Mode`. Screen should read `waiting`to`establish`connection` \
- On the computer...FIXME`

## Maintenance

- Keep dust off of everything if possible, especially the tubing and fans. Don't set the chamber down on the ground unless the cap is on.
- Don't let it get wet. If measurements must be made in rain, cover everything - console and chamber - with plastic bags. Remember that a rainstorm is not a good time to make accurate respiration measurements.
- When the Drierite becomes mostly pink it is time to change both canisters of chemicals. The canisters can be unscrewed from the console using the small knobs below the scrub/bypass knobs. Do not empty or fill the canisters through the top - unscrew the bottom cap. Use gloves, don't inhale the dust, put the old stuff in waste containers, etc.`

#### Maintenance Log

* The Li-Cor temperature probe is currently broken. Substitute the omega probe for soil temp measurements.
* Replaced chemical traps (Drierite and Soda-lime) and bought 2 new batteries in July 2010.
* Fixed a leak around the top of the soil respiration collar in July 2012.`
