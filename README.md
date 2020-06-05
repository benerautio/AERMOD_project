## AERMOD_project
This run of AERMOD simulates a point source on a drilling site in Broomfield from 19/3/1 TO 19/8/1
This is an example run to get familiar with the various pre-processors and basic options.

Receptors are configured on a polar grid with the origin on the point source. There are 3 rings of receptors, a 250m, 500m, 
and 750 m radius circle, with a receptor every 10 degrees. There is a total of 108 receptors. 

Pollutant: CH4

Upper Air data used for this model comes from Denver Airport. 
Hourly Surface Data comes from Akron Airport.

# IMPORTANT
Although the output of this project is already in AERMOD\AERMOD.out, if you want to run all of the preprocessors and the model again, you must download the Geotiff files since they couldn't be put in this repo due to their size.

NED for AERMAP:
https://prd-tnm.s3.amazonaws.com/StagedProducts/Elevation/13/TIFF/n40w106/USGS_13_n40w106.tif
Download this Geotiff file, decompress with GDAL, rename it gdal_uncompress.tif, and put it in AERMAP\NED

NLCD for AERSURFACE:
ftp://newftp.epa.gov/Air/aqmg/nlcd/2016/2016_R08_CO-UT.zip

Download this NLCD, unzip, and put all of the tiff files in AERSURFACE\2016_R08_CO-UT

