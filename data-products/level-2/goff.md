---
short_title: GOFF
---
# Geocoded Pixel Offsets (GOFF)

{button}`Product Specification <https://nisar.asf.earthdatacloud.nasa.gov/NISAR-SAMPLE-DATA/DOCS/NISAR_D-105010_RevC_NASA_SDS_Product_Specification_L2_GOFF_Nov8_2024_w-sigs.pdf>`
{button}`Find Data <https://search.asf.alaska.edu/#/?dataset=NISAR&sciProducts=GOFF>`

The GOFF product is an L2 product derived from the ROFF product by geocoding the pixel offset layers and associated data layers (i.e., SNR) on a geographical grid at 80 m posting. Geocoding uses the orbit of the reference RSLC product and a DEM to project the data onto a pre-defined UTM or Polar stereographic projection system map grid. The geocoding algorithm uses a bilinear interpolation for interpolating data layers with floating-point data types. 

The GOFF product contains a collection of data layers representing the pixel offset shifts between a pair of coarsely coregistered RSLC granules. The spacing, the window size, and the search radius used to generate the pixel offset layers in the range-Doppler geometry are organized by range bandwidth and area of observation. 

Pixel offset layers are distributed without performing any conventional post-processing operation, i.e., layers might contain offset outliers and are not low pass filtered to reduce noise in the data.
