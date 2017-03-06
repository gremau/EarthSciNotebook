# Century Soil Model

The [CENTURY model](https://www.nrel.colostate.edu/projects/century/) is an ecosystem model used to simulate carbon and nutrient dynamics (N, S, P) for different types of ecosystems including grasslands, agricultural lands, forests and savannas. 

The manual for the model is [here](https://www.nrel.colostate.edu/projects/century/MANUAL/html_manual/man96.html). Be sure to see the [manual addendum](http://www.nrel.colostate.edu/projects/century/MANUAL/html_manual/man96.html#ADDENDUM), [tutorial](http://www.nrel.colostate.edu/projects/century/century_tutorial.pdf), and [parameterization workbook](http://www.nrel.colostate.edu/projects/century/CENTURY%20Parameterization%20Workbook.pdf) also.

**Miscellaneous links:**

* [Simple slideshow](http://slideplayer.com/slide/4060115/)
* [DAYCENT (daily timestep version)](http://www.nrel.colostate.edu/projects/daycent-home.html)
* [Version 5 of Century](https://www.nrel.colostate.edu/projects/century5/_)
* A gridded model product [has been created](https://daac.ornl.gov/MODELS/guides/century_vemap.html)

## Basic steps for a Century simulation

1. Download the model and build the components in the CENTURY, EVENT100, FILE100, and LIST100 subdirectories (using `make`, see README files in each subdir)

2. Create a simulation folder that contains the appropriate files. Basically this will include the century, list100, file100, and event100 executables and all the parameter files. See README's and manual for a complete list of files.

3. Parameterize the model for your site.  There are twelve data files that store these parameters that are used by Century during a simulation. These files can be created and updated using the FILE100 program. The most important is the `<site>.100` file that is specific to your site.
    * Note that I cannot get the `file100` executable to work on my linux system unless it is within the original FILE100 directories (so parameter files must be moved there for editing, or edited with text editor)

4. Establish the simulation time and schedule events to occur using the EVENT100 program. This will create a .sch file that can be used to run a simulation

5. Run the model with `century -s <schedule.file> -n <binary.output.file>`

6. Model will output a binary file that should be converted to ascii with LIST100 program. Run `list100`, choose options, then the [output variables](http://www.nrel.colostate.edu/projects/century/MANUAL/html_manual/man96.html#OUT_VARS) you want to print in the new file.

6. Evaluate the output.

## Useful papers

Parton, William J., Melannie Hartman, Dennis Ojima, and David Schimel. 1998. “DAYCENT and Its Land Surface Submodel: Description and Testing.” Global and Planetary Change 19 (1): 35–48. [link](http://dx.doi.org/10.1016/S0921-8181(98)00040-X)

Parton, W. J., David S. Schimel, C. V. Cole, and D. S. Ojima. 1987. “Analysis of Factors Controlling Soil Organic Matter Levels in Great Plains Grasslands.” Soil Science Society of America Journal 51 (5): 1173–1179.[link](http://dx.doi.org/10.2136/sssaj1987.03615995005100050015x)

Parton, W. J., D. S. Ojima, C. V. Cole, and D. S. Schimel. "A general model for soil organic matter dynamics: sensitivity to litter chemistry, texture and management." SSSA special publication (USA) (1994).[link](https://dl.sciencesocieties.org/publications/books/abstracts/sssaspecialpubl/quantitativemod/169/preview)

Burke, Ingrid C., C. M. Yonker, W. J. Parton, C. V. Cole, D. S. Schimel, and K. Flach. 1989. “Texture, Climate, and Cultivation Effects on Soil Organic Matter Content in US Grassland Soils.” Soil Science Society of America Journal 53 (3): 800–805. [link](http://dx.doi.org/10.2136/sssaj1989.03615995005300030029x)

