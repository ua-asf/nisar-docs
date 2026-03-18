# Amplitude

The amplitude component of a SAR acquisition is the amount of the signal sent out by the sensor that returns to be measured, often referred to as radar backscatter. These values represent the conditions of the scatterers on the earth’s surface in that area, and can indicate the degree of surface roughness, structural complexity, and relative moisture content. These values are impacted by changes to the physical structure of the earth’s surface, including processes that alter vegetation or built structures. 

For NISAR data, the [Geocoded Covariance (GCOV)](#gcov-product-overview) are the most accessible amplitude-based products. The individual covariance layers in the GCOV product can be used like Radiometric Terrain Corrected (RTC) products, as the backscatter has been normalized to account for the impacts of terrain. The pixel values represent the intensity of radar backscatter in gamma-nought power, with a different layer for each polarization. <!-- talk about DEM use in the processing workflow -->



The pixel values of [Geocoded Single Look Complex (GSLC)](#gslc-product-overview) products are encoded as complex Digital Numbers (DN), but the amplitude values can be [extracted and converted from beta-nought radiometry](#gslc-backscatter) to either gamma-nought or sigma-nought if desired. For users who do not want radiometrically terrain corrected data, this is an alternative source for amplitude values. 

Because of NISAR’s regular acquisition schedule and insensitivity to cloud cover, data is available at regular intervals all over the world. This makes it very valuable for time-series analysis, which can be used to track short- or long-term changes to natural and anthropogenic features. 

The L-band sensor can penetrate through moderately complex vegetation and more deeply into the soil than C-band SAR sensors such as Sentinel-1. This provides insight into the conditions under the canopy, and at deeper levels in the soil column, and having observations using both wavelengths (and, in some areas, S-band data in addition) increases the ability to understand processes driving change on the landscape.
