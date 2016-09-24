###### δ13C analysis of soil extracts

A method to measure the δ^13^C value of dissolved organic carbon in soil
extracts (fumigated or unfumigated).

##### Materials

Chemicals
---------

` * H`~`2`~`O`~`2`~` solution (30% Hydrogen peroxide, diluted to 10%)`\
` * FeSO`~`4`~`•7-H`~`2`~`O (Ferrous sulfate heptahydrate)`\
` * 1N H`~`2`~`SO`~`4`~` (Sulfuric acid, stronger acid could be diluted)`\
` * CaCl`~`2`~` or BaCl`~`2`~

Laboratory equipment and consumables
------------------------------------

` * Centrifuge suitable for 15ml tubes`\
` * Balance for weighing chemicals.`\
` * Volumetric flasks for mixing solutions (volume depends on how many samples you are processing).`\
` * 1 5 ml eppendorf centrifuge tube per sample/standard (mixing and precipitation vessel).`\
` * Micropipetter (10-100µl and 100-1000µl instruments both come in handy).`\
` * Pipette tips `\
` * 1 Exetainer for each sample (oxidation vessel).`\
` * 1ml syringe and needles`

##### Liquid oxidation and IRMS analysis

Initial mixing of the extract and reactant solutions takes place in a
5ml eppendorf centrifuge tube. Once reactants are mixed and sulfate is
precipitated out of this solution, it is centrifuged and the supernatant
liquid is measured into a glass exetainer for oxidation. Precipitation
and centrifugation steps could (maybe) be omitted if cryotrapping is
used to purify the CO~2~ prior to IRMS analysis. These are the basic
steps, and the mass/volume of extract or reactant used in each step are
explained below. I also made a spreadsheet that calculates the extract
and reactant amounts for each sample.

` - Add FeSO`~`4`~` solution to centrifuge tube in required amount. (Optional)`\
` - Dilute with 1 ml distilled H`~`2`~`O (optional)`\
` - Measure extract volume with desired amount of dissolved C (currently equivalent to 5µmol C) into centrifuge tube.`\
` - Add enough acid to create a final pH of ~3 with extract and dilution factored in.`\
` - Precipitate SO`~`4`~^`2-`^` using CaCl`~`2`~` or BaCl`~`2`~` (Optional)`\
` - Centrifuge sample to separate extract/reactant solution from sulfate precipitate. (Optional)`\
` - Measure extract/reactant solution (equivalent to 1µmol C) to reaction vial`\
` - Close vial and purge with He gas (Job 14 on PAL)`\
` - Add H`~`2`~`O`~`2`~` or Sodium persulfate reagent.`\
` - Allow oxidation reaction to complete (~4 hours)`\
` - Load into GasBench and analyze resulting CO`~`2`~` by IRMS`

#### Calculate volume of extract

We wish to analyze roughly 1 μmol CO~2~ in the mass spectrometer. TOC/TN
analysis yielded TOC values in mgC/L. To convert:

\$\$ V = \\frac{1}{(TOC \\times \\frac{0.001mg}{g}) \\times
mwC\^{-1}}\$\$

where \$V\$ is the volume in μL of extract to oxidize to yield 1 μmol
CO~2~, \$TOC\$ is the extract C concentration in mg/L, and \$mwC\$ is
the molecular weight of carbon (12.0107). Note that the conversions from
L to μL (/1e6) and mol to μmol(\*1e6) cancel out. This same conversion
should be usable for the C3 and C4 standard solutions.

#### Calculate amount of standard sugar (raw)

Sucrose (C~12~H~22~O~11~) has a formula weight of 342.296. The molecular
weight of the C in sucrose is 144.128 (12 \* 12.0107). So, sucrose is
approximately 42.106% C (144.128/342.296). To measure the isotope ratio
of pure sucrose, weighing 1mg into a tin should do. To calculate the
amount to add to an exetainer for oxidation and IRMS analysis via the
gasbench:

\$\$ M = \\frac{342.296}{1 \\times 10\^6} \\times \\frac{1 mol \\
\\mathrm{sucrose}}{12 mol \\ \\mathrm{C}} \* 1000mg/g = 0.0285mg \$\$

#### Calculate amounts of Fenton's reagent and other reagents to use

We need to oxidize the carbon in the sample as completely as possible.
In the Benatti paper, experimentally determined optimum values are given
for the ratio of the Fenton's reagent components (\[H~2~O~2~\]:\[Fe++\]
= 4.5:1), the ratio of Fenton's reagent to oxidizeable C
(\[H~2~O~2~\]:\[COD\] = 9:1), and reaction pH (4 or less). The highest
\[H~2~O~2~\]:\[COD\] value tested was 9:1, but other literature suggests
that additional H~2~O~2~ will increase the completion of the oxidation
reaction. So, to be safe, we'll use these ratios to start

` * [H`~`2`~`O`~`2`~`]:[Fe++] = 4.5:1`\
` * [H`~`2`~`O`~`2`~`]:[COD] = 12:1, `\
` * pH = 4 (or less)`

For each µmol of sample C, we need at least 12 µmol H~2~O~2~ and 2.6
µmol Fe++ (to get the 4.5:1 ratio).

Remember:

\$\$M\_i V\_i = M\_f V\_f\$\$

Hydrogen peroxide solution
--------------------------

We have a 30% H~2~O~2~ (MW = 34.0147) solution with a density of
1.11g/cm^3^. We want a 10% solution. For every ml of this 10% solution
there is 0.11g H~2~O~2~, or 0.00326 moles (3.3M solution). Adding 300μL
of this will give 978 μmol H~2~O~2~. We hope to have at least 80umol C
in each reaction vial, so this should be sufficient to oxidize that.

` * To make 250ml, dilute 83.33ml of this to 250ml with distilled H`~`2`~`O.`\
` * To make 100ml, dilute 33.33ml of this to 100ml with distilled H`~`2`~`O.`

Persulfate reagent
------------------

Using roughly the recipe in Doyle et al 2004 (50 g K~2~S~2~O~4~ + 16.8 g
NaOH + 30 g H~3~BO~3~ L^-1^), but with sodium persulfate. I adjusted
this to 44 g Na~2~S~2~O~4~ + 18.8 g NaOH L^-1^ to raise the pH a little.

Ferrous sulfate solution
------------------------

We want to have about 217μmol of Fe++ in each reaction vial, as this
will be in a 4.5:1 ratio with the H~2~O~2~ (815umol/4.5) that will be
added. The molecular weight of hydrated ferrous sulfate (FeSO~4~·7H~2~O)
is 382.95478g.

` * To make 250 ml of a 1M solution, dissolve 95.739 g in 250ml of water. This will yield 1000μmol/mL.`\
` * To make 100ml of a 1M solution, dissolve 38.295 g in 100ml water. Again, this yields 1000umol/ml.`

Acid to lower the pH
--------------------

We want a low pH (2-4) before adding the H~2~O~2~. We can use this
equation to calculate the amount of acid to use:

\$\$M\_1V\_1 + M\_2V\_2 = M\_3(V\_1 + V\_2)\$\$

where \$M\_1\$ is the molarity of the acid, \$V\_1\$ is the volume of
the acidic solution, \$M\_2\$ is the molarity of the water, \$V\_2\$ is
the volume of the water, and \$M\_3\$ is the target molarity of the end
solution. Converting this equation to solve for \$V\_1\$ yields the
following equation:

\$\$V\_1 = \\frac{(M\_3V\_2 - M\_2V\_2)}{(M\_1 - M\_3)}\$\$

Or if we know the volume to be added but want to calculate its
molarity...

\$\$M\_2 = -\\frac{M\_1V\_1 - M\_3(V\_1 + V\_2)}{V\_2}\$\$

Ca/Ba precipitation solutions
-----------------------------

We also need to precipitate all the sulfate out of our solution prior to
oxidizing (adding the peroxide). We are adding one mole + 10% extra of
Ca or Ba ions for each mole of sulfate in the solution.

The molecular weight of calcium chloride (CaCl~2~·2H~2~O) is 147.014g.

` * To make 250 ml of a 2M solution, dissolve 73.507 g in 250ml of water. This will yield 2umol/uL. `\
` * Could also do 3M solution: 44.1042g in 100ml`

The molecular weight of barium chloride (BaCl~2~·2H~2~O) is 244.28g.

` * To make 250 ml of a 2M solution, dissolve 127.64 g in 250ml of water. This will yield 2umol/uL.`

##### Notes about running these at SIRFER

` - Use the `*`CO2_injection.seq`*` sequence on Saltbush Bill instrument.`\
` - Rename the job in the spreadsheet that pops up, select that line, click Save and then Start.`\
` - In the dialoge that appears, rename the job (as above), copy this name to file export, and erase the "Acquisition" field from the export.`\
` - Inject samples - 0.3ml for the 10% CO2 tank, 1ml for the samples. Seems like peaks above 800mV are best`\
` - Turn on 30 seconds of CO2 wall gas after the last peak has been acquisitioned (top bar in Conflo interface).`\
` - Stop the acquisition`

##### Sugar Standards

We are using C3 and C4 sucrose (C~12~H~22~O~11~, table sugar) as a
standard to test IRMS analysis of the extracts. The molecular weight of
sucrose is 342.3, and 42.1% of this is C. To measure the isotope ratios
of these sugars, we weighed 1 mg of sucrose (which contains 0.4mg of C)
into tins and measured them with EA-IRMS analysis. We found that these
C3 and C4 sugars have -24.5 and -11.5 per mil isotope ratios,
respectively.

\^Getting the right amount of C from Sucrose\^\^\^\^ | CO~2~ production
| 1 μmol C | = 12 μg C | = 28.6 μg Sucrose | | EA-IRMS | 35.1 μmol C | =
420 μg C | = 1000 μg Sucrose |

#### Materials needed

` * K`~`2`~`SO`~`4`~\
` * Sugar from C3 plants (beet sugar)`\
` * Sugar from C4 plants (cane sugar)`\
` * 500 ml & 50 ml volumetric flasks`\
` * Weigh paper`\
` * Labeling tape`

#### Procedure

` - Determine expected concentrations to create a test range. For the Niwot-FEF soils, see `[`here`](niwot_girdling:soilanalysis)`.`\
`   - Using similar data gathered by Nicole Trahan we determined a rough range of concentrations of carbon that might be present in our soil samples, and that we would want to test with the sugar standards. Nicole had concentrations ranging from 200-2500 micrograms of carbon per gram of soil. Our extracts have 5 grams of soil per 25 milliliters, so the desired test range we calculated for our soil was 40 – 500 micrograms of carbon per milliliter of extract. We divided the range into five, and included a low value to come up with the test concentrations of 20, 40, 150, 270, 380, and 500 micrograms of carbon.`\
` - Make 1 L of a 0.5 M K`~`2`~`SO`~`4`~` solution`\
` - Add 500 ml of DI water to a 500 ml volumetric flask `\
` - Weigh out ~ 43.564g of K2SO4 and add to flask`\
` - Mix using a stir plate`\
` - Repeat for a total of 1 Liter of solution`\
`   - Exact values used: 43.5643g and 43.5646g`\
` - Weigh out sugar`

Micrograms of Carbon Per Milliliter

20 40 150 270 380 500 mg sucrose/ 50ml 2.37 4.75 17.81 32.06 45.13 59.38
actual suc c3 mg/50ml 2.34 4.73 17.84 32.2 45.05 59.32 actual suc c4
mg/50ml 2.42 4.71 17.88 32.07 45.09 59.26 mg C/ 50ml 1 2 7.5 13.5 19 25
actual C c3 mg/50ml 0.98514 1.99133 7.51064 13.5562 18.96605 24.97372
actual C c4 mg/50 ml 1.01882 1.98291 7.52748 13.50147 18.98289 24.94846

Add sugar to 50 ml of potassium sulfate solution There should be a total
of 12, 50 ml potassium sulfate solutions each with a distinct
concentration of either c3 or c4 sugar Evaporate solutions in drying
oven

##### References

` * Benatti, C. T., C. R. G. Tavares, and T. A. Guedes (2006), Optimization of Fenton’s oxidation of chemical laboratory wastewaters using the response surface methodology, Journal of Environmental Management, 80(1), 66–74, `[`doi:10.1016/j.jenvman.2005.08.014`](doi:10.1016/j.jenvman.2005.08.014)`.`\
` * Benatti, C. T., C. R. G. Tavares, and E. Lenzi (2009), Sulfate removal from waste chemicals by precipitation, Journal of Environmental Management, 90(1), 504–511, `[`doi:10.1016/j.jenvman.2007.12.006`](doi:10.1016/j.jenvman.2007.12.006)`.`
