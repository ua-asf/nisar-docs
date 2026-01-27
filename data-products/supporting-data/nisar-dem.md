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
:::

This dataset allows SAR scientists to generate their own higher-level products from NISAR data using the same input DEM as the mission-generated products. 

:::{important}Not Generated from NISAR Data
It is important to note that this dataset is _not_ generated from NISAR-acquired data. It is modified from an existing DEM, and used in NISAR data processing workflows. 
:::

The data are available from NASA's Alaska Satellite Facility Distributed Active Archive Center (ASF DAAC) through Earthdata Search as well as through [direct S3 access](aws-s3-access-overview) within the AWS us-west-2 region.

## DEM Datasets

The DEM is provided in three different projections: 

- WGS84 ([EPSG 4326](https://epsg.io/4326))
- North Polar Stereographic ([EPSG 3413](https://epsg.io/3413))
- South Polar Stereographic ([EPSG 3031](https://epsg.io/3031))

The DEM dataset in the WGS84 projection provides global coverage, while the DEM datasets in polar projections are only available for regions beyond 60 degrees north or south.

<!-- #TODO: add a map of the coverage for each DEM dataset -->

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

All three DEM datasets are included in one [NISAR_DEM](https://www.earthdata.nasa.gov/data/catalog/asf-nisar-dem-1) collection. They are accessible through [Earthdata Search](https://search.earthdata.nasa.gov/search?q=NISAR_DEM), but not currently discoverable in Vertex. The projection is included in the filename, making it easy to restrict searches to a single projection.

Each DEM filename gives an indication of its geographic location, which you can use to locate the tiles you need, but it is easiest to use Earthdata Search to find the necessary tiles for a specific geographic area of interest. To incorporate subsetting into a programmatic workflow, it is useful to leverage the [DEM VRT](#dem-vrt-files) files 

(dem-vrt-files)=
### DEM VRT Files

Enables programmatic subsetting to a custom AOI

### S3 File Organization

While the DEM files are all included in a single collection, they are divided into different S3 prefixes based on their projection. When searching for content directly in S3, the DEM prefix includes a version prefix (v1.2), then a prefix for each different projection: 

- EPSG4326
- EPSG3413
- EPSG3031

Refer to @aws-s3-access-overview for more information on searching for data directly in S3.