# Earthdata Search

(earthdata-search-overview)=
## Overview
 <!-- TODO: Add in summary overview -->

## Using Earthdata Search to Access NISAR Data 

### 1. Go to https://search.earthdata.nasa.gov/ and log in using your Earthdata credentials
* Create an account 

### 2. Search for NISAR data products

:::{table} NISAR Data Product Earthdata Search Short Name List
:label: tbl:earthdata-search-shortname-list

| Product | Short Name            |
|---------|-----------------------|
| SME2    | NISAR_L3_SME2_BETA_V1 |
| GCOV    | NISAR_L2_GCOV_BETA_V1 |
| GUNW    | NISAR_L2_GUNW_BETA_V1 |
| GOFF    | NISAR_L2_GOFF_BETA_V1 |
| GSLC    | NISAR_L2_GSLC_BETA_V1 |
| RUNW    | NISAR_L1_RUNW_BETA_V1 |
| RIFG    | NISAR_L1_RIFG_BETA_V1 |
| ROFF    | NISAR_L1_ROFF_BETA_V1 |
| RSLC    | NISAR_L1_RSLC_BETA_V1 |

:::

```{figure} ../assets/earthdata-search-nisar-filters.png
:label: earthdata-search-nisar-filters
:alt: Screenshot showing the platform and processing level filters in Earthdata Search selected to be NISAR and Level 2 and Level 3, respectively. 
:align: center

Setting the platform filter to NISAR and the processing level to 2 and 3 will filter to show analysis-ready NISAR data products.
```

### 3. Download data

```{figure} ../assets/earthdata-search-download-GCOV.png
:label: earthdata-search-download-GCOV
:alt: Screenshot showing how to select and download a single GCOV granule.  
:align: center

Click the download icon, toggle to "Download Files", and click the download icon next to the filename to download your desired granule directly. 
```

To learn more about downloading multiple files at once, visit the [NASA Earthdata Cloud Cookbook](https://nasa-openscapes.github.io/earthdata-cloud-cookbook/how-tos/find-data/earthdata_search.html). 