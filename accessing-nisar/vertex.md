---
short_title: Vertex Data Search
---

# Finding NISAR Data with Vertex Data Search

(vertex-overview)=
# Vertex Data Search

[Vertex](https://search.asf.alaska.edu/#/) was developed by ASF to facilitate search and discovery for NASA's SAR datasets. Refer to the [Vertex User Manual](https://docs.asf.alaska.edu/vertex/manual/) for more guidance on search capabilities. 

## Using Vertex to Access NISAR Data

To search for NISAR datasets specifically, select `NISAR` from the **Dataset** menu. 

```{figure} ../assets/vertex-dataset-selection.png
:label: vertex-dataset-selection
:alt: Image depicting the option to select "NISAR" from the "Datset" options. 
:align: center

Click on the "Dataset" button and select "NISAR" to search for NISAR products. 
```

Toggle on drawing mode to draw a region of interest to search for products that lie within that area. The left-most "Area of Interest" button offers selection between a point, line, polygon, box, circle, or by uploading a geospatial file. 
```{figure} ../assets/vertex-geographic-search.png
:label: vertex-geographic-search
:alt: Screenshot of Vertex highlighting the "Geographic Search" option to draw a region of interest to search for products. 
:align: center

Using the "Geographic Search" type, toggle into drawing mode to draw a region of interest to search for NISAR products. 
```

Click the **Filters** button to expose additional parameters that can be used to narrow your search. 
Select a date range by entering a start and end date to search. Toggling on "Seasonal Search" allows to search for products produced annually within an overall date range.  

```{figure} ../assets/vertex-date-filters.png
:label: vertex-date-filters
:alt: Screenshot displaying the date filters option.
:align: center

The option to filter by date pops up after clicking on "Filters"
```

Because search parameters of interest for SAR differ from other types of Earth observation data, it can be helpful to use a platform that is tailored to the parameters and characteristics of SAR data. This is particularly useful for those who are less familiar with SAR data products and may need more guidance to find the appropriate dataset for their use case. 

Select the products you wish to search for by navigating to the product filter section. 
Organized by product level
For a list and descriptions of NISAR products, see @data-products-overview. 
Product configuration is either production, urgent response, or custom configuration.  Production product configurations are acquired on a normal schedule, while urgent response products are acquired after a natural disaster or major event occurs. 

:::{table} Product Filters for NISAR Products
:label: tbl:vertex-product-filters

| Product Filter        | Description                                                                   |
|-----------------------|-------------------------------------------------------------------------------|
| Science Product       | Specific product type, grouped by product level. Multiple selections allowed. |
| Product Configuration | Specific processing pipelines. Multiple selections allowed.                   |

:::

Refining down to different observational strategies, such as polarization, direction, instrument, frame coverage, and range bandwidth. 
For information about these strategies, see @nisar-instrumentation. 
Note that S-band data are available through [ISRO's Bhoonidhi](https://bhoonidhi.nrsc.gov.in/bhoonidhi/home.html).

:::{table} Observational Filters for NISAR Products
:label: tbl:vertex-observational-filters

| Observational Filter   | Description                                             |
|------------------------|---------------------------------------------------------|
| Main Band Polarization | Frequency A polarizations. Multiple selections allowed. |
| Side Band Polarization | Frequency B polarizations. Multiple selections allowed. |
| Direction              | Orbit direction (ascending, descending).                |
| Instrument             | Currently, only L-Band SAR available.                   |
| Frame Coverage         | Full or Partial frame coverage.                         |
| Range Bandwidth        | Range bandwidth in MHz. Multiple selections allowed.    |
| Joint Observation Only | Toggle on for simultaneous L- and S-Band acquisitions.  |

:::

### Downloading files via Vertex

Data are free and available to download through Vertex. Once the desired scene is selected, click on the shopping cart icon in the scene listed. This will add the scene to your Downloads, which is the shopping cart icon on the top right hand of the screen. 
```{figure} ../assets/vertex-add-to-downloads.png
:label: vertex-add-to-downloads
:alt: Screenshot highlight the download button next to desired product and the "Downloads" icon that will dispaly file options. 
:align: center

Add files from desired granules to the Downloads cart by clicking the shopping cart button to add scene files to downloads.
```

The Download queue will have eight files added per selected scene. For majority of users, only the `hdf5` file is necessary to download. Click the download icon next to the HDF5 file name to save to your local workspace. 

```{figure} ../assets/vertex-download-files.png
:label: vertex-download-files
:alt: Screenshot of the list of products for a single GCOV product. 
:align: center

All product files associated with a GCOV product. The HDF5 file is the most useable file and can be downloaded directly by clicking the download icon, circled in red.  
```