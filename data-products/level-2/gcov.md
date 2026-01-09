---
short_title: GCOV
---
# Geocoded Polarimetric Covariance (GCOV)

{button}`Product Specification <https://nisar.asf.earthdatacloud.nasa.gov/NISAR-SAMPLE-DATA/DOCS/NISAR_D-102274_RevE_NASA_SDS_Product_Specification_L2_GCOV_Nov8_2024_w-sigs.pdf>`
{button}`Find Data <https://search.asf.alaska.edu/#/?dataset=NISAR&sciProducts=GCOV>`

(gcov-product-overview)=
## Product Overview

Geocoded Polarimetric Covariance (GCOV) products provide calibrated backscatter measurements corrected for both radiometric and terrain distortions, presented as gamma-0 power values. For users familiar with other corrected SAR amplitude products, these data can be used like Normalized Radar Backscatter (NRB) or Radiometrically Terrain Corrected (RTC) products.

Due to the side-looking nature of NISAR, topography can significantly affect the magnitude of backscatter, with areas facing the sensor becoming artificially “brighter” (returning higher backscatter) than expected, which biases covariance measurements. To mitigate the effect of topography, an area-based RTC is applied to the covariance terms, normalizing the backscatter. The reference digital elevation model (DEM) for processing and RTC is based on the [Copernicus 30-m and 90-m DEM](https://dataspace.copernicus.eu/explore-data/data-collections/copernicus-contributing-missions/collections-description/COP-DEM). These normalized terms are then geocoded to the output grid using area-based adaptive multi-looking.

GCOV products are projected to the appropriate UTM zone for their location and have a pixel spacing of 10 or 20 meters, depending on the acquisition location. They can be used directly in geospatial analysis platforms and workflows. Each product includes a covariance variable for each polarization available from the acquisition.

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

The diagonal terms shown in @gcov-matrix (HHHH, HVHV, VVVV, VHVH, RHRH, RVRV) are real-valued and describe the intensity of the radar backscatter for the given polarization.

The remaining terms shown in @gcov-matrix (HHHV, HHVH, HHVV, HVVH, HVVV, VHVV, RHRV) are complex-valued and describe the intensity and phase between different polarizations. These off-diagonal terms are only included for quad-pol data acquisitions. Users who require off-diagonal values for dual-pol acquisitions will need to generate these layers manually from [GSLC](#gslc-product-overview) products. <!-- TODO: Link to the OSL notebook once it's available: There are [workflows available](link to OSL notebook or other reference) for generating off-diagonal terms for dual-pol acquisitions from [GSLC](#gslc-product-overview) products if you need these values for your application.-->

The frequencies and polarizations available in a particular GCOV data product will vary based on the acquisition mode used to collect the data.

```{figure} ../../assets/nisar-gcov.png
:label: gcov-matrix
:alt: Diagram of the GCOV polarizations
:align: left

Matrix of the possible polarizations available in NISAR GCOV products. Products provided for any of the combinations on the diagonal (highlighted in dark grey) are formatted with real-valued float values, while any of the products provided from above the diagonal (highlighted in light grey) are formatted with complex values.

```

### Number of Looks

`/science/LSAR/GCOV/grids/frequency[A|B]/numberOfLooks`

The GCOV terms are obtained from the geocoding of the RSLC product polarimetric covariance terms using an adaptive area-based multi-looking algorithm. The multi-looking window and number of averaged looks vary with the topography and radar geometry. 

The number of looks layer provides the number of looks used for computing each GCOV term sample. 

### Mask

`/science/LSAR/GCOV/grids/frequency[A|B]/mask`

The mask layer provides information about the averaging ensemble of radar samples that originated the GCOV terms through adaptive multi-looking.

### Radiometric Terrain Correction Gamma-to-Sigma Factor

`/science/LSAR/GCOV/grids/frequency[A|B]/rtcGammaToSigmaFactor`

The RTC Gamma-to-Sigma factor provides factors to normalize the backscatter normalization convention of the GCOV matrix from gamma0 to sigma0.

## Naming Convention

NISAR GCOV product names will conform to the following naming convention: 

{term}`NISAR`\_{term}`I`{term}`L`\_{term}`PT`\_{term}`PROD`\_{term}`CYL`\_{term}`REL`\_{term}`P`\_{term}`FRM`\_{term}`MODE`\_{term}`POLE`\_{term}`S`\_{term}`StartDateTime`\_{term}`EndDateTime`\_{term}`CRID`\_{term}`A`\_{term}`C`\_{term}`LOC`\_{term}`CTR`.{term}`EXT`

Hover over a term listed above to see its description, or click on a specific segment to skip to its description below. Refer to @naming_convention_single_data in the [Naming Conventions](../naming-conventions#products-generated-from-a-single-acquisition) section to see a diagram.

:::{glossary}
NISAR
: 5 characters for the _Mission_
    - **NISAR**

I
: 1 character for the _Instrument_ used for the acquisition
    - **L**: L-band SAR
    - **S**: S-band SAR

L
: 1 character for the product processing _Level_ (1/2/3)
    - GCOV products are Level **2**

PT
: 2 characters for the _Processing Type_
    - **PR**: Production
    - **UR**: Urgent Response
    - **OD**: Science On-Demand

PROD
: 4 characters for the _PRODuct Identifier_
    - **GCOV**

CYL
: 3 characters for the _CYcLe_ number in the mission
    - each cycle represents 12 days
    - zero padded
    - starting at 001

REL
: 3 characters for the _RELative_ orbit track number within a cycle
    - resets to 1 with a cycle number increment
    - zero padded
    - valid values: 001-173

P
: 1 character for the _Orbit Direction_ (direction of movement of the satellite at the time of imaging)
    - **A**: Ascending
    - **D**: Descending

FRM
: 3 characters for the track _FRaMe_ number
    - a segment of an orbital track corresponding to the product
    - zero padded 
    - valid values: 001-176 on each track

MODE
: 4 characters for the _Bandwidth MODE Code_ of the Primary and Secondary Bands
    - first two characters for primary band, last two for secondary band
    - Possible values: 40, 20, 77, 05, or 00 
        - 00 only used if the secondary band is missing

POLE
: 4 characters for the _Polarization_ of the data for the primary and secondary bands respectively. Each band uses a two character code among the following:
    - **SH** = HH – Single Polarity (H transmit and receive)
    - **SV** = VV – Single Polarity (V transmit and receive)
    - **DH** = HH/HV – Dual Polarity (H transmit)
    - **DV** = VV/VH – Dual Polarity (V transmit)
    - **CL**= LH/LV – Compact Polarity (Left transmit)
    - **CR** = RH/RV – Compact Polarity (Right transmit)
    - **QP** = HH/HV/VV/VH – Quad Polarity
    - **NA** if band does not exist
: For example: 
    - a single-pol H-primary polarization mode would be SHSH
    - a dual-pol V-primary polarization mode would be DVDV
    - a “quasi-quad” polarization mode would be noted DHDV
    - a “quasi-dual” polarization mode would be noted SHSV

S
: 1 character for the _Source_ of data for the product
    - **A**: Acquired source of the observation, single mode
    - **M**: Mixed source of observations, mixed mode

StartDateTime
: 15 chars for Radar _Start Date/Time_ of the data processed as zero Doppler 
    - Format: YYYYMMDD**T**HHMMSS, UTC

EndDateTime
: 15 chars for Radar _End Date/Time_ of the data processed as zero Doppler
    - Format: YYYYMMDD**T**HHMMSS, UTC

CRID
: 6 characters for the _Composite Release IDentifier_
    - indicates the version of the workflow used to process the data, incorporating a number of software and project versions
    - Format of EPMMmm
    - MMmm indicates the major and minor version numbers

A
: 1 character for the Product _Accuracy_ or Fidelity of the Orbit Ephemeris and Radar Pointing:
    - **P**: Precise
    - **M**: Medium
    - **N**: Near Real-Time
    - **F**: Forecast

C
: 1 character indicating _Coverage_ of the frame
    - **F**: Full
    - **P**: Partial

LOC
: 1 character to represent the _Location_ of the Science Data System
    - **J**: JPL

CTR
: 3 characters for product _CounTeR_
    - zero padded

EXT
: 1 to n characters for _Extension_ 
    - **h5**
    - **met**
    - **log**
:::

## Finding Data

GCOV products can be found in Vertex by setting the Dataset filter to "NISAR" and the Science Product filter to "GCOV (Geocoded Polarimetric Covariance)":
[Find Data in Vertex](https://search.asf.alaska.edu/#/?dataset=NISAR&sciProducts=GCOV)

GCOV products can be found in Earthdata Search by searching for "NISAR_L2_GCOV_": [Find Data in Earthdata Search](https://search.earthdata.nasa.gov/search?q=nisar_l2_gcov_&ac=true)
