# Below-snow soil respiration

Wintertime soil CO~2~ fluxes are measured below a snowpack using a
diffusional measuremnt. Gas from the soil-snow interface is collected
through a inlet and tubing system, tranferred into evacuated vials
(Labco Exetainers), and measured for CO~2~ concentrations in the lab
using a Li-Cor 7000 IRGA. Fluxes are then calculated using Fick's law in
conjunction with atmospheric CO~2~ measurements and measured snowpack
characteristics (density, depth, tortuosity).

In use at:

* [Hidden`Canyon](hiddencanyon/hc_ecohydrology:soilresplog_1)

## Gas sampling inlets and installation

Gas from the soil-snow interface is collected in winter and spring using
an inlet and tubing system. 10cm diameter cylindrical inlets covered on
both ends with fine (50μm) mesh are placed on the soil surface in fall.
Each inlet is tubed to a central location where measurement activities
will not disturb the CO~2~ diffusion gradient near the inlet. Tubing is
1/4 inch Eaton Synflex™ tubing. Tubing terminates with a sampling port
fitted with a Swagelok stainless coupling and plug. THe coupling can be
connected to a complementary fitting on the pump/sampling assembly.
Inlets are located in what are intended to be spatially representative
replications in each plot. Each [soil temperature/moisture
profile](hiddencanyon:soilprofiles) currently is associated
with 3 inlets. There are thus 9 inlets each in the control and treatment
plots in the [Hidden Canyon snowpack
manipulation](hiddencanyon:snowmeltdesign).

#### Pump time calculation

Once inlets are installed and ready to be measured, the volume of air
between inlet and the sampling port must be known. This volume must be
pumped out using an electric pump prior to each measurement. After
pumping away this volume, the below-snow air is then sampled with the
pump/sampling assembly. To calculate this volume and the time needed to
pump it away follow this procedure:

- Measure the length of the tubing (//l//) between the inlet and sampling port in centimeters (to the nearest 50cm is ok).
- The tubing has an inner diameter of 1/4 inch, which is 0.635cm (this is //r//).
- The volume of this tubing (//V//)is calculated as: //πr`^`2`^* l//
- The pump claims to pump at 4000ml per minute, but we will reduce this a bit with the pin valve on a flowmeter
- Calculate the time needed to pump out air in the tubing as //V/flowrate//, so if we set the valve to allow 500ml per minute the time needed to pump out the stagnant air in the tubing is //V///500.
- Have these pump times for each inlet calculated before heading into the field to sample.`

## Pump/sampling assembly

A pump/sampling assembly is connected to the 1/4 inch Swage fitting at
the end of each sampling tube and is used to draw sample air to a
sampling port. This assembly consists of a small diaphragm pump (KNF
UNMP50), a Swagelok 1/4 inch gastight valve, a sampling port with septa,
a flowmeter/pinvalve assembly, and a filter. The pump is powered with a
LiCor rechargeable battery. The tubing at the end of the filter is
attached to the sampling tube, and the pump can then be used to draw air
samples from the inlet at a rate monitored and controlled at the
flowmeter/pinvalve. Once a sufficient volume of air has been drawn
through the sample tube to bring inlet air into the pump/sampling
assembly, the valve in front of the pump is closed, the pump powered
down, and a sample is withdrawn through the septa of the sampling port
using a syringe and needle.

FIXME - add photo of this device

## Field procedure for filling exetainers

#### Checklist

- Pump and associated tubing and sampling fittings
- 2 charged Li-Cor batteries
- Flowmeter/mass flow controller
- List of calculated pump times (see above)
- Stopwatch
- Evacuated exetainers (evacuated on Bowling Lab vacuum line prior to departure)
- Luer-lock 20ml+ syringe
- Luer-lock needles (bring spares)
- Sharpie for marking exetainers
- Spare septa
- 5/8 and 9/16 wrenches`

#### Procedure

- Ski to the first set of sampling ports to be sampled (they are in threes).
- Loosen the plug from each sampling port using the wrenches.
- Assemble the syringe and needle, replace the septum on the pump/sampling assembly, and attach the flowmeter (or MFC) to the pump/sampling assembly.
- Remove the plug from the first port and attach to the lower flowmeter inlet.
- Set stopwatch to zero.
- Open pump inlet valve, start pump by attaching Li-Cor battery, and start stopwatch - all at roughly the same time.
- While pump is pumping label the exetainer that you will use to hold the sample.
- When the pumping time is up, shut the pump inlet valve and unplug the battery from the pump.
- Uncap the needle on the syringe and insert it through the septum
- Flush the syringe once or twice
- Fill syringe to the necessary volume - exetainers are 12ml, but fill to at least 15ml at high elevation sites (see site recommendations below).
- Insert needle and empty syringe sample into the labeled exetainer.
- Repeat steps 4-12 for the rest of the ports, them move to the next set and remove again.
- Be sure to collect three atmospheric samples (through the syringe) during the sampling campaign.`

## Measuring the Exetainers

* Exetainers are returned to the lab and measured for CO`~`2`~concentration and δ`^`13`^`CO`~`2`~using a LI-7000 (CO`~`2`~`) open path system, and a tunable diode laser spectrometer (C isotopes).
* See the **protocol** for this [here](procedures:exetainer_CO2).`

## Calculating respiration rates and isotope ratios

Soil respiration rate can be calculated using Fick's law, adjusted for
snowpack properties:

$$ F = \\rho_a \\eta \\tau D \\frac{dC}{dz} $$

where $\\rho_a$ is the molar density of air (adjusted for temperature
and pressure using the Boyle-Charles law, $\\eta$ and $\\tau$ are
the air-filled porosity and tortuosity of the snowpack, respectively ,
$D$ is the molecular diffusivity of CO~2~ in air (adjusted for
temperature and pressure following Massman 1998), and $C$ is the mole
fraction of CO~2~ at height $z$.

FIXME - add isotope ratios?

## Notes for Hidden Canyon Samples

* Fill syringe to 15ml so that exetainers are slightly pressurized before being brought down to a lower elevation (and higher pressure).
* Many of the inlets are plugged, so there may need to be a revision of the install procedure.
* Tubing lengths and pump times for each inlet are located in the HC_inlets spreadsheet.`
