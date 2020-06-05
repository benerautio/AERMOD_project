AERPLOT.exe
------------
(version 16216)

AERPLOT uses a .PLT (plot) file from AERMOD to create a .KMZ (Google
Earth) file with receptors plotted and colored according to their
concentration.  Source locations and source shapes can optionally be
plotted.  Contours and/or gradient lines can also be added to the plot
if desired.  Program options are controlled with the inputfile
AERPLOT.inp .

Installation: 
-------------

This program is designed to run on Microsoft Windows. It is provided 
as a stand-alone executable and no installation is required. 

Operation:
----------

1. The executable looks for the AERPLOT.inp file in the local
   directory and that file should be placed in the folder with the
   program executable. The .PLT file may be local or in another
   directory, as specified in the AERPLOT.inp file.

2. Alter the input file, AERPLOT.inp, as necessary. Comments in the
   provided sample .inp file explain the program options and are given
   below. The .inp file uses semicolons (;) to indicate comment
   lines. Blank lines are allowed. Comment characters should be in the
   first column only.

3. Invoke the AERPLOT.exe program, either from the command line, or
   by clicking in Windows Explorer.

3. The program will output a file, with a file name set by the parameter
   OutputFileNameBase, and a file extension of .KMZ .

   The .KMZ file is self-contained. It can be moved to another folder,
   or mailed to another computer, and still be viewed in an earth 
   browser (e.g., Google Earth). 


Resulting Display:
------------------

When opened in Google Earth, each receptor will be be displayed as 
a colored circle. At the time of this release, Google Earth will 
display the circles centered on the given coordinates.

Each receptor is colored according to its concentration.  Red 
indicates the highest concentration, with dark blue the lowest 
concentration. (An alternate set of icons that run from dark red 
to dark green is available, selectable from within the AERPLOT.inp 
file.)

If contours are selected, the contour lines will also be displayed
and the color scale will match the color scale of the receptors.

A legend will be displayed indicating the color scale corresponding 
to the concentration at each receptor.

If gradients are selected, a separate legend will be displayed
indicating the color scale corresponding to the gradient lines.

Clicking on a receptor will open an "information balloon" that has 
all of the associated data from the .PLT file.

Each receptor is named according to the concentration, the X and 
the Y coordinates, plus a leading sequence number. For example, 

           "8_60.54069_87.50000_151.55445", 

Sources are displayed if requested. The location, type, etc., are
determined from the plot's original aermod.inp file.

AERPLOT.inp parameters:
------------------------

For information about the parameters, see the supplied sample
AERPLOT.inp file.

"version=2"

The "version" parameter is required and must be the first parameter 
and SHOULD be 2.


"altitudeChoice=relativeToGround"
or 
"altitudeChoice=absolute"

Receptors can be plotted at a specific height level above or
below sea level, or relative to the ground.


"altitude=0"

The altitude can be offset from the height indicated in the .PLT file.


"easting=0"
"northing=0"
"utmZone=16"

The program converts UTM coordinates into latitude and longitude
for display in Google Earth. Thus, if the input coordinates are not
in UTM, additional adjustments are required, as described below. 
Also note that UTM coordinates require the UTM "zone" to be set
in AERPLOT.inp.   

Three options for the model grid coordinate system:

1) X and Y are relative coordinates in meters: the UTM coordinates in 
AERPLOT.inp should be set to the "zero origin" of that coordinate 
system to show the plot in the right location within the browser.  

2) X and Y parameters are absolute UTM coordinates: coordinates 
in AERPLOT.inp should be set to zero.

3) X and Y are not relative to a real grographic location: UTM 
coordinates in AERPLOT.inp can be used to select a neutral 
background (e.g., a glacier field) for easy display. 


"NameDisplayedInGoogleEarth=vrd_an_b_15_v1_2010"

The name that will be displayed in Google Earth for the dataset. 


"PlotFileName=vrd_an_b_15_v1_2010.plt"

The input file name.


"OutputFileNameBase=vrd_an_b_15_v1_2010"

The output file name is built by appending a suffix and/or a file extension.


"binningChoice=Log"

The user has the choice between a "Linear" or "Log" color scale. 

"sIconSetChoice=redBlue"
or
"sIconSetChoice=redGreen"
"IconScale = 0.70"

The color scheme for the concentration scale and the size of the 
icons in Google Earth. The suggested icon scale default is 0.7. 

"minbin=DATA"
"maxbin=DATA"


The program will automatically pick the maximum and minimum 
values for the color scale (keyword "DATA"). However, these
parameters can be used to manually set either the maximum 
or minimum or both.

"sDisableEarthBrowser= True"

This parameter controls whether the program will 
automatically launch Google Earth after processing the 
.PLT file ("TRUE") or not ("FALSE"). 

"makeContours                       = False"
"numberOfTimesToSmoothContourSurface= 1"
"numberOfGridCols                   = 400"
"numberOfGridRows                   = 400"

The parameter 'makeContours' enables ("TRUE") or disables 
("FASLE") contours.

Normally, the 'numberOfTimesToSmoothContourSurface=' parameter
should be set to one. One smoothing can make the contours   
much less chaotic, while a second one can move the contours farther
from their proper locations according to the receptor values. However,
a setting greater than one may be beneficial when there is greater 
spacing between receptors.

For particularly large model domains, the "numberOfGridCols" and 
"numberOfGridRows" may need to be increased beyond the default 
values of 400. 

Note: although these last three parameters are not frequently 
used, they are required to be present.


Additional notes:
----------------

The current version of AERPLOT assumes that the .PLT file includes all 
header information that is included by default in AERMOD. Without the 
header, AERPLOT will not be able to read in the .PLT file.
