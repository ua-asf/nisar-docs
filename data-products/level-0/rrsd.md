---
short_title: RRSD
---
# Radar Raw Signal Data (RRSD)

{button}`Product Specification <https://nisar.asf.earthdatacloud.nasa.gov/NISAR-SAMPLE-DATA/DOCS/NISAR_D-102267_RevE_NASA_SDS_Product_Specification_L0B_RRSD_CRSD_Nov8_2024_w-sigs.pdf>`
{button}`Find Data <https://search.asf.alaska.edu/#/?dataset=NISAR&sciProducts=L0B>`

L0B RRSD is the Level 0 product available to the science disciplines from the DAAC. The RRSD product comprises time-sorted unpacked recordings of raw radar echo pulses and related radar instrument telemetry. It is comparable to the Level-0 raw data products delivered by SAR sensors worldwide (e.g., L1.0 by ESA and JAXA). The RRSD data is focused to a Radar Single Look Complex (RSLC) product before use in higher-level processing. 

A single RRSD product granule consists of radar echoes acquired in the same imaging mode. An observation constitutes all consecutive radar echoes acquired in the same imaging mode. The radar echoes are organized in sub-groups by imaging frequency (A or B), transmit polarization (H, V, L, or R), and receive polarization (H or V) in that order. 

The radar echoes of any given frequency and polarization combination are decoded and aligned to adjust for different sampling window start times and can be accessed as a simple two-dimensional raster image. The RRSD product also contains all the instrument telemetry for the entire data take, including the observation.
