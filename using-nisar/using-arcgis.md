---
short_title: ArcGIS
---
# Using NISAR Data in ArcGIS

There are a number of Level 2 and 3 NISAR products that are suitable for use in GIS, as described in the [using GIS software overview](#using-gis-software). 

## NISAR Support in ArcGIS Pro

Support for the NISAR file format was added to ArcGIS Pro at version 3.4 (November 2024). Those using version 3.4.0 or newer are able to use NISAR products as they would any other HDF5 file in ArcGIS Pro. 

When using older versions of ArcGIS Pro, [refer to this documentation](https://www.earthdata.nasa.gov/learn/tutorials/work-nisar-sample-data#ArcEarly) for guidance. 

## NISAR in ArcGIS Tutorials

This page provides a quick introduction to working with NISAR data in ArcGIS. More in-depth tutorials are also available:

- The [NISAR in GIS](https://www.earthdata.nasa.gov/learn/gis/storymaps/nisar-gis) tutorial provides step-by-step guidance for adding NISAR data to an ArcGIS Pro project, visualizing the data, and using standard and SAR-specific imagery and analysis tools, focusing on the [GCOV](#gcov-product-overview) and [GUNW](#gunw-product-overview) products. 

- The [Spatial Subsetting for NISAR Data](https://storymaps.arcgis.com/stories/cac03522f82f420ab992316bb935a709) tutorial demonstrates workflows for subsetting NISAR products and transforming them to other data formats.

(arcgis-adding-nisar-data)=
## Adding NISAR Data

There are multiple options available for adding NISAR data to an ArcGIS Pro project. You can use the [Add Multidimensional Raster](#arcgis-add-multidimensional-raster-tool) tool or simply [Drag and Drop](#arcgis-drag-and-drop) the HDF5 file from the table of contents. Step-by-step guidance for each method can be found in the [NISAR Data in ArcGIS Pro](https://storymaps.arcgis.com/stories/c8f85d20b73c48fd8e89f8eef49bc60b#ref-n-4Bfbbu) section of the NISAR in GIS tutorial. 

(arcgis-add-multidimensional-raster-tool)=
### Add Multidimensional Raster Tool

Using the [Add Multidimensional Raster](https://storymaps.arcgis.com/stories/c8f85d20b73c48fd8e89f8eef49bc60b#ref-n-diybcG) tool provides more flexibility in how the variables are displayed. 

- Variables can each be added as individual layers or combined into [multivariate](https://storymaps.arcgis.com/stories/c8f85d20b73c48fd8e89f8eef49bc60b#ref-n-JNuqoM) or [multiband](https://storymaps.arcgis.com/stories/c8f85d20b73c48fd8e89f8eef49bc60b#ref-n-I2ow3f) rasters. 
- If you want to work with the variable in its native HDF5 format, this is the best option to use.

#### 1. Select **Multidimensional Data** from the **Add Data** menu

- Click on the **Map** menu
- Click on the bottom half of the **Add Data** button to open the menu
- Select **Multidimensional Data** to open the **Add Multidimensional Data** dialog window

```{figure} ../assets/add-multidimensional-raster-tool.png
:name: add-multidimensional-raster-tool-screenshot
:alt: Screenshot highlighting the Add Multidimensional Raster tool in ArcGIS Pro
:align: left

Click the **Add Data** menu and select **Multidimensional Data** to open the **Add Multidimensional Data** dialog window ArcGIS Pro.
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

#### Add HDF5 File from Catalog Pane

- Navigate to a NISAR HDF5 file in the **Catalog** pane
- Drag the file onto the map area
- Cancel the **Calculating Statistics** function
  - It is too time-consuming to run this function on the full HDF file; statistics can be calculated when a [variable is extracted using the subset tool](#arcgis-subset-multidim-raster-tool)

By default, the first variable in the HDF5 file is displayed, and any changes to symbology are applied to all variables in the file.

```{figure} ../assets/arcgis-drag-and-drop.png
:name: arcgis-drag-and-drop-screenshot
:alt: Screenshot demonstrating drag-and-drop capabilities in ArcGIS Pro
:align: left

Using drag-and-drop functionality to add NISAR data to an ArcGIS Pro project.
```

:::{note}No Access to Phase with Drag and Drop
You will not be able to access the phase values in complex-valued variables, such as wrapped interferograms, using the drag-and-drop method. 

Use the **[Add Multidimensional Raster](#arcgis-add-multidimensional-raster-tool)** tool and select **Multiband Raster** as the layer format in order to access both the amplitude and phase components of the dataset.
:::

(arcgis-visualizing-nisar-data)=
## Visualizing NISAR Data

Most NISAR data does not visualize well by default, and symbology adjustments need to be applied to view features of interest. Refer to the [NISAR in GIS StoryMap](https://storymaps.arcgis.com/stories/c8f85d20b73c48fd8e89f8eef49bc60b) to learn more about adjusting symbology for [GCOV](https://storymaps.arcgis.com/stories/c8f85d20b73c48fd8e89f8eef49bc60b#ref-n-irIq6l) and [GUNW](https://storymaps.arcgis.com/stories/c8f85d20b73c48fd8e89f8eef49bc60b#ref-n-GR2AW1) product variables. 

### Symbology Settings

Symbology adjustments can be made for NISAR variables as you would any other layer. Right-click the layer and select **Symbology** to open the Symbology panel. 

```{figure} ../assets/arcgis-symbology.png
:name: arcgis-symbology-screenshot
:alt: Screenshot showing how to access the Symbology settings in ArcGIS Pro
:align: left

Right-click a layer and select **Symbology** to open the Symbology settings pane.
```

By default, ArcGIS displays NISAR variables using the `Spectrum - Full Bright` color scheme. SAR backscatter is traditionally displayed in grayscale, with lower values appearing darker than higher values, but you can apply whatever color scheme you prefer. If you do want to use the traditional grayscale rendering, make sure that the **Invert** check-box is cleared.

```{figure} ../assets/arcgis-symbology-grayscale.png
:name: arcgis-symbology-grayscale-screenshot
:alt: Screenshot showing how to set the color scheme in ArcGIS Pro
:align: center
:width: 30%

Change the color scheme for the layer. To use a traditional grayscale scheme, clear the check next to **Invert** when selecting the `Black-to-White` color scheme.
```

#### Viewing Amplitude Data

When viewing [amplitude data](#gis-amplitude-products), the images tend to appear very dark when using the default symbology. Because most backscatter values are very close to 0, it's helpful to change the stretch settings to focus on the range of the majority of the pixel values. 

One way to quickly render a view of the landscape is to apply a Standard Deviation stretch using Dynamic Range Adjustment (DRA). 

Set the **Stretch type** to `Standard Deviation`. In the Statistics tab, set **Statistics** to `DRA`. You may want adjust the number of standard deviations to see what works best for your particular area. Values between 1 and 2 are often suitable for backscatter. 

```{figure} ../assets/arcgis-symbology-std-dev-dra.png
:name: arcgis-symbology-std-dev-dra-screenshot
:alt: Screenshot showing how to set a standard deviation stretch symbology using dynamic range adjustment in ArcGIS Pro
:align: left

Set the **Stretch type** to `Standard Deviation`, and set the **Statistics** type to `DRA` in the Statistics tab.
```

Another option is to set a custom Minimum-Maximum value range. Experiment to find the values that work best to view the features you want to see in your area of interest. Keep in mind that cross-pol (HV or VH) backscatter values tend to be lower than co-pol (HH or VV) returns, so you may need to use different ranges depending on the polarization.

Change the **Stretch** setting to `Minimum-Maximum` if necessary. In the Statistics tab, set **Statistics** to Custom, and enter the desired **Min** and **Max** values. 

```{figure} ../assets/arcgis-symbology-min-max.png
:name: arcgis-symbology-min-max-screenshot
:alt: Screenshot showing how to set custom min-max values for stretch symbology in ArcGIS Pro
:align: left

For the Minimum-Maximum stretch, set the **Statistics** type to `Custom`, and enter the desired pixel values for **Min** and **Max**.
```

#### Viewing Coherence Data

The [Coherence variables](#gis-coherence) included in the GUNW products are traditionally displayed in grayscale, and stretched from 0 to 1. You can use whatever color scheme you prefer, but by using the `Minimum-Maximum` **Stretch type** and setting the **Min** and **Max** values to `0` and `1`, you can render a consistent visualization across products, regardless of the range of actual values represented in each different coherence layer. 

```{figure} ../assets/arcgis-symbology-coh.png
:name: arcgis-symbology-coh-screenshot
:alt: Screenshot showing a common approach for viewing coherence data in ArcGIS Pro
:align: left

To include the full range of potential coherence values, use a `Minimum-Maximum` **Stretch type** and set the **Statistics** type to `Custom` with a **Min** value of `0` and a **Max** value of `1`.
```

### Maintaining Symbology Settings
Sometimes connections to the source HDF5 variable are broken, and symbology settings may not be preserved even if you use the **Set Data Source** dialog in the layer properties (under the **Source** tab) to re-set the variable path. 

If you make symbology changes to a NISAR variable and you want them to persist, consider [exporting the variable](#arcgis-export-raster) as a stand-alone raster first, which provides a more stable source for ArcGIS projects. It also allows you to save the data as a layer, including the symbology settings, for use in other projects. 

(arcgis-transforming-nisar-data)=
## Transforming NISAR Data

There are many reasons for transforming NISAR variables. You may prefer working with a particular raster file format, require a different coordinate system or projection, need to resample the data to match another dataset, or want to subset the dataset spatially to make analysis more manageable. 

There are a number of approaches for transforming NISAR variables in ArcGIS Pro. The [Subset Multidimensional Raster Tool](#arcgis-subset-multidim-raster-tool) and the [Export Raster](#arcgis-export-raster) function are well suited for use with NISAR data. Both methods provide the ability to apply multiple transformations at the same time.

(arcgis-subset-multidim-raster-tool)=
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
7. If you want to export the variable using the [default environment settings](#arcgis-adjust-environment-settings), click the **OK** button to export the variable

```{figure} ../assets/arcgis-subset-tool.png
:name: arcgis-subset-tool-screenshot
:alt: Screenshot demonstrating using the subset tool in ArcGIS Pro
:align: left

Using the Subset tool to extract variables from an HDF5 file added to ArcGIS Pro using the Drag-and-Drop method.
```

(arcgis-adjust-environment-settings)=
#### Adjust Environment Settings

The **Environment** tab of the **Subset Multidimensional Raster** Geoprocessing dialog provides a convenient interface for applying dataset transformations as a variable is being extracted. 

You can output the variable with a different coordinate system, apply [spatial subsetting](#arcgis-subset-spatial-subsetting), change the pixel size, or adjust the raster storage characteristics (pyramid behavior, statistic calculation approach, compression, resampling method).

(arcgis-subset-spatial-subsetting)=
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

Once you've adjusted the settings in the **Environments** tab, return to the **Parameters** tab to verify that all other settings are correct before clicking the **OK** button to export the variable to a stand-alone raster format.

(arcgis-export-raster)=
### Export Raster

To export an HDF5 variable added as an individual layer using the @arcgis-add-multidimensional-raster-tool, you can simply use the **Export Raster** function. Access this function using one of these methods: 

- Right-click the layer in the **Contents** pane, select **Data** from the menu, and click **Export Raster** (@arcgis-export-raster-screenshot)

```{figure} ../assets/arcgis-export-raster.png
:name: arcgis-export-raster-screenshot
:alt: Screenshot demonstrating accessing the Export Raster function from the context menu for an item in the **Contents** pane in ArcGIS Pro
:align: center
:width: 90%

Accessing **Export Raster** from the context menu for an item in the **Contents** pane. 
```

- Select the layer in the **Contents** pane, and click the Export Raster button in the **Data** menu (@arcgis-export-raster-button-screenshot)

```{figure} ../assets/arcgis-export-raster-button.png
:name: arcgis-export-raster-button-screenshot
:alt: Screenshot demonstrating accessing the Export Raster function from the Data menu in ArcGIS Pro
:align: center
:width: 90%

Accessing **Export Raster** from the Data menu for an item in the **Contents** pane. 
```

In the Export Raster dialog window: 

1. Set the path and filename for the output raster
2. Select the raster format to use
3. If you want to export the variable using the [default settings](#arcgis-export-raster-settings), click the **Export** button

```{figure} ../assets/arcgis-export-raster-dialog.png
:name: arcgis-export-raster-dialog-screenshot
:alt: Screenshot illustrating the Export Raster function dialog window 

Set the output file path and file type in the **Export Raster** dialog window. 
```

(arcgis-export-raster-settings)=
#### Export Raster Settings

As with the @arcgis-subset-multidim-raster-tool, there are a number of settings that can be adjusted to apply additional data transformations when exporting the variable to a stand-alone raster. 

Some of these settings are accessed directly in the **General** tab, including:

- Coordinate system
- [Spatial extent](#arcgis-export-spatial-subsetting)
- Cell size
- Pixel type
- Rendering type
- Compression type/quality

Additional options are available in the **Settings** tab, including: 

- Snap Raster options
- Resampling options
- Pyramid options
- Statistics options

(arcgis-export-spatial-subsetting)=
#### Spatial Subsetting

The options available for setting a spatial extent are available in the **Clipping Geometry** section of the **General** tab. 

The **Clipping Geometry** drop-down menu provides the option to use the current map extent or the extent of a layer in the map. It's convenient to use a feature class containing a single feature (or restricted to a single feature using a definition query) to set the extent, as illustrated by the Area of Interest (AOI) feature class used in @arcgis-export-raster-spatial-extent-screenshot. 

You can also click the **Browse** icon to navigate to a saved geospatial file, or manually enter an extent in the **Extent** fields.

```{figure} ../assets/arcgis-export-raster-spatial-extent.png
:name: arcgis-export-raster-spatial-extent-screenshot
:alt: Screenshot illustrating setting the raster extent in the Export Raster dialog window

Set the raster extent in the **Export Raster** dialog window. 
```

Once all the other settings (in both the **General** and **Settings** tabs) are set as desired, click the **Export** button to export the variable to a stand-alone raster with the desired spatial extent.