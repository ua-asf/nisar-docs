---
short_title: DEM for NISAR
---

# Modified Copernicus DEM for NISAR

{button}`Find Data <https://search.earthdata.nasa.gov/search?q=NISAR_DEM>`

The [Modified Copernicus Digital Elevation Model used by the NISAR Mission](https://www.earthdata.nasa.gov/data/catalog/asf-nisar-dem-1) is a tiled collection of Cloud-Optimized GeoTIFF (COG) files representing the DEM used for processing NISAR products. 

## DEM for NISAR Overview

The DEM used for NISAR product generation is derived from the [Copernicus DEM 30-m COP-DEM_GLO-30-DGED/2023_1](https://doi.org/10.5270/ESA-c5d3d65). Elevation values are re-referenced vertically from the EGM2008 geoid model to the WGS84 ellipsoid model, and areas over the ocean are filled. This results in a DEM suitable for use in SAR processing workflows, with complete global coverage. 

:::{warning}Modified for SAR Applications
Because this DEM has been re-referenced from a geoid model to an ellipsoid model, which is necessary for SAR processing, the elevation values will differ from the source DEM.

```{figure} ../../assets/ellipsoid-geoid.png
:label: ellipsoid-geoid
:alt: Figure illustrating the difference between ellipsoid and geoid heights.
:align: left
:width: 75%

The elevation values in most DEMs are calculated relative to a geoid model, and require a conversion before being used in SAR processing workflows. This figure from @ellipsoid_diagram illustrates the relationship between measurements based on geoid and ellipsoid models.
```

This DEM is not suitable for use in applications that require geoid-based heights. For these applications, the original [Copernicus WorldDEM-30 (GLO-30)](https://doi.org/10.5270/ESA-c5d3d65) dataset should be used instead.
:::

This dataset allows SAR scientists to generate their own higher-level products from NISAR data using the same input DEM as the mission-generated products. 

:::{important}Not Generated from NISAR Data
This dataset is _not_ generated from NISAR-acquired data. It is modified from an existing DEM, and used in NISAR data processing workflows. 
:::

The data are available from NASA's Alaska Satellite Facility Distributed Active Archive Center (ASF DAAC) through [Earthdata Search](https://search.earthdata.nasa.gov/search?q=NISAR_DEM) as well as through [direct S3 access](#aws-s3-access-overview) within the AWS us-west-2 region.

(dem-datasets)=
## DEM Datasets

The DEM is provided in three different projections: 

- [WGS84](#dem-extent-4326) ([EPSG 4326](https://epsg.io/4326))
- [North Polar Stereographic](#dem-extent-3413) ([EPSG 3413](https://epsg.io/3413))
- [South Polar Stereographic](#dem-extent-3031) ([EPSG 3031](https://epsg.io/3031))

The DEM dataset in the WGS84 projection provides global coverage, while the DEM datasets in polar projections are only available for regions beyond 60 degrees north or south.

```{figure} ../../assets/dem-extent-4326.png
:label: dem-extent-4326
:alt: Visualization of the WGS84 DEM for NISAR. This dataset provides global coverage using the World Geodetic System 1984 (WGS84) geographic coordinate system ([EPSG 4326](https://epsg.io/4326)).
:align: left

Visualization of the WGS84 DEM for NISAR. This dataset provides global coverage using the World Geodetic System 1984 (WGS84) geographic coordinate system ([EPSG 4326](https://epsg.io/4326)).
```
```{figure} ../../assets/dem-extent-3413.png
:label: dem-extent-3413
:alt: Visualization of the North Polar Stereographic DEM for NISAR. This dataset provides coverage north of 60°N using the NSIDC Sea Ice Polar Stereographic North projected coordinate system ([EPSG 3413](https://epsg.io/3413)), based on the WGS84 coordinate reference system.
:align: left

Visualization of the North Polar Stereographic DEM for NISAR. This dataset provides coverage north of 60°N using the NSIDC Sea Ice Polar Stereographic North projected coordinate system ([EPSG 3413](https://epsg.io/3413)), based on the WGS84 coordinate reference system.
```
```{figure} ../../assets/dem-extent-3031.png
:label: dem-extent-3031
:alt: Visualization of the South Polar Stereographic DEM for NISAR. This dataset provides coverage south of 60°S using the Antarctic Polar Stereographic projected coordinate system ([EPSG 3031](https://epsg.io/3031)), based on the WGS84 coordinate reference system. 
:align: left

Visualization of the South Polar Stereographic DEM for NISAR. This dataset provides coverage south of 60°S using the Antarctic Polar Stereographic projected coordinate system ([EPSG 3031](https://epsg.io/3031)), based on the WGS84 coordinate reference system. 
```

### DEM Dataset Characteristics

:::{table} DEM for NISAR Dataset Characteristics
:label: tbl:nisar-dem-characteristics

|                    | WGS84                                                                                           | North Polar                                                                                     | South Polar                                                                                     |
|--------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| **EPSG Code**      | [4326](https://epsg.io/4326)                                                                    | [3413](https://epsg.io/3413)                                                                    | [3031](https://epsg.io/3031)                                                                    |
| **Spatial Extent** | Global                                                                                          | North of 60°N Latitude                                                                          | South of 60°S Latitude                                                                          |
| **Pixel Spacing**  | 30 m                                                                                            | 20 m{sup}`*`                                                                                    | 20 m{sup}`*`                                                                                    |
| **Tiling Scheme**  | 1 x 1 degree                                                                                    | 100 x 100 km                                                                                    | 100 x 100 km                                                                                    |
| **Readme File**    | [EPSG4326 Readme](https://nisar.asf.earthdatacloud.nasa.gov/NISAR/DEM/v1.2/EPSG4326/README.txt) | [EPSG3413 Readme](https://nisar.asf.earthdatacloud.nasa.gov/NISAR/DEM/v1.2/EPSG3413/README.txt) | [EPSG3031 Readme](https://nisar.asf.earthdatacloud.nasa.gov/NISAR/DEM/v1.2/EPSG3031/README.txt) |

{sup}`*` While the polar stereographic datasets have a pixel spacing of 20 meters, they are derived from the Copernicus 30-m DEM, so the resolution is coarser than the pixel spacing.
:::

## DEM Naming Conventions

The actual filenames of the DEM tiles are quite basic, differing only by the indication of the geographic location of the tile. While the naming scheme allows for two decimal places for each tile reference term, product names for all tiles use `_00` in the decimal placeholder.

### WGS84 Tiling Scheme

The WGS84 files include the latitude and longitude of the lower left corner of the tile.

For example: 
`DEM_N17_00_E135_00_C01.tif`

- `N17` indicates that the lower left corner of the tile is at 17°N
- `E135` indicates that the lower left corner of the tile is at 135°E

### Polar Stereographic Tiling Scheme

The North Polar Stereographic (@north-polar-grid) and South Polar Stereographic (@south-polar-grid) datasets have equivalent tiling schemes and use a common naming convention.

The coverage for these datasets is overlain with a 100 x 100 km grid, which is used to determine the extent of each DEM file. Tile coordinates (in both the X and Y axes of the grid) are numbered from 06 to 73, with tiles 39 and 40 straddling the pole. The tile coordinates are indicated in the name of each DEM file.

For example:
`DEM_20_00_64_00_C01.tif`  

- `20` refers to the bottom-to-top Y coordinate of the tile
- `64` refers to the left-to-right X coordinate of the tile

```{figure} ../../assets/north-polar-grid.png
:label: north-polar-grid
:alt: Gridding system for the North Polar Stereographic DEM dataset, highlighting an example tile location and its corresponding file name.
:align: left

Gridding system for the North Polar Stereographic DEM dataset. 
```

```{figure} ../../assets/south-polar-grid.png
:label: south-polar-grid
:alt: Gridding system for the South Polar Stereographic DEM dataset, highlighting an example tile location and its corresponding file name.
:align: left

Gridding system for the South Polar Stereographic DEM dataset.
```

:::{warning}Duplicate Names for Polar Stereographic Files
The dataset projection is not included in the DEM file names. Because the two Polar Stereographic datasets use the same naming scheme, the same file names are present in both datasets. 

Use care when downloading DEM files from both of the Polar Stereographic datasets to avoid overwriting files. 
:::

### Earthdata File Titles

In [Earthdata Search](https://search.earthdata.nasa.gov/search?q=NISAR_DEM), each file is given a title that includes the coordinate system code (EPSG number). These titles are based on the [S3 path](#s3-file-organization) where the files are stored, and results in a unique title for each file. 

While these unique titles are helpful for finding specific DEM files during the search process, the actual filenames of the downloaded files only partially match these titles. This is particularly important to know when working with the polar stereographic datasets, as the filenames used for the north and south polar datasets are identical. 

Examples comparing Earthdata titles to actual filenames: 

- WGS84
  - Earthdata title: `v1-2-EPSG4326-N20-N20_E160-DEM_N23_00_E162_00_C01-tif`
  - File name: `DEM_N23_00_E162_00_C01.tif`
- North Polar Stereographic
  - Earthdata title: `v1-2-EPSG3413-60_40-DEM_73_00_43_00_C01-tif`
  - File name: `DEM_73_00_43_00_C01.tif`
- South Polar Stereographic
  - Earthdata title: `v1-2-EPSG3031-60_40-DEM_73_00_43_00_C01-tif`
  - File name: `DEM_73_00_43_00_C01.tif`

## DEM File Types

The actual DEM data is contained in tiled assemblages of Cloud Optimized GeoTIFF (COG) files, but the NISAR_DEM collection also includes [VRT](#vrt-reference-files) files. VRTs are virtual files that reference the tiled DEM COGs, allowing them to be visualized as a mosaic. <!-- #TODO: Add reference to the product spec -->

(tiled-dem-cog-files)=
### Tiled DEM COG Files

The DEM height values are contained in the COG files. The files are tiled to provide complete coverage for each of the [projection-based datasets](#dem-datasets) included in the DEM collection. The tiling scheme differs based on the projection, as indicated in @tbl:nisar-dem-characteristics.

These files have an extension of `.tif`.

(vrt-reference-files)=
### VRT Reference Files

To facilitate visualization and subsetting of the tiled DEM COG files, [VRT](https://gdal.org/en/stable/drivers/vector/vrt.html) files are available for each polarization. These VRT files are just a metadata file, and require access to the associated DEM COG files to be useful. 

These files have an extension of `.vrt`.

There are multiple VRT files for each projection. Each projection has a dataset-wide VRT, with one or more layers of VRTs that organize smaller subsets of data:
* The global WGS84 dataset includes a VRT for each latitude band, which each reference another layer of VRTs grouping smaller collections of COGs within each latitude band. 
* The datasets with polar projections just have one layer of VRTs under the dataset-wide VRT, grouping together collections of COGs by spatial location.

:::{warning}VRT Files Require Source DEM Files
If you only download VRT files to your local compute environment, they will not display anything. The source DEM COG files referenced by the downloaded VRT must also be downloaded to the same location, and be arranged in the file structure expected by the VRT, in order to visualize mosaics locally. 
:::

The VRT files are more useful when interacting with the DEM files directly in the cloud, where they can be used to find the necessary DEM COGs for an area of interest in programmatic workflows. Refer to @vrt-subsetting for more guidance.

## Finding DEM Files

The DEM for NISAR files can be found in Earthdata Search by searching for "NISAR_DEM".  
[Find Data in Earthdata Search](https://search.earthdata.nasa.gov/search?q=NISAR_DEM)

All three DEM datasets (with their [tiled GeoTIFFs](#tiled-dem-cog-files) and associated [VRT files](#vrt-reference-files)) are included in one [NISAR_DEM](https://www.earthdata.nasa.gov/data/catalog/asf-nisar-dem-1) collection. They are accessible through [Earthdata Search](https://search.earthdata.nasa.gov/search?q=NISAR_DEM), but not currently discoverable in Vertex. The projection is included in the title for each DEM file in Earthdata Search, making it easy to restrict searches to a single projection.

Each DEM filename gives an indication of its geographic location, which you can use to locate the tiles you need, but it is easiest to use Earthdata Search to find the necessary tiles for a specific geographic area of interest. To incorporate subsetting into a programmatic workflow, it is useful to leverage @vrt-subsetting.

(s3-file-organization)=
## S3 File Organization

The DEM files are hosted in NASA's [Earthdata Cloud (EDC)](https://www.earthdata.nasa.gov/about/earthdata-cloud-evolution), in the [same S3 bucket](#nisar-s3-buckets) as the data products from the NISAR mission. While the DEM files for all three projections are included in a single Earthdata collection ([NISAR_DEM](https://www.earthdata.nasa.gov/data/catalog/asf-nisar-dem-1)), they are archived under projection-specific S3 prefixes in EDC. 

When searching for DEM files [directly in S3](#aws-s3-access-overview), the path includes the DEM prefix, followed by a version prefix (v1.2), then a prefix specific to each different projection: 

- `/DEM/v1.2/EPSG4326`
- `/DEM/v1.2/EPSG3413`
- `/DEM/v1.2/EPSG3031`

Refer to @aws-s3-access-overview for more information on direct S3 access.

(vrt-subsetting)=
## Subsetting via Global VRT Mosaics

A global mosaic is provided for each DEM in the form of a [VRT](https://gdal.org/en/stable/drivers/raster/vrt.html) file. This enables subsetting the global DEM to any specific area of interest while downloading only the needed data.

The following examples demonstrate subsetting using the [gdalwarp](https://gdal.org/en/stable/programs/gdalwarp.html) utility via the [/vsicurl](https://gdal.org/en/stable/user/virtual_file_systems.html#vsicurl-http-https-ftp-files-random-access) and [/vsis3](https://gdal.org/en/stable/user/virtual_file_systems.html#vsis3-aws-s3-files) drivers. These examples will subset the DEM VRT to a 0.1° x 0.1° region in Death Valley, CA, USA. 

### Subsetting via /vsicurl

GDAL's [/vsicurl](https://gdal.org/en/stable/user/virtual_file_systems.html#vsicurl-http-https-ftp-files-random-access) driver enables interacting with data files hosted online through a URL. The URLs for the three VRT mosaics are:
```
https://nisar.asf.earthdatacloud.nasa.gov/NISAR/DEM/v1.2/EPSG4326/EPSG4326.vrt
https://nisar.asf.earthdatacloud.nasa.gov/NISAR/DEM/v1.2/EPSG3413/EPSG3413.vrt
https://nisar.asf.earthdatacloud.nasa.gov/NISAR/DEM/v1.2/EPSG3031/EPSG3031.vrt
```

1. Create a `.netrc` file containing your Earthdata Login credentials as described in [Creating a .netrc File for Earthdata Login](https://nsidc.org/data/user-resources/help-center/creating-netrc-file-earthdata-login)
1. Set the following GDAL configuration options via environment variables:
   ```shell
   export GDAL_DISABLE_READDIR_ON_OPEN=TRUE
   export GDAL_HTTP_COOKIEFILE=~/cookies.txt
   export GDAL_HTTP_COOKIEJAR=~/cookies.txt
   ```
1. Run the subsetting command:
   ```
   gdalwarp /vsicurl/https://nisar.asf.earthdatacloud.nasa.gov/NISAR/DEM/v1.2/EPSG4326/EPSG4326.vrt out.tif -te -116.7 35.9 -116.6 36.0
   ```

### Subsetting via /vsis3

GDAL's [/vsis3](https://gdal.org/en/stable/user/virtual_file_systems.html#vsis3-aws-s3-files) driver enables interacting with data files hosted in AWS S3. The S3 URIs for the three VRT mosaics are:
```
s3://sds-n-cumulus-prod-nisar-products/DEM/v1.2/EPSG4326/EPSG4326.vrt
s3://sds-n-cumulus-prod-nisar-products/DEM/v1.2/EPSG3413/EPSG3413.vrt
s3://sds-n-cumulus-prod-nisar-products/DEM/v1.2/EPSG3031/EPSG3031.vrt
```

1. Configure temporary AWS credentials as described in @aws-s3-access-overview.
1. Run the subsetting command:
   ```
   gdalwarp /vsis3/sds-n-cumulus-prod-nisar-products/DEM/v1.2/EPSG4326/EPSG4326.vrt out.tif -te -116.7 35.9 -116.6 36.0
   ```

## Acknowledging the DEM for NISAR

Users, including those who redistribute, adapt, modify, or combine Copernicus DEM for NISAR data, must comply with the terms of the Copernicus DEM 30m License Agreement. For additional information, please refer to [Modified Copernicus Digital Elevation Models used by the NASA-ISRO Synthetic Aperture Radar (NISAR) Mission](https://doi.org/10.5067/NIDEM-1) and [Copernicus DEM - Global and European Digital Elevation Model](https://doi.org/10.5270/ESA-c5d3d65).

When distributing the Modified Copernicus DEM for NISAR, acknowledge the dataset using the following statement<!-- #TODO: add link to legal agreement -->: 

> Produced using Copernicus WorldDEM-30 © DLR e.V. 2010-2014 and © Airbus Defence and Space GmbH 2014-2018 provided under COPERNICUS by the European Union and ESA; all rights reserved. The organisations in charge of the Copernicus programme by law or by delegation do not incur any liability for any use of the
Copernicus WorldDEM-30.

### Citing the DEM

To cite the Modified Copernicus Digital Elevation Models used by the NASA-ISRO Synthetic Aperture Radar (NISAR) Mission, refer to the [Dataset Citation](https://www.earthdata.nasa.gov/data/catalog/asf-nisar-dem-1#toc-copy-citation).
