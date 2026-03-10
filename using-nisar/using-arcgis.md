---
short_title: ArcGIS
---
# Using NISAR Data in ArcGIS

Support for the NISAR file format was added to ArcGIS Pro at version 3.4 (November 2024). Those using version 3.4.0 or newer are able to use NISAR products as they would any other HDF5 file in ArcGIS Pro. 

When using older versions of ArcGIS Pro, [refer to this documentation](https://www.earthdata.nasa.gov/learn/tutorials/work-nisar-sample-data#ArcEarly) for guidance. 

## NISAR in ArcGIS Tutorials

The [NISAR in GIS](https://www.earthdata.nasa.gov/learn/gis/storymaps/nisar-gis) tutorial provides step-by-step guidance for adding NISAR data to an ArcGIS Pro project, visualizing the data, and using standard and SAR-specific imagery and analysis tools, focusing on the [GCOV](gcov-product-overview) and [GUNW](gunw-product-overview) products. 

The [Spatial Subsetting for NISAR Data](https://storymaps.arcgis.com/stories/cac03522f82f420ab992316bb935a709) tutorial demonstrates workflows for subsetting NISAR products and transforming them to other data formats.

(arcgis-adding-nisar-data)=
## Adding NISAR Data

There are multiple options available for adding NISAR data to an ArcGIS Pro project. You can either use the [Add Multidimensional Raster](#arcgis-add-multidimensional-raster-tool) tool or simply [Drag and Drop](#arcgis-drag-and-drop) the HDF5 file from the table of contents. Step-by-step guidance for each method can be found in the [NISAR Data in ArcGIS Pro section of the NISAR in GIS](https://storymaps.arcgis.com/stories/c8f85d20b73c48fd8e89f8eef49bc60b#ref-n-4Bfbbu) tutorial. 

(arcgis-add-multidimensional-raster-tool)=
### Add Multidimensional Raster Tool

Using the [Add Multidimensional Raster](https://storymaps.arcgis.com/stories/c8f85d20b73c48fd8e89f8eef49bc60b#ref-n-diybcG) tool provides more flexibility in how the variables are displayed. 

- Variables can each be added as individual layers or combined into [multivariate](https://storymaps.arcgis.com/stories/c8f85d20b73c48fd8e89f8eef49bc60b#ref-n-JNuqoM) or [multiband](https://storymaps.arcgis.com/stories/c8f85d20b73c48fd8e89f8eef49bc60b#ref-n-I2ow3f) rasters. 
- If you want to work with the variable in its native HDF5 format, this is the best option to use.

#### 1. Select **Multidimensional Data** from the **Add Data** menu

- Click on the **Map** menu
- Click on the bottom half of the **Add Data** button to open the menu
- Select **Multidimensional Data** to open the **Add Multidimensional Data** dialog box

```{figure} ../assets/add-multidimensional-raster-tool.png
:name: add-multidimensional-raster-tool-screenshot
:alt: Screenshot highlighting the Add Multidimensional Raster tool in ArcGIS Pro
:align: left

Click the **Add Data** menu and select **Multidimensional Data** to add NISAR data in ArcGIS Pro.
```

#### 2. Select Desired Variables

- Click the **Browse** icon in the Add Multidimensional Data dialog box
- Navigate to a NISAR file and select it to view the available variables
- Check the box next to the variable(s) you want to add to the map
- Leave the **Output Configuration** set to `Multidimensional Raster` to add each selected variable as its own layer in the map
- Click **OK** to add the variables

```{figure} ../assets/add-multidimensional-raster-tool-variables.png
:name: add-multidimensional-raster-tool-variables-screenshot
:alt: Screenshot illustrating how to select desired variables in an HDF5 file using the Add Multidimensional Raster tool in ArcGIS Pro
:align: left

Select desired variables from a NISAR file to add them as individual layers to the map.
```

The `Multidimensional Raster` output configuration is the best choice for adding most variables to the map as individual layers. However, to add complex-valued variables, such as wrapped interferograms, you will need to select `Multiband Raster` as the output format in order to access both the amplitude and phase components of the dataset. 

(arcgis-drag-and-drop)=
### Drag and Drop

You can simply drag and drop the entire file from the **Catalog** pane. This approach is most useful when you want to export individual variables to other data formats before working with them in ArcGIS Pro. 

The ability to adjust visualizations, use imagery tools, or perform analysis is limited when you add the entire HDF5 file to the map. 

:::{note}Drag and Drop not supported for complex-valued variables
You will not be able to work with complex-valued variables, such as wrapped interferograms, using the drag-and-drop method. You would need to use the **Add Multidimensional Raster** tool, and select **Multiband Raster** as the layer format in order to access both the amplitude and phase components of the dataset.
:::

#### 1. Drag Desired File from Catalog Pane

- Navigate to a NISAR HDF5 file in the **Catalog** pane
- Drag the file onto the map area
- Cancel the **Calculating Statistics** function
  - It is too time-consuming to run this function on the full HDF file; statistics are calculated when a [variable is extracted](#2-extract-variables)

By default, the first variable in the HDF5 file is displayed, and any changes to symbology are applied to all variables in the file. 

```{figure} ../assets/arcgis-drag-and-drop.png
:name: arcgis-drag-and-drop-screenshot
:alt: Screenshot demonstrating drag-and-drop capabilities in ArcGIS Pro
:align: left

Using drag-and-drop functionality to add NISAR data to an ArcGIS Pro project.
```


(arcgis-visualizing-nisar-data)=
## Visualizing NISAR Data




(arcgis-transforming-nisar-data)=
## Transforming NISAR Data

There are many reasons for transforming NISAR variables. You may prefer working with a particular raster file format, require a different coordinate system or projection, need to resample the data to match another dataset, or want to subset the dataset spatially to make analysis more manageable. 

There are a number of approaches for transforming NISAR variables in ArcGIS Pro.

### Subset Multidimensional Raster Tool

To extract variables from an HDF5 file, you can use the **Subset** tool in the **Data Management** menu to save individual variables to a stand-alone raster format. 

This tool can be used either with a full HDF5 layer that was added to the project using the @arcgis-drag-and-drop method, or with individual layers added using the @arcgis-add-multidimensional-raster-tool interface.

1. Click on an HDF5 layer or an individual variable layer in the **Contents** pane
2. Click on the **Multidimensional** menu tab
3. Click the **Data Management** button
4. Select **Subset** to open the **Subset Multidimensional Raster** tool
5. Edit the **Output Multidimensional Raster** field to enter the desired filename
   - The default output format is [Cloud Raster Format (CRF)](https://pro.arcgis.com/en/pro-app/latest/help/data/imagery/an-overview-of-multidimensional-raster-data.htm#ESRI_SECTION1_22F66BF74FAB42BAA35FD55E21A17201), but you can simply type `.tif` as the file extension to output the variable as a GeoTIFF
6. If working with a full HDF5 layer, check the box next to the desired variable to export
   - If you've referenced an individual variable layer, only that one variable will be listed, and is checked by default
7. If you want to export the variable using the [default environment settings](#adjust-environment-settings), click the **OK** button to export the variable

```{figure} ../assets/arcgis-subset-tool.png
:name: arcgis-subset-tool-screenshot
:alt: Screenshot demonstrating using the subset tool in ArcGIS Pro
:align: left

Using the Subset tool to extract variables from an HDF5 file added to ArcGIS Pro using the Drag-and-Drop method.
```

#### Adjust Environment Settings

The **Environment** tab of the **Subset Multidimensional Raster** Geoprocessing dialog provides a convenient method to transform the dataset as it is being exported. 

You can output the variable with a different coordinate system, apply spatial subsetting, change the pixel size, or adjust the raster storage characteristics (pyramid behavior, statistic calculation approach, compression, resampling method).

#### Spatial Subsetting

To extract a spatial subset of the variable using the subset tool: 

1. Click on the **Environments** tab
2. Set the processing extent using one of the available options indicated by the icons, including:
   - Use the current map extent
   - Manually draw an extent on the map (as illustrated in @arcgis-subset-tool-spatial-extent-screenshot)
   - Use the extent of a layer in the map
   - Use the extent of a saved geospatial file

```{figure} ../assets/arcgis-subset-tool-spatial-extent.png
:name: arcgis-subset-tool-spatial-extent-screenshot
:alt: Screenshot demonstrating applying a spatial extent environment setting to the subset tool in ArcGIS Pro
:align: left

Setting the Environment variables in the Subset tool to apply a spatial extent to variables extracted from an HDF5 file added to ArcGIS Pro using the Drag-and-Drop method.
```

Once you've adjusted the Environmental settings, return to the Parameters tab to verify that all other settings are correct before clicking the **OK** button to export the variable to a stand-alone raster format.


(arcgis-subsetting-nisar-data)=
### Subsetting

(arcgis-converting-nisar-format)=
### Converting Format










