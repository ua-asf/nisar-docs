---
short_title: SME2
---
# Soil Moisture (SME2)

{button}`Product Specification <https://nisar.asf.earthdatacloud.nasa.gov/NISAR-SAMPLE-DATA/DOCS/NISAR_D-107677_RevC_NASA_SDS_Product_Specification_L3_SME2_Nov8_2024_w-sigs.pdf>`
{button}`Find Data <https://search.asf.alaska.edu/#/?dataset=NISAR&sciProducts=SME2>`

(sme2-product-overview)=
## Product Overview

NISAR backscatter observations are used to estimate a global high-resolution soil moisture product at a pixel spacing of 200 m. This product is generated with each new acquisition, and is expected to have a data latency of 72 hours. Products generated for [5+5 MHz acquisitions](#nisar-frequencies) are aggregated to 400 meters, but are still posted to the 200-m EASE-Grid 2.0.

Soil moisture estimates are provided over areas with dense vegetation (VWC greater than 5 kg/m2) and during periods of precipitation, but these values are flagged as potentially unreliable. No soil moisture retrievals are provided for areas with urban build-up, permanent snow and ice cover, or permanent inland waterbodies, and these pixels are flagged appropriately. No soil moisture retrievals are provided over areas with frozen ground or snow on the ground.

The NISAR soil moisture has an accuracy goal of 0.06 m3/m3 over unflagged areas with vegetation water content below 5 kg/m2. 

(sme2-product-maturity-level)=
### Product Maturity Level

Soil moisture products are generated from a time series analysis using Level 2 [GCOV](#gcov-product-overview) products as input. 

:::{warning}Soil Moisture Products Not Fully Calibrated or Validated

The algorithms used to generate SME2 products rely on long time series of GCOV products. Due to insufficient availability of validated GCOV time series data, there is not yet a collection of VALIDATED SME2 products. 

The SME2 products in the PROVISIONAL collection should not be considered fully calibrated. Refer to [PROVISIONAL Known Issues](#provisional-known-issues-sme2) for more information.
:::

The [release of VALIDATED collections in November 2026](#nisar-validated-data-nov) did not include a collection for SME2 products. Because SME2 products are not yet fully validated, pending the availability of longer time series of VALIDATED GCOV products, products generated with CRID P05036<!--[#TODO: Verify CRID number]--> are currently still being added to the [PROVISIONAL SME2 collection](https://www.earthdata.nasa.gov/data/catalog/asf-nisar-l3-sme2-provisional-v1-1). 

To differentiate between products generated with CRID PO5036<!--[#TODO: Verify CRID]--> and the CRID used for the products originally added to the PROVISIONAL collection (P05023), use a wildcard search in either [Earthdata Search](#earthdata-search-advanced-filters) or [Vertex](#vertex-scene-name-patterns) to select only products with the desired CRID. 
