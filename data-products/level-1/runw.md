---
short_title: RUNW
---
# Range Doppler Unwrapped Interferogram (RUNW)

{button}`Product Specification <https://nisar.asf.earthdatacloud.nasa.gov/NISAR-SAMPLE-DATA/DOCS/NISAR_D-102271_RevE_NASA_SDS_Product_Specification_L1_RUNW_Nov8_2024_w-sigs.pdf>`
{button}`Find Data <https://search.asf.alaska.edu/#/?dataset=NISAR&sciProducts=RUNW>`

The RUNW product represents the unwrapped, ellipsoid- and topography-flattened, multi-looked interferogram generated from two L1 Range Doppler Single Look Complex (RSLC) products in the earlier reference acquisition range-Doppler geometry. The RUNW product has a nominal posting of 80 meters on the ground, irrespective of the slant range bandwidth. 

The product contains raster layers representing single precision floating point unwrapped and normalized interferometric coherence magnitude. The product includes the connected component mask, a mask layer identifying invalid pixels (i.e., pixels affected by geometric distortions), and the slant range and along-track offsets obtained from incoherent cross-correlation. Look-up tables for parallel and perpendicular baseline components are also included. 

The RUNW product also contains an ionospheric phase screen layer and a layer quantifying its uncertainty. Where possible, the ionospheric phase screen is estimated from the two spectral bands frequencyA and frequencyB. In the case of mode transitions where the continuity of spectral bands is impacted, a split spectrum ionospheric phase estimate and an estimate of its standard deviation are derived from the main imaging band frequencyA. The estimated ionospheric phase screen is included in the product but not applied to the data layers within RUNW by default. 

The RUNW product includes the slant range and along-track sub-pixel offsets obtained from incoherent cross-correlation and used to generate the complex wrapped interferogram. If an offset product in range-Doppler coordinates (e.g., ROFF) is available for the processed frame, the sub-pixel offset layers included in RUNW are obtained by optimally blending the multiresolution offset layers included in ROFF.
