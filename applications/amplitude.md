# Amplitude

(sar-amplitude)=
## SAR Amplitude
The amplitude component of a SAR acquisition is the amount of the signal sent out by the sensor that returns to be measured, often referred to as radar backscatter. These values represent the conditions of the scatterers on the earth’s surface in that area, and can indicate the degree of surface roughness, structural complexity, and relative moisture content. 

Backscatter values are impacted by changes to the physical structure of the earth’s surface, including processes that alter vegetation or built structures. Because of NISAR’s regular acquisition schedule and insensitivity to cloud cover, data is available at regular intervals all over the world. This makes it very valuable for time-series analysis, which can be used to track short- or long-term changes to natural and anthropogenic features. 

The L-band sensor can penetrate through moderately complex vegetation and more deeply into the soil than C-band SAR sensors such as Sentinel-1. This provides insight into the conditions under the canopy, and at deeper levels in the soil column, and having observations using both wavelengths (and, in some areas, S-band data in addition) increases the ability to understand processes driving change on the landscape.

(nisar-amplitude-datasets)=
## Amplitude Datasets

### GCOV

[Geocoded Covariance (GCOV)](#gcov-product-overview) products are the most accessible amplitude-based NISAR products. The individual covariance layers in the GCOV product have had Radiometric Terrain Correction (RTC) applied. This process uses a DEM to correct for distortions caused by the impacts of terrain on the side-looking acquisitions.

Not only is the output product aligned with the DEM topographically, but radiometric flattening is applied to normalize the radar backscatter based on the surface area contributing to the signal returns. The pixel values represent radar backscatter in gamma-nought power, with a different layer for each polarization. 

The RTC results in products that align well with other imagery and geospatial datasets, and provide more consistent values regardless of the acquisition geometry. For areas with overlapping acquisitions, products from different path may be suitable for use in the same time-series analysis, allowing for denser time series than would be possible using only acquisitions for the same path and frame.

### GSLC

The [Geocoded Single Look Complex (GSLC)](#gslc-product-overview) products are complex valued, including both the amplitude and the phase components of the SAR signal returns. The pixel values are encoded as complex Digital Numbers (DN), but the amplitude values can be [extracted and converted from beta-nought radiometry](#gslc-backscatter) to either gamma-nought or sigma-nought backscatter coefficients if desired. 

The topographic phase (calculated from a DEM) is removed during the generation of the GLSC products. As a result, the amplitude values are terrain-corrected. Unlike the GCOV product, they have not been radiometrically flattened, so should be used in amplitude workflows only if you do not want or need the backscatter values to be normalized to the surface area contributing to the signal returns.

### Pixel Spacing

The pixel spacing of the GSLC products is always 5 meters in the north direction, but can vary from 2.5 to 40 meters in the east direction, depending on the acquisition mode and frequency. In contrast, most of the GCOV products have a cell size of either 10x10 or 20x20 meters for [Frequency A](#nisar-frequencies) layers (which are higher resolution than the Frequency B layers).

While GSLC products can allow users to see features in finer detail than in the corresponding GCOV products, the smaller pixel size (and complex data format) results in products that are _much_ larger than the GCOV files. They are more time-consuming to download, visualize, and analyze than the GCOV products. 

Note also that the cell sizes for GSLC rasters are not always square. While 40 MHz acquisitions are processed to output 5x5 meter pixels for Frequency A GSLC layers, all the other frequencies will have non-square pixels. 


