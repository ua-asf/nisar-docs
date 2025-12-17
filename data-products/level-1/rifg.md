---
short_title: RIFG
---
# Range Doppler Wrapped Interferogram (RIFG)

{button}`Product Specification <https://nisar.asf.earthdatacloud.nasa.gov/NISAR-SAMPLE-DATA/DOCS/NISAR_D-102270_RevD_NASA_SDS_Product_Specification_L1_RIFG_w-sigs.pdf>`
{button}`Find Data <https://search.asf.alaska.edu/#/?dataset=NISAR&sciProducts=RIFG>`

The RIFG product represents the ellipsoid and topography flattened wrapped interferogram generated from two L1 range-Doppler Single Look Complex (RSLC) products in the range-Doppler geometry of the earlier reference acquisition. The WGS84 ellipsoid is used as the reference surface for flat earth correction. 

The RIFG product contains a binary raster layer of complex numbers representing the wrapped interferometric phase difference in radians, i.e., the wrapped interferogram. The product also contains a binary raster layer of floating-point numbers representing the normalized interferometric correlation, i.e., the interferometric coherence magnitude. 

The wrapped interferogram and the interferometric coherence magnitude are multi-looked to a nominal posting of 30 m on the ground. No ionospheric phase screen correction layers are available with this product. 

The interferometric workflow producing RIFG products coregisters a pair of RSLC products using a DEM and the best available orbit ephemeris. This coregistration is refined using incoherent cross-correlation on the pair of coarsely coregistered RSLCs. 

The RIFG product includes the slant range and along-track sub-pixel offsets obtained from incoherent cross-correlation and used to generate the complex wrapped interferogram. If an offset product in range-Doppler coordinates (e.g., ROFF) is available for the processed frame, the sub-pixel offset layers included in RIFG are obtained by optimally blending the multiresolution offset layers included in ROFF.
