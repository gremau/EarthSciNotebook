# Hemispherical canopy photos

Hemispherical photos can be used to calculate a number of important
parameters about a forest canopy: canopy area, canopy radiation
transmission, leaf area index (with adjustments), and other information.
Here are our field and data analysis procedures.

## Field procedure

### Equipment checklist

* Sigma EX 8mm/F3.5 Fisheye lens
* Canon Digital SLR camera body with EX lens mount
  * MUST have a full frame (35mm) sensor - The APS-C sensor in most dlsr cameras have a smaller field of view and crop photos from the lens above.
  * We are renting a Canon EOS 5d Mark II camera
* Tripod capable of being leveled, or a leveling device.
* A compass
* Marker to place directly north of the camera (ski pole, probe, etc)

### Procedure

- Select photo location and set up tripod and camera so that lens is at 1m above ground level.
- Using a compass place a North marker a few meters due north(magnetic) of the camera.
- Orient the top of the camera so that the top of the photo will be at magnetic north (the marker will appear here in the photo).
- Level the camera using a carpenter's level or the inclinometer of the compass.
- Check the north orientation one more time, duck, remove lens cap, and take photo

## Photo analysis software (GLA)

Here is the gap light analyzer (GLA) software (and helpful manual):

<http://www.rem.sfu.ca/forestry/publications/downloads/gaplightanalyzer.htm>

## Configuration for GLA

Configurations specifying the camera/lens used, the site where they were
taken, and parameters used to model incoming radiation, are stored in a
file called a //.scn// file. These can be loaded for multiple photos.
The settings used for Hidden Canyon are shown below as an example.

- The top of the photos that I take are referenced to magnetic North and need to be adjusted with the appropriate declination. Calculate this at [this NGDC site](http://www.ngdc.noaa.gov/geomag-web/#declination).
- Lens projection is Polar (azimuthal equidistant) for Sigma lenses.
- Topographic mask: This is a vector of azimuth and zenith angles that masks the horizon line if there are ridglines, mountains, etc that block the sun at the photographic location for part of the day. These can be generated with a GIS, or with the provided software. They can be saved in a //.msk// file for use with multiple photos. Currently I just pick a photo and fuss with the array values until it looks right.

~~~ 
--- IMAGE --- Initial Cursor Point: 11.88 degrees. # Declination
Projection Distortion: Polar # For sigma lens

--- SITE --- Latitude: 40:367 North Longitude: 111:342 West Elevation:
2890 Slope: 21 # Measured Aspect: 200 # Measured Topographic Mask: Yes
# Created in the configuration interface

--- RESOLUTION --- Solar Time Step: 2 mins Growing Season Start: 4:15 #
Beginning of growing season for seasonal calculations. Growing Season
End: 10:31 # End of growing season for seasonal calculations. Azimuth
Regions: 36 Zenith Regions: 9

--- RADIATION --- Data Source: Modelled Solar Constant: 1367 Output
Units: Mols m-2 d-1 Cloudiness Index (kt): 0.5 BeamFraction: 0.5
SpectralFraction: 0.5 Sky Brightness Dist.: UOC Model Clear-Sky Trans.:
0.65
~~~

## Procedure for photo analysis in GLA

### 1. Classify an image(register, mask, and threshold)

- Create or load the appropriate configuration file (//.scn// file) for your photos.
- If necessary, load a //.msk// file or create a topographic mask and save it to the configuration. This mask can created or edited by changing azimuth and zenith angles within GLA, or (somehow) with a GIS.
  - This mask can be saved with the //.scn// file, and thus automatically loaded each time that configuration is used. 
- Open a hemispherical photo into GLA.
- Register the photo by marking the top (North) of the photo, and dragging the cursor to the bottom (south) of the photo, taking care to create a circle that squarely encompasses the extent of the fisheye photo.
  - The registration coordinates can be saved and applied to subsequent photos.
- After registering the photo, windows with "Registered" and "Working" versions of the photo will be shown. Apply the overlays of the sky region grid and the topographic mask to the "Registered" photo to make sure the mask looks good.
- For photos taken under a clear sky, it is wise to select the blue color plane before applying a threshold. It removes some glare and lens flare and improves the contrast between vegetation and sky. This change, and the threshold will appear in the "Working" image.
  - Once registered, the"Working" photo's properties, such as contrast, color depth, brightness, etc., can be modified using the menu system. These options may help improve the threshold process in the next step.
- Apply a threshold to the photo and inspect photo using the zoom tool. If the threshold tool did a good job, vegetation and sky are accurately represented by black and white.
- If the threshold looks good, calculate canopy structure and/or transmitted gap light. There are also several modeling routines that can calculate other aspects of canopy transmission.

### 2. Compute results

Once the configuration, registering, and threshold of the image is
complete, the calculations for the image can be made. There are 2
options for this, the first calculates only canopy structure (6
parameters), and the second calculates canopy structure plus transmitted
gap light calculations (about 15 more parameters). Once the calculations
are complete, the calculations can be appended to a table. **Do not
forget to append data for each image to the table!** There is also an
option to save detailed data for each sky region to a text file.

 **Some interesting calculations:**

* **Sky Area** is the percent area of the sky hemisphere found above the effective horizon. If the effective horizon is at 90o (i.e., no topographic mask), then % Sky Area will equal 100 percent. However, if the effective horizon is less than 90o, then the area of visible sky will be less than 100 percent.
* **Mask Area** is the percent area of the sky hemisphere that is obstructed by the surrounding topography.
* **Canopy Openness** is the percentage of open sky seen from beneath a forest canopy. This measure is computed from the hemispherical photograph only, and does not take into account the influence of the surrounding topography.
* **Site Openness** is the percentage of open sky seen from beneath a forest canopy given the additional influence of an effective horizon that is less than 90o (topographic shading)
* **Trans Direct** is the amount of direct solar radiation transmitted by the canopy and topographic mask (if one has been defined).
* **Trans Diffuse** is the amount of diffuse solar radiation transmitted by the canopy and topographic mask (if one has been defined).
* Trans Total is the sum of Trans Direct and Trans Diffuse.
* **% Trans Direct** is the ratio of Trans Direct to Above Direct Mask multiplied by 100%.
* **% Trans Diffuse** is the ratio of Trans Diffuse to Above Diffuse Mask multiplied by 100%.
* **% Trans Total** is the ratio of Trans Total to Above Total Mask multiplied by 100%.

After calculating and saving these values you can move on to the next
image, OR...

### 3. Compute other things

There are a few options, including detailed information for each sky
region (values above for every sky region), a solar intensity model for
the site, percent transmittance for each solar zenith value, etc.
