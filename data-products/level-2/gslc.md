---
short_title: GSLC
---
# Geocoded Single Look Complex (GSLC)

{button}`Product Specification <https://cumulus.asf.earthdatacloud.nasa.gov/PUBLIC/DATA/NISAR/NISAR_D-102269_RevF_NASA_SDS_Product_Specification_L2_GSLC_w-esigs.pdf>`
{button}`Find Data <https://search.asf.alaska.edu/#/?dataset=NISAR&sciProducts=GSLC>`

(gslc-product-overview)=
## Product Overview

The GSLC product is a Level 2 product derived from the Level-1 [RSLC](#rslc-product-overview) product by geocoding the input RSLC into a map coordinate system such as a UTM Zone or Polar stereographic projection system.

The geocoding is performed by inverse mapping of the map coordinates with their topographic heights into the radar coordinate system and interpolating the radar signal at the radar location corresponding to the map coordinate. Phase-preserving complex interpolation projects the data onto a uniformly spaced, north-south/east-west aligned geographic grid.

(gslc-pixel-spacing)=
## Pixel Spacing

The pixel spacing of the product depends on the acquisition bandwidth used, as indicated in @tbl:gslc-pixel-spacing. 

- Most GSLC [Frequency A](#nisar-frequencies) datasets for acquisitions over land are posted to a pixel spacing of either 5 by 5 meters or 5 by 10 meters.
- Cryosphere acquisitions (Antarctica, Greenland, etc.) are generally posted to a pixel spacing of 5 by 2.5 meters. 
- Acquisitions over sea ice and [Frequency B](#nisar-frequencies) datasets are generally posted to a pixel spacing of 5 by 40 meters. 

:::{table} NISAR GSLC Pixel Spacing by L-Band Acquisition Bandwidth 
:label: tbl:gslc-pixel-spacing

| Range bandwidth (MHz) | RSLC Azimuth sampling (m) | RSLC Range sampling (m) | Ground Range Sampling in mid-Swath (m) | GSLC Posting in Northing (m) | GSLC Posting in Easting (m) |
|:---------------------:|:-------------------------:|:-----------------------:|:--------------------------------------:|:----------------------------:|:---------------------------:|
|           5           |            ~5             |           ~25           |                 ~36.3                  |              5               |             40              |
|          20           |            ~5             |          ~6.25          |                  ~9.1                  |              5               |             10              |
|          40           |            ~5             |          ~3.12          |                  ~4.5                  |              5               |              5              |
|          77           |            ~5             |          ~1.56          |                 ~2.27                  |              5               |             2.5             |

:::

### Interferometry

The phase of the GSLC product is flattened for the orbit used in the RSLC processing. The phase flattening removes the topographic phase contribution in the GSLC. Consequently, cross-multiplying two GSLC products will result in an interferometric phase flattened interferogram.

(gslc-backscatter)=
### Backscatter

Because of the phase flattening applied to the GSLC, the amplitude values are also terrain corrected. No radiometric flattening is applied to normalize the backscatter relative to the area contributing to the returned signal, however. For radiometrically terrain corrected backscatter, refer to the [Geocoded Covariance (GCOV)](#gcov-product-overview) products.

The pixel values in the GSLC product are presented as complex Digital Numbers (DN). To convert these DNs to backscatter values, simply calculate the square of the absolute value of the DN of the desired frequency/polarization data from the GSLC product. The resulting backscatter values are in beta-nought (beta0) radiometry.

$$\text{beta0 backscatter} = |\text{GSLC DN}|^2$$

For users who prefer backscatter values in either gamma-nought (gamma0) or sigma-nought (sigma0) radiometry, Lookup Tables (LUTs) are provided in the GSLC product to help convert the values. The LUTs are found in the `metadata/calibrationInformation/geometry` subgroup of the GSLC products, as illustrated in @gslc_coefficient_luts_image.

```{figure} ../../assets/gslc_coefficient_luts.png
:name: gslc_coefficient_luts_image
:alt: Illustration of where the LUTs are located in the GSLC HDF5 file structure
:align: left
:width: 50%

The LUTs are located in the `metadata` group of a GSLC HDF5 file, under the subgroups `calibrationInformation` -> `geometry`. There are LUTs for beta0 as well as gamma0 and sigma0, but the data is already in beta0 radiometry when converted from the DN, so applying the beta0 LUT is not necessary (the value in the beta0 LUT for each pixel with valid data is 1, so leaves the value unchanged).
```

Once you have calculated beta0 backscatter from the DN, divide it by the square of the values provided in either the sigma0 or gamma0 LUT to output the desired backscatter coefficient. For example:

$$\text{sigma0 backscatter} = {\text{beta0 backscatter} \over (\text{sigma0 LUT})^2}$$

Refer to [this Earthdata Forum post](https://forum.earthdata.nasa.gov/viewtopic.php?f=7&p=25489#p25489) to see code for converting GSLC DN values to a different radar backscatter coefficient.
