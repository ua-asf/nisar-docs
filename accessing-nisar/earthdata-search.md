---
short_title: Earthdata Search
---
# Finding NISAR Data with Earthdata Search

{button}`Search for all NISAR Data Products<https://search.earthdata.nasa.gov/search?q=nisar%20beta>`

(earthdata-search-overview)=
## Earthdata Search

[Earthdata Search](https://search.earthdata.nasa.gov/ ) is a web application developed by [NASA'S Earth Science Data and Information System (ESDIS)](https://www.earthdata.nasa.gov/about/esdis) that allows users to search, compare, visualize, and access all of NASA's [Earth Science](https://science.nasa.gov/earth-science/) data. 

Earthdata Search organizes data by product type. Each of these data types is called a "collection". There are more than 10,000 collections available, so you will need to apply filters to return the search results you want. 

## 1. Find NISAR collections

The NISAR mission generates many data product types of varying processing levels, as described in the @data-products-overview. Each one of these product types has its own collection in Earthdata Search. You can search for multiple NISAR collections at once to explore the available data types, or restrict your search to a specific NISAR collection. 

(earthdata-search-bar)=
### Earthdata Search Landing Page

Get started searching for NISAR data quickly by using the search bar on the [Earthdata Search landing page](https://search.earthdata.nasa.gov/). To search for all available NISAR data products, enter `NISAR Beta` into the search bar. 

```{figure} ../assets/earthdata-search-search-bar.png
:label: earthdata-search-search-bar
:alt: Image of the Earthdata Search web interface with the search bar highlighted.
:align: center

Search using the search bar on the Earthdata Search landing page. 
```

To search for a specific product type, input the corresponding short name from @tbl:earthdata-search-shortname-list into the search bar. For ancillary datasets such as orbit ephemeris files, refer to @tbl:earthdata-search-supporting-shortname-list for the short names.

:::{table} NISAR Data Product Short Names
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

:::{table} NISAR Supporting Data Product Short Names
:label: tbl:earthdata-search-supporting-shortname-list

| Product         | Short Name            |
|-----------------|-----------------------|
| DEM for NISAR   | NISAR_DEM             |
| Orbit Ephemeris | NISAR_OE              |

:::

### Filter Panel

If you left the search bar blank when launching your search from the landing page, or want to further refine your search for NISAR collections, you can leverage the panel of filter options on the left side of the Earthdata Search map interface. 

Start by typing `NISAR` into the search bar at the top of the filter panel.

```{figure} ../assets/earthdata-search-nisar-filters.png
:label: earthdata-search-nisar-filters
:alt: Screenshot showing the platform and processing level filters in Earthdata Search selected to be NISAR and Level 2 and Level 3, respectively. 
:align: center

Typing `NISAR` in the **Search Bar** and setting the **Platforms** filter to `NISAR` and the **Processing Level** to include levels `2` and `3` will show analysis-ready NISAR data products.
```

You can also enter more specific keywords into the search bar, but they may not narrow your search completely. For example:
- Entering `NISAR GCOV` returns just the NISAR_L2_GCOV_BETA_V1 collection.
- Entering `NISAR RSLC` returns not only the NISAR_L1_RSLC_BETA_V1 collection, but other NISAR collections that use RSLC products as input during processing.

Beneath the search bar are many filter options organized by category. The categories most useful for refining NISAR search results are [Platforms](#eds-platforms) and [Processing Levels](#eds-processing-levels).

(eds-platforms)=
#### Platforms

In the **Platforms** section of the filter panel, select `Space-based Platforms`, then `Earth Observation Satellites`, then `NISAR`. 

Note the following: 

- If you have not typed `NISAR` into the search bar, NISAR may not be displayed as one of the options in the `Earth Observation Satellites` category. Type `NISAR` into the search bar to make sure that it is displayed in the list of Platforms.

- In preparing for the NISAR mission, there were NISAR-like products generated from data collected by other sensors, including Sentinel-1, ALOS PALSAR, and UAVSAR. These collections may be included in NISAR search results if you do not select only the NISAR sensor from the list of platforms displayed in the panel.

(eds-processing-levels)=
#### Processing Levels

Use the **Processing Levels** section to select the desired [product level](#data-products-overview). 

Keep in mind that the definitions assigned to the various processing levels are different for SAR data than optical imagery. Refer to @tbl:earthdata-search-processing-levels to compare the product level descriptions listed in the Earthdata Search filter panel to the SAR-specific descriptions.

:::{table} Processing Levels for SAR compared to Earthdata Search level descriptions
:label: tbl:earthdata-search-processing-levels
| Level                                      | Earthdata Description                  | SAR Description                       |
|:-------------------------------------------|:---------------------------------------|:--------------------------------------|
| [Level 1](#level-1-range-doppler-products) | Radiance                               | Datasets in Range-Doppler coordinates |
| [Level 1A](#nisar-ancillary-files)         | Radiance                               | Ancillary data files                  |
| [Level 2](#level-2-geocoded-products)      | Geophys. Variables, Sensor Coordinates | Datasets geocoded to a map projection |
| [Level 3](#level-3-geophysical-products)   | Gridded Observations                   | Geophysical products                  |
:::

#### Organizations

You can use the **Organizations** section to select datasets archived by the `Alaska Satellite Facility`.

Setting the Organization filter to `Alaska Satellite Facility` is another way to ensure that `NISAR` is displayed as a platform in the filter panel under `Earth Observation Satellites`. 

## 2. Find specific products

Individual data products are called “granules” in Earthdata Search. Refine your search to identify granules available in a particular location using a [Spatial Filter](#earthdata-search-spatial-filters), or for a specified time range using a [Temporal Filter](#earthdata-search-temporal-filters).

Search results are presented by collection. Once you've applied your filters, click on the desired collection in the search results ([](#earthdata-search-collection-results-a)) to view the granules available for that collection.

While you can apply the same search filters to multiple collections, you need to click on each collection in turn to see the available granules. Return to the list of collections using the **Search Results** link ([](#earthdata-search-collection-results-b)) to view available granules for a different collection.

:::{figure}
:label: earthdata-search-collection-results
:alt: Series of two screenshots illustrating how to view the granules for multiple collections in Earthdata Search results
:class: grid grid-cols-2 gap-4
Explore results for multiple collections.

(earthdata-search-collection-results-a)=
```{figure} ../assets/earthdata-search-collection-results.png
:width: 100%
<div style="text-align: left;">
After applying search filters to multiple collections, click on one of the collections in the search results to see the available granules.
</div>
```

(earthdata-search-collection-results-b)=
```{figure} ../assets/earthdata-search-collection-return.png
:width: 100%
<div style="text-align: left;">
Click on the <b>Search Results</b> link at the top of the window to return to the search results and select a different collection to view its granules.
</div>
```
:::

(earthdata-search-spatial-filters)=
### Spatial Filters

To search for a specific geographic region, use the **Spatial** search menu. You can search with a polygon, rectangle, circle, or point by either by drawing on the map or specifying coordinates.  You can also upload a Shapefile, KML, GeoJSON, or GeoRSS file. 

```{figure} ../assets/earthdata-search-spatial-search.png
:label: earthdata-search-spatial-search
:alt: Screenshot showing a rectangular spatial search of GCOV products. 
:align: center

Search by drawing a region of interest or entering coordinates using the **Spatial** search filter. This example shows a rectangular search, but users can also search using a polygon, circle, point, or geospatial file. 
```

(earthdata-search-temporal-filters)=
### Temporal Filters

To search for products in a specific date range, use the **Temporal** search menu. This filter searches for products between the specified start and end date/time.

```{figure} ../assets/earthdata-search-temporal-search.png
:label: earthdata-search-temporal-search
:alt: Screenshot showing the temporal search of GCOV products. 
:align: center

Search using a date range with the **Temporal** search filter. 
```

To search for products for a specific date range on an annual basis, check the box next to **Use a recurring date range**. You will be prompted for a month/day (and optionally a time) for the start and stop dates, and can select the range of years to include. 

```{figure} ../assets/earthdata-search-temporal-recurring.png
:label: earthdata-search-temporal-recurring
:alt: Screenshot showing a recurring temporal search for GCOV products. 
:align: center

Search for a recurring date range using the **Temporal** search filter. 
```

(earthdata-search-advanced-filters)=
### Advanced Searches

Once you click on a collection to see the available granules, you can apply an advanced search to refine the list of displayed granules using the **Granule Search** filter. 

To search for a list of specific products, enter granule ID names separated by commas.

This filter also supports wildcard searches, allowing you to search for specific elements found within the product filename. To review NISAR product naming conventions and elements, see @naming-convention-overview. 

- The question mark (?) wildcard matches a single character at the specified position
- The asterisk (*) wildcard matches any number of characters at the specified position

For example, searching for `*_QP*` in the `NISAR_L2_GCOV_BETA_V1` collection will restrict your search results to only quad-pol acquisitions. 

```{figure} ../assets/earthdata-search-granule-search.png
:label: earthdata-search-granule-search
:alt: Screenshot showing a Granule ID search using `*_QP*` to find quad-pol GCOV products.   
:align: center

Filter using the Granule ID filter set to `*_QP*` to find all quad-pol products. 
```

## 3. Access desired products

There are two options for accessing NISAR data from your search results. You can either [download](#download-nisar-data-earthdata-search) it, or use direct [AWS S3 Access](#direct-s3-access-in-earthdata) paths to work with the data directly in the cloud. 

(download-nisar-data-earthdata-search)=
### Downloading NISAR Data 

Log in to Earthdata Search using your [Earthdata Login (EDL)](https://urs.earthdata.nasa.gov/) account. To learn more about EDL, see @earthdata-login.

Individual granules can be downloaded directly from the Earthdata Search results. Select the download icon associated with the desired granule to save the file locally.

```{figure} ../assets/earthdata-search-download-GCOV.png
:label: earthdata-search-download-GCOV
:alt: Screenshot showing how to select and download a single GCOV granule.  
:align: center

Log in with EDL credentials by clicking the **Log In** button (#1) on the upper right-hand side of the screen. Once logged in, click the **download icon** (#2), select the **Download Files** tab, and click the **download icon** next to the filename to download your desired granule directly. 
```

For guidance on downloading multiple files in bulk, refer to the [NASA Earthdata Cloud Cookbook](https://nasa-openscapes.github.io/earthdata-cloud-cookbook/how-tos/find-data/earthdata_search.html). 

(direct-s3-access-in-earthdata)=
### Direct AWS S3 Access

Earthdata Search also provides the S3 paths for NISAR data products, allowing users to leverage tools that interact with the data directly in S3 storage. 

Click the **Download** icon for a product, and select the **AWS S3 Access** tab. Click the **copy icon** to copy the S3 path to your clipboard. 

```{figure} ../assets/earthdata-search-copy-GCOV-s3-link.png
:label: earthdata-search-s3-link-GCOV
:alt: Screenshot showing how to retrieve the S3 access path for a single GCOV granule.  
:align: center

Click the **download icon** for an item in your search results, select the **Download Files** tab, and click the **copy icon** next to the filename to copy the S3 path for that granule. 
```

To learn more about using direct AWS S3 Access, refer to @aws-s3-access-overview.
