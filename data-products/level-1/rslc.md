---
short_title: RSLC
---
# Range Doppler Single Look Complex (RSLC)

{button}`Product Specification <https://nisar.asf.earthdatacloud.nasa.gov/NISAR-SAMPLE-DATA/DOCS/NISAR_D-102268_RevE_NASA_SDS_Product_Specification_L1_RSLC_clean_w-sigs.pdf>`
{button}`Find Data <https://search.asf.alaska.edu/#/?dataset=NISAR&sciProducts=RSLC>`

The RSLC product is in the zero-Doppler radar geometry convention. The output image is on a grid characterized by constant azimuth time interval and one-way slant range spacing, and all the primary image layers for a multi-polarization or multi-frequency product are generated on a common time-slant range grid. The output grid is also characterized by a fixed starting slant range, azimuth time interval, and slant range spacing values for easy interpolation. 

The complex backscatter values of the RSLC are digital numbers (DNs) with secondary layer look-up tables (LUTs) provided to convert to beta-naught, sigma-naught, and gamma-naught radiometry. These radiometric correction LUTs are defined for the ellipsoid, not for the local terrain. 

All standard (i.e., not urgent-response) products are processed using the Medium-fidelity Orbit Ephemeris (MOE) product for forward processing and the Precise Orbit Ephemeris (POE) product for reprocessing campaigns.
