---
short_title: Vertex 
---

# Finding NISAR Data with Vertex

(vertex-overview)=
## Vertex
[Vertex](https://search.asf.alaska.edu/#/?dataset=NISAR&prodConfig=PR) is ASF's web-based method to search for NISAR data products. Because search parameters for SAR differ from other types of Earth observation data, it can be helpful to use a platform that is tailored specifically for SAR data. This is useful for those who are less familiar with SAR data products and may need more guidance to find the appropriate data products for their use case. 

## Using Vertex to Access NISAR Data

### 1. Search for NISAR data
Navigate to [Vertex](https://search.asf.alaska.edu/#/?dataset=NISAR&prodConfig=PR) and set the **Search Type** to `Geographic Search` and select `NISAR` from the **Dataset** menu. Press **Search** to explore search results. 

```{figure} ../assets/vertex-dataset-selection.png
:label: vertex-dataset-selection
:alt: Image depicting the option to select "NISAR" from the "Datset" options. 
:align: center

Click on the "Dataset" button and select "NISAR" to search for NISAR products. 
```

### 2. Filter for desired products

To search for a specific geographic region, click on the left-most **Area of Interest** button to choose to draw a point, line, polygon, box, circle, or to upload a geospatial file. Toggle on drawing mode to draw a region of interest, then press **Search** to update the search for the new region of interest.

```{figure} ../assets/vertex-geographic-search.png
:label: vertex-geographic-search
:alt: Screenshot of Vertex highlighting the "Geographic Search" option to draw a region of interest to search for products. 
:align: center

Choose a shape and draw an area of interest for a geographic search. 
```

To search for products in a specific date range, open the **Filters** panel and specify a start and end date to define the search range. 

```{figure} ../assets/vertex-date-filters.png
:label: vertex-date-filters
:alt: Screenshot displaying the date filters option.
:align: center

The option to filter by date pops up after clicking on "Filters"
```

NISAR-specific filters are available to more precisely search for NISAR data products. Refer to the [Vertex Getting Started User Guide](https://docs.asf.alaska.edu/vertex/manual/#product-filters) for a comprehensive list of filters and search options. 

```{figure} ../assets/vertex-nisar-filters.png
:label: vertex-nisar-filters
:alt: Screenshot displaying the NISAR-specific filters in Vertex. 
:align: center

NISAR-specific filters in Vertex.
```

**Product Filters** are listed in @tbl:vertex-product-filters. Science Products are organized by product level, and multiple selections are allowed. For a complete list of NISAR products, including detailed descriptions and specifications, refer to @data-products-overview.

:::{table} Product Filters for NISAR Products
:label: tbl:vertex-product-filters

| Product Filters       | Description                                                                   |
|-----------------------|-------------------------------------------------------------------------------|
| Science Product       | Specific product type, grouped by product level. Multiple selections allowed. |
| Product Configuration | Specific processing pipelines. Multiple selections allowed.                   |

:::

**Observational Filters** allow users to refine search results by polarization, direction, instrument, frame coverage, and/or range bandwidth, as described in @tbl:vertex-observational-filters. For information about NISAR bands, frequencies, and polarization, see @nisar-instrumentation. Note that only L-band data are available through Vertex. S-band data are provided through [ISRO's Bhoonidhi](https://bhoonidhi.nrsc.gov.in/bhoonidhi/home.html).

:::{table} Observational Filters for NISAR Products
:label: tbl:vertex-observational-filters

| Observational Filters  | Description                                             |
|------------------------|---------------------------------------------------------|
| Main Band Polarization | Frequency A polarizations. Multiple selections allowed. |
| Side Band Polarization | Frequency B polarizations. Multiple selections allowed. |
| Direction              | Orbit direction (ascending, descending).                |
| Instrument             | Currently, only L-Band SAR available.                   |
| Frame Coverage         | Full or Partial frame coverage.                         |
| Range Bandwidth        | Range bandwidth in MHz. Multiple selections allowed.    |
| Joint Observation Only | Toggle on for simultaneous L- and S-Band acquisitions.  |

:::

Users can also search by **Track and Frame**. Note that "Track" is also known as "Path" or "Relative Orbit" for other satellite missions, such as Sentinel-1. Searching for a specific track and frame will return scenes that align consistently over a specific area. The NISAR track-frame map for available NISAR data is available on the [NISAR Mission website](https://science.nasa.gov/mission/nisar/data/). 

### 3. Download data

Data are free and available to download through Vertex. Once the desired scene is selected, a list of files will appear on the right-hand side of the screen (or below the scene details on a narrow browser window). The HDF5 file, listed first, contains the science data and imagery. To learn more about HDF5 files, see @hdf5. 

Click the download icon next to the HDF5 file name to save to your computer. You will be prompted to sign in with your [Earthdata Login (EDL)](https://urs.earthdata.nasa.gov/) account if you have not already. For more information about EDL accounts, see @earthdata-login. 

```{figure} ../assets/vertex-download-files.png
:label: vertex-download-files
:alt: Screenshot of the list of files for a single GCOV product. 
:align: center

All product files associated with a GCOV product. The HDF5 file, listed first, contains the science data and imagery, and can be downloaded directly by clicking the download icon, circled in red.  
```