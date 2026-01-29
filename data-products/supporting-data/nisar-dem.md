---
short_title: DEM for NISAR
---

# Copernicus DEM for NISAR

{button}`Find Data <https://search.earthdata.nasa.gov/search?q=NISAR_DEM>`

The modified Copernicus Digital Elevation Model used by the NISAR mission is a tiled collection of Cloud-Optimized GeoTIFF (COG) files representing the DEM used for processing NISAR products. 

## DEM Overview

The DEM used for NISAR product generation is derived from the [Copernicus DEM 30-m COP-DEM_GLO-30-DGED/2023_1](https://doi.org/10.5270/ESA-c5d3d65). Areas over the ocean are filled using the EGM2008 geoid model, resulting in a DEM with complete global coverage. Elevation values are ellipsoid-corrected for use in Synthetic Aperture Radar (SAR) processing workflows.

:::{warning}Modified for SAR Applications
Because this DEM has had an ellipsoid correction applied, which is necessary for SAR processing, the elevation values will differ from the source DEM. It should not be used for non-SAR applications, which typically require geoid-based elevations. 

```{figure} ../../assets/ellipsoid-geoid.png
:label: ellipsoid-geoid
:alt: Figure illustrating the difference between ellipsoid and geoid heights.
:align: left
:width: 75%

The elevation values in most DEMs are calculated relative to a geoid model, and require a conversion before being used in SAR processing workflows. This figure from @ellipsoid_diagram illustrates the relationship between measurements based on geoid and ellipsoid models.
```
:::

This dataset allows SAR scientists to generate their own higher-level products from NISAR data using the same input DEM as the mission-generated products. 

:::{important}Not Generated from NISAR Data
It is important to note that this dataset is _not_ generated from NISAR-acquired data. It is modified from an existing DEM, and used in NISAR data processing workflows. 
:::

The data are available from NASA's Alaska Satellite Facility Distributed Active Archive Center (ASF DAAC) through Earthdata Search as well as through [direct S3 access](#aws-s3-access-overview) within the AWS us-west-2 region.

## DEM Datasets

The DEM is provided in three different projections: 

- [WGS84](#dem-extent-4326) ([EPSG 4326](https://epsg.io/4326))
- [North Polar Stereographic](#dem-extent-3413) ([EPSG 3413](https://epsg.io/3413))
- [South Polar Stereographic](#dem-extent-3031) ([EPSG 3031](https://epsg.io/3031))

The DEM dataset in the WGS84 projection provides global coverage, while the DEM datasets in polar projections are only available for regions beyond 60 degrees north or south.

```{figure} ../../assets/dem-extent-4326.png
:label: dem-extent-4326
:alt: Visualization of the WGS84 DEM for NISAR.
:align: left

Visualization of the WGS84 DEM for NISAR.
```
```{figure} ../../assets/dem-extent-3413.png
:label: dem-extent-3413
:alt: Visualization of the North Polar Stereographic DEM for NISAR.
:align: left

Visualization of the North Polar Stereographic DEM for NISAR.
```
```{figure} ../../assets/dem-extent-3031.png
:label: dem-extent-3031
:alt: Visualization of the South Polar Stereographic DEM for NISAR.
:align: left

Visualization of the South Polar Stereographic DEM for NISAR.
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

### DEM Naming Conventions

The actual filenames of the DEM tiles are quite basic, differing only by the indication of the geographic location of the tile. 

The WGS84 files include the latitude and longitude of the lower left corner of the tile. For example: 
`DEM_N00_00_E005_00_C01.tif`

The Polar Stereographic files include a reference to the 100 x 100 km tile number. For example:
`DEM_11_00_23_00_C01.tif`

In Earthdata Search, each file is given a title that also includes the projection. These titles are based on the S3 path where the files are stored.

## Finding DEMs

The DEM for NISAR files can be found in Earthdata Search by searching for "NISAR_DEM": [Find Data in Earthdata Search](https://search.earthdata.nasa.gov/search?q=NISAR_DEM)

All three DEM datasets are included in one [NISAR_DEM](https://www.earthdata.nasa.gov/data/catalog/asf-nisar-dem-1) collection. They are accessible through [Earthdata Search](https://search.earthdata.nasa.gov/search?q=NISAR_DEM), but not currently discoverable in Vertex. The projection is included in the title for each DEM file in Earthdata Search, making it easy to restrict searches to a single projection.

Each DEM filename gives an indication of its geographic location, which you can use to locate the tiles you need, but it is easiest to use Earthdata Search to find the necessary tiles for a specific geographic area of interest. To incorporate subsetting into a programmatic workflow, it is useful to leverage @vrt-subsetting.

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

## S3 File Organization

While the DEM files are all included in a single collection, they are divided into different S3 prefixes based on their projection. When searching for content directly in S3, the DEM prefix includes a version prefix (v1.2), then a prefix for each different projection: 

- EPSG4326
- EPSG3413
- EPSG3031

Refer to @aws-s3-access-overview for more information on searching for data directly in S3.