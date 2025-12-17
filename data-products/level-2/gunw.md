---
short_title: GUNW
---
# Geocoded Unwrapped Interferogram

{button}`Product Specification <https://nisar.asf.earthdatacloud.nasa.gov/NISAR-SAMPLE-DATA/DOCS/NISAR_D-102272_RevE_NASA_SDS_Product_Specification_L2_GUNW_Nov8_2024_w-sigs.pdf>`
{button}`Find Data <https://search.asf.alaska.edu/#/?dataset=NISAR&sciProducts=GUNW>`

The GUNW product is an L2 product derived from the RIFG and RUNW products by geocoding the unwrapped phase and associated data layers (i.e., coherence magnitude, ionospheric phase screen) on a geographical grid at 80 m posting. 

Geocoding is performed using the orbit of the reference RSLC product and a DEM to project the data onto a predefined Universal Transverse Mercator (UTM) or Polar stereographic projection system map grid. The geocoding algorithm uses a bilinear interpolation for interpolating data layers with floating-point data types, Sinc interpolation for the complex wrapped interferogram, and nearest-neighbor interpolation for unsigned integer datasets (e.g., connected components mask). 

The GUNW products also include the wrapped complex interferogram (multi-looked at 30 m in range-Doppler coordinates and geocoded at 20-m posting), the unwrapped interferometric phase in radians (80-m posting), the normalized interferometric coherence magnitude (20-m and 80-m posting), connected components mask, and sub-pixel offset layers obtained from incoherent cross-correlation. If an offset product in range-Doppler coordinates (e.g., ROFF) is available for the processed frame, the sub-pixel offset layers included in GUNW are obtained by optimally blending the multiresolution offset layers included in ROFF. 

The GUNW product also includes an ionospheric phase screen layer from the RUNW product and a layer quantifying its uncertainty. In the case of mode transitions where the continuity of spectral bands is impacted, a split spectrum ionospheric phase estimate is derived from the main imaging band frequencyA. The estimated ionospheric phase screen is included in the product but not applied to the data layers within the GUNW product by default. 

The GUNW product also includes geocoded lookup tables for external phase corrections (e.g., solid Earth tides, hydrostatic and wet tropospheric phases). These phase corrections, when available, are not removed from the interferometric data.
