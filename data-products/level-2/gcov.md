---
short_title: GCOV
---
# Geocoded Polarimetric Covariance (GCOV)

{button}`Product Specification <https://nisar.asf.earthdatacloud.nasa.gov/NISAR-SAMPLE-DATA/DOCS/NISAR_D-102274_RevE_NASA_SDS_Product_Specification_L2_GCOV_Nov8_2024_w-sigs.pdf>`
{button}`Find Data <https://search.asf.alaska.edu/#/?dataset=NISAR&sciProducts=GCOV>`

## Product Overview

Geocoded Polarimetric Covariance (GCOV) products provide calibrated backscatter measurements corrected for both radiometric and terrain distortions. For users familiar with SAR amplitude products, these data can be used like Normalized Radar Backscatter (NRB) or Radiometrically Terrain-Corrected (RTC) products.

Due to the side-looking nature of NISAR, topography can significantly affect the magnitude of backscatter, with areas facing the sensor becoming artificially “brighter” (i.e., increased backscatter) and areas away from the sensor turning “darker” (i.e., decreased backscatter) in the images, which biases covariance measurements. To mitigate the effect of topography, an area-based RTC is applied to the covariance terms, normalizing the backscatter. The reference digital elevation model (DEM) for processing and RTC is based on the [Copernicus 30-m and 90-m DEM](https://dataspace.copernicus.eu/explore-data/data-collections/copernicus-contributing-missions/collections-description/COP-DEM).  These normalized terms are then geocoded to the output grid using area-based adaptive multi-looking.

Download-ready GCOV products are projected to their appropriate UTM zone and have a pixel spacing of 10 or 20 meters, depending on acquisition location. Each product includes a covariance variable for each polarization available from acquisition.

## Product Specification

A complete description of NISAR GCOV products is available in @l2_gcov_product_specs2025.

## Data Layers

A GCOV data product includes the following raster data sets. Complete descriptions of these data layers are available in @l2_gcov_product_specs2025 [Section 4.3].

### Geocoded Polarimetric Covariance Terms

`/science/LSAR/GCOV/grids/frequency[A|B]/HHHH` \
`/science/LSAR/GCOV/grids/frequency[A|B]/HVHV` \
`/science/LSAR/GCOV/grids/frequency[A|B]/HHHV` \
`/science/LSAR/GCOV/grids/frequency[A|B]/HHVH` \
`/science/LSAR/GCOV/grids/frequency[A|B]/HHVV` \
`/science/LSAR/GCOV/grids/frequency[A|B]/HVVH` \
`/science/LSAR/GCOV/grids/frequency[A|B]/HVVV` \
`/science/LSAR/GCOV/grids/frequency[A|B]/VVVV` \
`/science/LSAR/GCOV/grids/frequency[A|B]/VHVH` \
`/science/LSAR/GCOV/grids/frequency[A|B]/VHVV` \
`/science/LSAR/GCOV/grids/frequency[A|B]/RHRH` \
`/science/LSAR/GCOV/grids/frequency[A|B]/RVRV` \
`/science/LSAR/GCOV/grids/frequency[A|B]/RHRV`

The primary data elements of the GCOV product are the images of the geocoded polarimetric covariance terms. Visit @nisarPolarimetry to learn more about NISAR polarimetry.

The diagonal terms (HHHH, HVHV, VVVV, VHVH, RHRH, RVRV) are real-valued and describe the intensity of the radar backscatter for the given polarization.

The remaining terms (HHHV, HHVH, HHVV, HVVH, HVVV, VHVV, RHRV) are complex-valued and describe the intensity and phase between different polarization.

Which frequencies and polarizations are available in a particular GCOV data product will vary based on the acquisition mode of the satellite used to collect the data.

### Number of Looks

`/science/LSAR/GCOV/grids/frequency[A|B]/numberOfLooks`

The GCOV terms are obtained from the geocoding of the RSLC product polarimetric covariance terms using an adaptive area-based multi-looking algorithm. The multi-looking window and number of averaged looks vary with the topography and radar geometry. The number of looks layer provides the number of looks used for computing each GCOV term sample. 

### Mask

`/science/LSAR/GCOV/grids/frequency[A|B]/mask`

The mask layer provides information about the averaging ensemble of radar samples that originated the GCOV terms through adaptive multi-looking.

### Radiometric Terrain Correction Gamma-to-Sigma Factor

`/science/LSAR/GCOV/grids/frequency[A|B]/rtcGammaToSigmaFactor`

The RTC Gamma-to-Sigma factor provides factors to normalize the backscatter normalization convention of the GCOV matrix from gamma0 to sigma0.

## Naming Convention

NISAR GCOV product names will conform to the following naming convention:

{term}`NISAR`\_{term}`I`{term}`L`\_{term}`PT`\_{term}`PROD`\_{term}`CYL`\_{term}`REL`\_{term}`P`\_{term}`FRM`\_{term}`MODE`\_{term}`POLE`\_{term}`S`\_{term}`StartDateTime`\_{term}`EndDateTime`\_{term}`CRID`\_{term}`A`\_{term}`C`\_{term}`LOC`\_{term}`CTR`.{term}`EXT`

:::{glossary}
NISAR
: 5 char for mission: NISAR

I
: 1 char for Instrument: L for L-SAR, S for S-SAR

L
: 1 char for Level: 1 or 2 or 3

PT
: 2 char for Processing Type:
    - PR: Production
    - UR: Urgent Response
    - OD: Science On-Demand

PROD
: 4 chars for Product Identifier: GCOV

CYL
: 3 chars for CycLe number in the mission, each cycle represents 12 days, zero padded, starting at 001.

REL
: 3 chars for RELative orbit track number within a cycle, resets to 1 with a cycle number increment, zero padded.Valid values: 001-173.

P
: 1 char for direction of movement of the satellite at the time of imaging
    - A for Ascending
    - D for Descending

FRM
: 3 chars for track frame number, a segment of an orbital track corresponding to theproduct, zero padded Valid Values: 001-176 on each track.

MODE
: 4 chars for Bandwidth Mode Code of Primary and Secondary Bands:
    - 40, 20, 77, 05, or 00 (only if the secondary band is missing)

POLE
: 4 chars for Polarization of the data for the primary and secondary bands. Each band uses a two character code among the following:
    - SH = HH – Single Polarity (H transmit and receive)
    - SV = VV – Single Polarity (V transmit and receive)
    - DH = HH/HV – Dual Polarity (H transmit)
    - DV = VV/VH – Dual Polarity (V transmit)
    - CL= LH/LV – Compact Polarity (Left transmit)
    - CR = RH/RV – Compact Polarity (Right transmit)
    - QP = HH/HV/VV/VH – Quad Polarity
    - NA if band does not exist
    For example, a “quasi-quad” polarization mode would be noted DHDV while a “quasidual” polarization mode would be noted SHSV.

S
: 1 char for source of data for the product
    - A = Acquired source of the observation, single mode
    - M = Mixed source of observations, mixed mode

StartDateTime
: 15 chars for Radar Start Time of the data processed as zero Doppler contained in the file as YYYYMMDDTHHMMSS, UTC

EndDateTime
: 15 chars for Radar End Time of the data processed as zero Doppler contained in the file as YYYYMMDDTHHMMSS, UTC

CRID
: 6 chars for Composite Release Identifier
    - Format of EPMMmm.

A
: 1 char for Product Accuracy or Fidelity of the Orbit Ephermis and Radar Pointing:
    - P, M, N, or F.

C
: 1 char as Coverage Indicator: F for Full or P for Partial.

LOC
: 1 char to represent the location of the Science Data System. J for JPL,vrecommends N for NRSC.

CTR
: 3 chars for Product Counter (zero padded).

EXT
: 1 to n chars for Extension: h5, met, log
:::

## Finding Data

GCOV products can be found in Vertex by setting the Dataset filter to "NISAR" and the Science Product filter to "GCOV (Geocoded Polarimetric Covariance)":
[Find Data in Vertex](https://search.asf.alaska.edu/#/?dataset=NISAR&sciProducts=GCOV)

GCOV products can be found in Earthdata Search by searching for "NISAR_L2_GCOV_": [Find Data in Earthdata Search](https://search.earthdata.nasa.gov/search?q=nisar_l2_gcov_&ac=true)
