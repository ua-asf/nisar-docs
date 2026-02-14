---
short_title: Earthdata Search
---
# Finding NISAR Data with Earthdata Search

(earthdata-search-overview)=
## Earthdata Search
[Earthdata Search](https://search.earthdata.nasa.gov/ ) is a web application developed by [NASA'S Earth Science Data and Information System (ESDIS)](https://www.earthdata.nasa.gov/about/esdis) that allows users to search, compare, visualize, and access NASA's Earth science data collections.  

## Using Earthdata Search to Access NISAR Data 

### 1. Filter by data product type
Earthdata Search organizes data by product type (called a "collection" in Earthdata Search). A collection must be selected before doing any additional filtering. 

```{figure} ../assets/earthdata-search-search-bar.png
:label: earthdata-search-search-bar
:alt: Image of the Earthdata Search web interface with the search bar highlighted.
:align: center

Search using the search bar. 
```

To search for a specific product type, input the corresponding short name from @tbl:earthdata-search-shortname-list into the search bar. For a description of NISAR's data product types, see @data-products-overview. 

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

To search for all NISAR data products, use the filter options on the left-hand panel, as shown in @earthdata-search-nisar-filters. Set "Platforms" to `NISAR` and "Processing Level" to the desired product level.  The results will update to display all NISAR product data types that fit the selected criteria. 

```{figure} ../assets/earthdata-search-nisar-filters.png
:label: earthdata-search-nisar-filters
:alt: Screenshot showing the platform and processing level filters in Earthdata Search selected to be NISAR and Level 2 and Level 3, respectively. 
:align: center

Setting the platform filter to NISAR and the processing level to 2 and 3 will show analysis-ready NISAR data products.
```

### 2. Filter for desired products
After selecting a collection, use the available filters to refine the list of products. Individual data products are called "granules" in Earthdata Search.  

To search for a specific geographic region, use the `Spatial Search` button. You can search with a polygon, rectangle, circle, or point by either by drawing on the map or specifying coordinates.  You can also upload a ShapeFile, KML, GeoJSON, or GeoRSS file. 

```{figure} ../assets/earthdata-search-spatial-search.png
:label: earthdata-search-spatial-search
:alt: Screenshot showing a rectangular spatial search of GCOV products. 
:align: center

Search by drawing a region of interest or entering coordinates using the "Spatial" search filter. This example shows a rectangular search, but users can also search using a polygon, circle, point, or geospatial file. 
```

To search for products in a specific date range, use the `Temporal Search` button. This filter searches for products between a start and end date, with the option to find products that occur on an annual basis by checking the "Use a recurring date range" button. 

```{figure} ../assets/earthdata-search-temporal-search.png
:label: earthdata-search-temporal-search
:alt: Screenshot showing the temporal search of GCOV products. 
:align: center

Search using a date range with the "Temporal" search filter. 
```

Use the "Granule ID" filter to perform advanced searches, including wildcard matching and searches for multiple Granule IDs separated by commas. The question mark (?) wildcard matches a single character at the specified position, while the asterisk (*) wildcard matches any number of characters at the specified position. For example, searching for `*_QP*` will return quad-pol acquisitions. To review NISAR product naming conventions and elements, see @naming-convention-overview. 

```{figure} ../assets/earthdata-search-granule-search.png
:label: earthdata-search-granule-search
:alt: Screenshot showing a Granule ID search using `*_QP*` to find quad-pol GCOV products.   
:align: center

Filter using the Granule ID filter set to `*_QP*` to find all quad-pol products. 
```

### 3. Download data

Log in to Earthdata Search using your [Earthdata Login (EDL)](https://urs.earthdata.nasa.gov/) account. To learn more about EDL, see @earthdata-login.

Individual granules can be downloaded directly from the Earthdata Search results. Select the download icon associated with the desired granule to save the file locally.

```{figure} ../assets/earthdata-search-download-GCOV.png
:label: earthdata-search-download-GCOV
:alt: Screenshot showing how to select and download a single GCOV granule.  
:align: center

Log in with EDL credentials by clicking the "Log In" button (#1) on the upper right-hand side of the screen. Once logged in, click the download icon (#2), toggle to "Download Files", and click the download icon next to the filename to download your desired granule directly. 
```

For guidance on downloading multiple files in bulk, refer to the [NASA Earthdata Cloud Cookbook](https://nasa-openscapes.github.io/earthdata-cloud-cookbook/how-tos/find-data/earthdata_search.html). 


For information on accessing data using the AWS CLI, see @s3-paths-earthdata-search.