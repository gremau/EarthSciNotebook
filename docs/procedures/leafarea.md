# Leaf Area Index

There are many different methods for measuring and estimating Leaf Area Index. Other vegetation coverage and biomass indices, such as coverage or Plant Area Index are similar to or can be related to LAI. See the [wikipedia page](https://en.wikipedia.org/wiki/Leaf_area_index) for additional details. This is about some fairly easy methods to get at LAI (or similar measures) using digital images.

## Using ImageJ

ImageJ, software created for biological image analysis by NIH ([available here](https://imagej.nih.gov/ij/), can be used to calculate leaf area at several scales if there is sufficient contrast between the leaves/canopy and the background. Below are instructions for calculating plant area index from aerial images, such as those available from Google Earth.

1. Open the aerial photo in ImageJ.
2. Set the scale for the photo.
  - You must have some reference scale on the photo, such as a scale bar or an object of known dimensions.
  - Select the straight line tool and draw a line along the known dimension, which should return a length in pixels.
  - With that line drawn, open "Analyze>Set Scale"
  - The distance in pixels should be populated based on the line you drew, then type in the known distance of this line and the units. Check "Global" and select OK. This should reference the image in feet.
3. If a color photo, make it grayscale with "Image>Type>8bit". There are other options for this, such as splitting the photo into RBG channels and using one channel.
4. Threshold the photo with "Image>Adjust>Threshold" and then adjust the sliders until the vegetation in the photo has been highlighted appropriately. The "Auto" button will try to do this step in a standardized way, which may work.
5. Draw a region of interest on the image now using one of the tools (Rectangular, elliptical, polygon, etc).
6. Measure the area of the ROI using the "Analyze>Measure" tool. If the scale is set correctly this should provide a Results box with the area of the highlighted ROI calculated in the chosen units.
7. Now calculate the area of the vegetation (thresholded areas) using "Analyze>Analyze Particles". In the dialog select "Summarize results". The calculated area of the vegetation particles (in chosen units) will appear in the "Summary" box.
8. Divide the vegetation area by the ROI area to get Leaf/Plant Area Index.

## Hemispherical canopy photography

Hemispherical photos (using a "fisheye" lens) can be used to calculate a number of important values related to and approximating LAI.

See the [Canopy photography page](canopyphotos.md)
