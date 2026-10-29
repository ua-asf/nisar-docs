# Harmony

(harmony-overview)=
## Harmony Services for NISAR

[Harmony](https://www.earthdata.nasa.gov/data/tools/nasa-harmony) is Earthdata's data transformation service for customizing NASA datasets. It is seamlessly integrated into the [Earthdata Search](#earthdata-search-overview) platform, but users can also leverage the [Harmony APIs](https://harmony.earthdata.nasa.gov/docs) or the [Harmony-py](https://github.com/nasa/harmony-py) Python library to interact with the data programmatically. 

ASF and the Harmony team developed options for NISAR customization, with services that [extracts individual datasets](#harmony-supported-products-extract), spatially subset, and reproject NISAR HDF5 products and export them as GeoTIFFs. 

Refer to the @tools-services-roadmap to see the development plan for additional Harmony services supporting NISAR.

(harmony-supported-products-extract)=
### Dataset Customization Service

Users can use Harmony to customize NISAR products for the following products: 

- Geocoded Polarimetric Covariance ([GCOV](#gcov-product-overview))
- Geocoded Unwrapped Interferogram ([GUNW](#gunw-product-overview))
- Geocoded Pixel Offsets ([GOFF](#goff-product-overview))
- Soil Moisture ([SME2](#sme2-product-overview))

#### Spatial Subsetting
This service subsets two-dimensional datasets to the spatial filter used in Earthdata Search. Note that option is only enabled when using the [Spatial Filter](#earthdata-search-spatial-filters). 

(harmony-variable-subsetting)=
#### Variable Subsetting
This service extracts two-dimensional datasets from the `/science/LSAR/$product-type/grids/` group as stand-alone GeoTIFFs. This is particularly useful for those users only interested in one or two layers in a product. 

Because the HDF5 files are more compressed, users interested in several layers will be better served by [downloading the full HD5 file](#download-nisar-data-earthdata-search), as they are more efficient to download than extracted GeoTIFF files.

#### Output Projection Selection
This service reprojects output files to the selected EPSG code. Supported projections include Geographic (EPSG:4326), Antarctic Polar Stereographic (EPSG:), NSIDC Sea Ice Polar Stereographic North (EPSG:), and UTM Zone North (EPSG:32601-EPSG:32660) and UTM Zone South (EPSG:32701-32760) projections. For more information on supported NISAR projects, see @nisar-l2-projections.

(harmony-extract-datasets)=
## Customize Downloads in Earthdata Search

Harmony services are available directly in [Earthdata Search](#earthdata-search-overview), which is a map-based web browser interface for data search and access. This makes it easy to find NISAR products for your area and time period of interest and extract just the datasets of interest from the HDF5 file. Each selected dataset is output as a GeoTIFF file.

1. Search for one of the [supported product types](#harmony-supported-products-extract) in [Earthdata Search](#earthdata-search-overview) and [select the desired collection](#find-nisar-collections). If looking to spatially subset NISAR products, make sure to [use Spatial Filters](#earthdata-search-spatial-filters) and filter to your desired AOI.  

    ```{figure} ../assets/harmony-search-gcov.png
    :label: harmony-search-gcov-image
    :alt: Screenshot of searching for a GCOV product in Earthdata Search
    :align: center
    :class: framed
    
    Search for [supported product type](#harmony-supported-products-extract) collections in [Earthdata Search](#earthdata-search-overview) and select the desired collection.
    ```

2. Add one or more granules to a project by clicking the green ＋ icon for each item of interest.

    ```{figure} ../assets/harmony-add-to-project.png
    :label: harmony-add-to-project-image
    :alt: Screenshot of adding an item to a project in Earthdata Search
    :align: center
    :class: framed
    
    Click the green ＋ icon for a granule of interest to add it to your project.
    ```

3. Click the **My Project** button to view the list of granules you've added. 

   - You will need to log in with your [Earthdata Login](#earthdata-login) credentials if you have not already done so. 

    ```{figure} ../assets/harmony-open-project.png
    :label: harmony-open-project-image
    :alt: Screenshot of opening the My Project pane in Earthdata Search
    :align: center
    :class: framed
    
    Click the **My Project** button to view the list of granules you've added.
    ```

4. Select the **Customize Download** option to select the customization options that suit your needs.
   
    ```{figure} ../assets/harmony-customize-download.png
    :label: harmony-customize-download-image
    :alt: Screenshot of selecting the option to customize download and clicking the Edit Variables button
    :align: center
    :class: framed
    
    Select the **Customize Download** option and select your desired customization options. 
    ```
   
If you are subsetting variables, expand the HDF5 group structure by clicking on the directory icons to see their contents.Then, select the individual datasets to extract. 

- When using the [Variable Subsetting customization](#harmony-variable-subsetting), note that not all products will contain all the listed variables. This list includes all possible variables that _may_ be present in a product of that type. As long as at least one of the selected datasets is available in the product, the Harmony job will run. 
   - GeoTIFFs will be generated for any selected variables that are present in the granule, and any datasets that are not present will be ignored.
   - If you do not see a download link for a variable you selected, refer to the file [naming convention](#naming-convention-overview) to determine which polarizations and frequencies would be expected for that product.

    ```{figure} ../assets/harmony-select-variables.png
    :label: harmony-select-variables-image
    :alt: Screenshot of selecting the datasets to extract from a NISAR HDF5 file
    :align: center
    :class: framed
    
    Expand the directory structure and select the datasets to be extracted to GeoTIFF format.
    ```
- If you add datasets for multiple collections to the same project, each collection will be listed in the left panel. You can switch collections by clicking the **Edit Options** link for the desired collection.

    ```{figure} ../assets/harmony-multiple-collections.png
    :label: harmony-multiple-collections-image
    :alt: Screenshot of accessing the download options for each collection when multiple collections are added to the same project
    :align: center
    :class: framed
      
    When multiple collections are included in the project, click the **Edit Options** link for each collection to set the variables to extract.
    ```

5. Once customization options are defined, press the **Download Data** button to submit your data for processing.

    ```{figure} ../assets/harmony-download-data.png
    :label: harmony-multiple-collections-image
    :alt: Screenshot highlighting the **Download Data** button
    :align: center
    :class: framed
      
    Click the **Download Data** button to submit your data for processing.
    ```
If multiple collections are included in the Project, you will need to define the download options for each one. You can either: 
   - Click the **Edit Options** link for each collection, as illustrated in @harmony-multiple-collections-image.
   - Click the **Back to Edit Options** link at the top of the panel once you have made your variable selections and click the **Next** button to progress through each collection. 

        ```{figure} ../assets/harmony-multiple-edit.png
        :label: harmony-multiple-edit-image
        :alt: Screenshot of using the Next button to access the download options for each collection when multiple collections are added to the same project
        :align: center
        :class: framed
      
        To set download options when multiple collections are included in the project, click the **Next** button at the bottom of the Edit Options panel to move to the next collection.
        ```

   - The **Download Data** button will launch the Harmony jobs for all collections in the project that have customization options defined. 
   
6. Harmony will process your request and indicate its progress on the status page. You may need to refresh the status page to see updated progress.

    ```{figure} ../assets/harmony-status-page.png
    :label: harmony-status-page-image
    :alt: Screenshot of the Harmony Status page in Earthdata Search
    :align: center
    :class: framed
    
    Once you click the **Download Data** button, the Harmony Status page will open and indicate progress.
    ```

7. Once processing is complete, the download links for the individual GeoTIFFs will be displayed. Click each link to download the products through the web browser, or click the **Download Files** button to leverage the Earthdata bulk download app.

    ```{figure} ../assets/harmony-status-complete.png
    :label: harmony-status-complete-image
    :alt: Screenshot of the Harmony Status page in Earthdata Search showing a completed job
    :align: center
    :class: framed
    
    Once processing is complete, the Harmony Status page will display the download links for the extracted GeoTIFFs. 
    ```