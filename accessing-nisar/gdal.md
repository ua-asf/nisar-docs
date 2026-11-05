# GDAL

The [Geospatial Data Abstraction Library (GDAL)](https://gdal.org/en/stable) is an open-source software library used to work with raster and vector geospatial data. There are a number of GDAL command-line interface (CLI) utilities that we can leverage to transform NISAR data.

(gdal-nisar)=

## Using GDAL to Transform NISAR Data

NISAR products are distributed in HDF5 format, and the files can be very large. Many users may want to transform the data by extracting just the datasets of interest from the HDF5 files and/or subsetting the data to a defined spatial extent.

We can use command-line utilities from the GDAL software library to transform these files. Leveraging GDAL's ability to stream data from Earthdata Cloud directly allows us to download only the data we need in the desired format.

(installing-gdal)=

### Installing GDAL

To use GDAL CLI commands, you must install GDAL locally. The process for installing GDAL differs based on the operating system installed on your computer, or the compute environment in which you wish to run the exported GDAL snippets.

#### Windows

The recommended method of installing GDAL on Windows is to install [QGIS](https://qgis.org/) and utilize the [OSGeo4W Shell](https://www.osgeo.org/projects/osgeo4w/), which provides GDAL.

#### MacOS

Install GDAL on MacOS with the [Homebrew package manager](https://brew.sh/). If you do not have Homebrew installed, first run the following command to install Homebrew:

```{code} bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then, install GDAL by running the following command:

```{code} bash
brew install gdal
```

#### Linux

Install GDAL using your distribution's package manager. On Debian or Ubuntu systems run the following command:

```{code} bash
sudo apt install gdal-bin
```

### Preparing GDAL to Access EDC

In this guide, we will be streaming products directly from NASA's [Earthdata Cloud (EDC)](https://www.earthdata.nasa.gov/about/earthdata-cloud-evolution) without downloading them first. To do so, we must allow GDAL to authenticate to EDC by placing a `.netrc` file in the home directory of our compute environment containing our [Earthdata Login](#earthdata-login) credentials.

::::{tab-set}
:::{tab-item} Unix Shell
:sync: unix

```{code-block} plaintext
:filename: ~/.netrc

machine urs.earthdata.nasa.gov
    login <username>
    password <password>
```

:::
:::{tab-item} Windows OSGeo4W
:sync: windows

```{code-block} plaintext
:filename: C:/Users/<YOUR WINDOWS USERNAME>/.netrc

machine urs.earthdata.nasa.gov
    login <username>
    password <password>
```

:::
::::

### Using a `gdalrc` File

Unix/Linux users can choose to generate a `gdalrc` file to simplify GDAL commands. This replaces the need to include `--config` flags for each command.

Create a file in `~/.gdal/gdalrc` with the following content:

```{code-block} ini
:filename: ~/.gdal/gdalrc

[configoptions]
CPL_VSIL_CURL_CHUNK_SIZE=2097152
CPL_VSIL_CURL_CACHE_SIZE=67108864
GDAL_CACHEMAX=64000000
GDAL_DISABLE_READDIR_ON_OPEN=TRUE
GDAL_HTTP_MERGE_CONSECUTIVE_RANGES=YES
GDAL_HTTP_MULTIPLEX=YES
GDAL_NUM_THREADS=ALL_CPUS
CPL_VSIL_CURL_CACHE_SIZE=1GB
GDAL_HTTP_NETRC=YES
GDAL_HTTP_COOKIEFILE=/tmp/gdal_cookies.txt
GDAL_HTTP_COOKIEJAR=/tmp/gdal_cookies.txt
```

If you have a `gdalrc` file staged, you can skip all the `--config` flags included in the sample commands on this page.

## Transform NISAR HDF5 Products

:::{warning} NISAR HDF5 format not supported in GDAL HDF5 drivers prior to version 3.13.0
For GDAL releases older than `3.13.0`, the `NETCDF` driver must be used instead of the default `HDF5` driver when working with NISAR products. Because NISAR encodes the spatial reference system using netCDF CF conventions, older HDF5 drivers cannot find the geospatial information required to project the data onto a map.

**Users can direct older versions of GDAL to use the netCDF driver by prepending `NETCDF:` to `/vsicurl/` in all GDAL commands.**

To identify your currently installed version of GDAL, run `gdal --version`.
:::

Users can transform NISAR data by using the [`gdal_translate`](https://gdal.org/en/stable/programs/gdal_translate.html) or [`gdalwarp`](https://gdal.org/en/stable/programs/gdalwarp.html) utility to [extract](#gdal-extract) and/or [spatially subset](#gdal-spatial-subset) data, [reproject](#gdal-spatial-reproject) the data, and change the file format. For the examples provided here, we will output the data as a GeoTIFF.

You will need the download link for a NISAR product to run these commands. Use the [Copy URL](#copy-download-url-image) links available in the search results for [Vertex](#vertex-overview), or use one of the other [available search methods](#nisar-access-overview) to find a NISAR product URL. Users can also leverage [Vertex's GDAL Snippet Exporter tool](#vertex-gdal-snippet-exporter) to generate GDAL commands.

```{figure} ../assets/copy-download-url.png
:label: copy-download-url-image
:alt: Screenshot of the Copy URL link for a NISAR product in Vertex.
:align: left
:width: 50%

Click the Copy URL link to get the download URL for a NISAR product in Vertex.
```

(gdal-extract)=

### Extract Datasets

Run the following [`gdalinfo`](https://gdal.org/en/stable/programs/gdalinfo.html) command, using the download URL for a NISAR product, to view information about the product, including the datasets it contains:

::::{tab-set}
:::{tab-item} Unix Shell
:sync: unix

```{code} bash
gdalinfo "/vsicurl/https://<DOWNLOAD URL>" \
         --config GDAL_HTTP_NETRC=YES \
         --config GDAL_HTTP_COOKIEFILE=/tmp/gdal_cookies.txt \
         --config GDAL_HTTP_COOKIEJAR=/tmp/gdal_cookies.txt
```

:::
:::{tab-item} Windows OSGeo4W
:sync: windows

```{code} bash
gdalinfo "/vsicurl/https://<DOWNLOAD URL>" ^
         --config GDAL_HTTP_NETRC=YES ^
         --config GDAL_HTTP_COOKIEFILE=%TEMP%/gdal_cookies.txt ^
         --config GDAL_HTTP_COOKIEJAR=%TEMP%/gdal_cookies.txt
```

:::
::::

Refer to the [Data Products](#data-products-overview) section for more information about the datasets included in NISAR products.

Utilize the following `gdal_translate` command to extract a specific dataset from an HDF5 product as a GeoTIFF:

::::{tab-set}
:::{tab-item} Unix Shell
:sync: unix

```{code} bash
gdal_translate -of GTiff \
                "/vsicurl/https://<DOWNLOAD URL>":<VARIABLE PATH> <OUTPUT FILE>.tif \
                --config CPL_VSIL_CURL_CHUNK_SIZE 2097152 \
                --config CPL_VSIL_CURL_CACHE_SIZE 67108864 \
                --config GDAL_CACHEMAX 64000000 \
                --config GDAL_DISABLE_READDIR_ON_OPEN=TRUE \
                --config GDAL_HTTP_MERGE_CONSECUTIVE_RANGES=YES \
                --config GDAL_HTTP_MULTIPLEX=YES \
                --config GDAL_NUM_THREADS=ALL_CPUS \
                --config CPL_VSIL_CURL_CACHE_SIZE=1GB \
                --config GDAL_HTTP_NETRC=YES \
                --config GDAL_HTTP_COOKIEFILE=/tmp/gdal_cookies.txt \
                --config GDAL_HTTP_COOKIEJAR=/tmp/gdal_cookies.txt
```

:::
:::{tab-item} Windows OSGeo4W
:sync: windows

```{code} bash
gdal_translate -of GTiff ^
                "/vsicurl/https://<DOWNLOAD URL>":<VARIABLE PATH> <OUTPUT FILE>.tif ^
                --config CPL_VSIL_CURL_CHUNK_SIZE 2097152 ^
                --config CPL_VSIL_CURL_CACHE_SIZE 67108864 ^
                --config GDAL_CACHEMAX 64000000 ^
                --config GDAL_DISABLE_READDIR_ON_OPEN=TRUE ^
                --config GDAL_HTTP_MERGE_CONSECUTIVE_RANGES=YES ^
                --config GDAL_HTTP_MULTIPLEX=YES ^
                --config GDAL_NUM_THREADS=ALL_CPUS ^
                --config CPL_VSIL_CURL_CACHE_SIZE=1GB ^
                --config GDAL_HTTP_NETRC=YES ^
                --config GDAL_HTTP_COOKIEFILE=%TEMP%/gdal_cookies.txt ^
                --config GDAL_HTTP_COOKIEJAR=%TEMP%/gdal_cookies.txt
```

:::
::::

The `gdalwarp` command is also suitable for this, and can be used as a drop-in replacement. However, using `gdal_translate` for simple dataset extraction operations may provide up to a 30% improvement in performance.

:::::{hint} Example
First, we will use `gdalinfo` to fetch information about the NISAR [GCOV](#gcov-product-overview) product used in this example:

```{code} bash
gdalinfo "/vsicurl/https://nisar.asf.earthdatacloud.nasa.gov/NISAR/NISAR_L2_GCOV_BETA_V1/NISAR_L2_PR_GCOV_005_149_A_024_4005_DHDH_A_20251120T123755_20251120T123830_X05009_N_F_J_001/NISAR_L2_PR_GCOV_005_149_A_024_4005_DHDH_A_20251120T123755_20251120T123830_X05009_N_F_J_001.h5"
```

This command returns a lot of information about the product, including the name and description for each dataset (or subdataset) contained in the HDF5 file.

Let's look at the information about the first subdataset:

```{code} plaintext
SUBDATASET_1_NAME=HDF5:"/vsicurl/https://nisar.asf.earthdatacloud.nasa.gov/NISAR/NISAR_L2_GCOV_BETA_V1/NISAR_L2_PR_GCOV_005_149_A_024_4005_DHDH_A_20251120T123755_20251120T123830_X05009_N_F_J_001/NISAR_L2_PR_GCOV_005_149_A_024_4005_DHDH_A_20251120T123755_20251120T123830_X05009_N_F_J_001.h5"://science/LSAR/GCOV/grids/frequencyA/HHHH
SUBDATASET_1_DESC=[35928x36288] //science/LSAR/GCOV/grids/frequencyA/HHHH (32-bit floating-point)
```

We can garner a number of important details from this information:

- The path of this dataset is `/science/LSAR/GCOV/grids/frequencyA/HHHH`, as specified by the second field of the `SUBDATASET_1_DESC` variable on the second line.
  - This dataset is the [Frequency A HHHH covariance dataset](#gcov-covariance-terms) (HH polarization) of the GCOV product which we are using for our example.
- The first and third field of the `SUBDATASET_1_DESC` variable specifies that the resolution of the dataset is 35928 by 36288 pixels with the type of 32-bit floating point.
- The `SUBDATASET_1_NAME` variable provides the full string which we can utilize in a `gdal_translate` command.

The following `gdal_translate` command references the `SUBDATASET_1_NAME` string to form a command which outputs our chosen dataset as a GeoTIFF named `output.tif

::::{tab-set}
:::{tab-item} Unix Shell
:sync: unix

```{code} bash
gdal_translate -of GTiff \
                "/vsicurl/https://nisar.asf.earthdatacloud.nasa.gov/NISAR/NISAR_L2_GCOV_BETA_V1/NISAR_L2_PR_GCOV_005_149_A_024_4005_DHDH_A_20251120T123755_20251120T123830_X05009_N_F_J_001/NISAR_L2_PR_GCOV_005_149_A_024_4005_DHDH_A_20251120T123755_20251120T123830_X05009_N_F_J_001.h5"://science/LSAR/GCOV/grids/frequencyA/HHHH output.tif \
                --config CPL_VSIL_CURL_CHUNK_SIZE 2097152 \
                --config CPL_VSIL_CURL_CACHE_SIZE 67108864 \
                --config GDAL_CACHEMAX 64000000 \
                --config GDAL_DISABLE_READDIR_ON_OPEN=TRUE \
                --config GDAL_HTTP_MERGE_CONSECUTIVE_RANGES=YES \
                --config GDAL_HTTP_MULTIPLEX=YES \
                --config GDAL_NUM_THREADS=ALL_CPUS \
                --config CPL_VSIL_CURL_CACHE_SIZE=1GB \
                --config GDAL_HTTP_NETRC=YES \
                --config GDAL_HTTP_COOKIEFILE=/tmp/gdal_cookies.txt \
                --config GDAL_HTTP_COOKIEJAR=/tmp/gdal_cookies.txt
```

:::
:::{tab-item} Windows OSGeo4W
:sync: windows

```{code} bash
gdal_translate -of GTiff ^
                "/vsicurl/https://nisar.asf.earthdatacloud.nasa.gov/NISAR/NISAR_L2_GCOV_BETA_V1/NISAR_L2_PR_GCOV_005_149_A_024_4005_DHDH_A_20251120T123755_20251120T123830_X05009_N_F_J_001/NISAR_L2_PR_GCOV_005_149_A_024_4005_DHDH_A_20251120T123755_20251120T123830_X05009_N_F_J_001.h5"://science/LSAR/GCOV/grids/frequencyA/HHHH output.tif ^
                --config CPL_VSIL_CURL_CHUNK_SIZE 2097152 ^
                --config CPL_VSIL_CURL_CACHE_SIZE 67108864 ^
                --config GDAL_CACHEMAX 64000000 ^
                --config GDAL_DISABLE_READDIR_ON_OPEN=TRUE ^
                --config GDAL_HTTP_MERGE_CONSECUTIVE_RANGES=YES ^
                --config GDAL_HTTP_MULTIPLEX=YES ^
                --config GDAL_NUM_THREADS=ALL_CPUS ^
                --config CPL_VSIL_CURL_CACHE_SIZE=1GB ^
                --config GDAL_HTTP_NETRC=YES ^
                --config GDAL_HTTP_COOKIEFILE=%TEMP%/gdal_cookies.txt ^
                --config GDAL_HTTP_COOKIEJAR=%TEMP%/gdal_cookies.txt
```

:::
::::

To extract other datasets, use the subdataset name displayed in the `gdalinfo` output for the desired dataset.
:::::

(gdal-spatial-subset)=

### Spatial Subsetting

GDAL has many utilities which allow for spatial subsetting. In this section we will demonstrate spatial subsetting through the use of the `gdalwarp` utility with WKT spatial extent strings.

The `gdalwarp` utility allows describing spatial extents using a type of string known as a Well Known Text (WKT) Polygon or MultiPolygon string (we will refer to them as WKT spatial extent strings), which are utilized widely across geospatial applications (see [examples of WKT formulation](https://en.wikipedia.org/wiki/Well-known_text_representation_of_geometry)).

(vertex-wkt)=
An easy method for defining a WKT spatial extent string is to set an Area of Interest (AOI) in [Vertex](#vertex-geographic-extent). Once you've drawn an AOI in Vertex, the [Area of Interest WKT field](#vertex-wkt-image) displays the WKT spatial extent string, and hovering over the field exposes a copy icon that you can use to capture the WKT.

```{figure} ../assets/vertex-copy-aoi-string.png
:label: vertex-wkt-image
:alt: A screenshot describing the location of the copy AOI string button in Vertex.
:align: center

Click the **Copy to clipboard** icon in the Area of Interest WKT field in Vertex to copy the WKT spatial extent string to your system's clipboard.
```

:::{tip}
Both `gdal_translate` and `gdalwarp` can be used for spatial subsetting, but the `gdalwarp` utility is more flexible, allowing for the use of WKT spatial extent strings to define an AOI. The `gdal_translate` utility is more efficient, but does not support the use of such strings.

If you are interested in maximizing performance by using `gdal_translate`, leverage the `-projwin` and `-projwin_srs` flags as described in the [`gdal_translate` documentation](https://gdal.org/en/stable/programs/gdal_translate.html#cmdoption-gdal_translate-projwin) to set the AOI and output projection.
:::

To perform spatial subsetting with `gdalwarp`, utilize the `-cutline <WKT>` flag alongside the `-cutline_srs WGS84`, `-crop_to_cutline`, and `-dstalpha` flags.

The command below demonstrates the use of these flags:

::::{tab-set}
:::{tab-item} Unix Shell
:sync: unix

```{code} bash
gdalwarp -of GTiff \
         "/vsicurl/https://<DOWNLOAD URL>":<VARIABLE PATH> <OUTPUT FILE>.tif \
         -cutline <WKT> \
         -cutline_srs WGS84 \
         -crop_to_cutline \
         -dstalpha \
         --config CPL_VSIL_CURL_CHUNK_SIZE 2097152 \
         --config CPL_VSIL_CURL_CACHE_SIZE 67108864 \
         --config GDAL_CACHEMAX 64000000 \
         --config GDAL_DISABLE_READDIR_ON_OPEN=TRUE \
         --config GDAL_HTTP_MERGE_CONSECUTIVE_RANGES=YES \
         --config GDAL_HTTP_MULTIPLEX=YES \
         --config GDAL_NUM_THREADS=ALL_CPUS \
         --config CPL_VSIL_CURL_CACHE_SIZE=1GB \
         --config GDAL_HTTP_NETRC=YES \
         --config GDAL_HTTP_COOKIEFILE=/tmp/gdal_cookies.txt \
         --config GDAL_HTTP_COOKIEJAR=/tmp/gdal_cookies.txt
```

:::
:::{tab-item} Windows OSGeo4W
:sync: windows

```{code} bash
gdalwarp -of GTiff ^
         "/vsicurl/https://<DOWNLOAD URL>":<VARIABLE PATH> <OUTPUT FILE>.tif ^
         -cutline <WKT> ^
         -cutline_srs WGS84 ^
         -crop_to_cutline ^
         -dstalpha ^
         --config CPL_VSIL_CURL_CHUNK_SIZE 2097152 ^
         --config CPL_VSIL_CURL_CACHE_SIZE 67108864 ^
         --config GDAL_CACHEMAX 64000000 ^
         --config GDAL_DISABLE_READDIR_ON_OPEN=TRUE ^
         --config GDAL_HTTP_MERGE_CONSECUTIVE_RANGES=YES ^
         --config GDAL_HTTP_MULTIPLEX=YES ^
         --config GDAL_NUM_THREADS=ALL_CPUS ^
         --config CPL_VSIL_CURL_CACHE_SIZE=1GB ^
         --config GDAL_HTTP_NETRC=YES ^
         --config GDAL_HTTP_COOKIEFILE=%TEMP%/gdal_cookies.txt ^
         --config GDAL_HTTP_COOKIEJAR=%TEMP%/gdal_cookies.txt
```

:::
::::

:::::{hint} Example
In this example, we will use the `gdalwarp` utility to perform spatial subsetting on the subdataset identified in the previous example.

We used Vertex to pick an area within our product and [copied the AOI string](#vertex-wkt), which is in a suitable WKT spatial extent string format:

```{code} plaintext
POLYGON((-115.7994 43.887,-113.7599 43.887,-113.7599 44.9751,-115.7994 44.9751,-115.7994 43.887))
```

We will then input this string and the full dataset string identified in the previous example into the spatial subsetting snippet provided above.

This gives us the final command, which we can utilize to perform our spatial subsetting operation:

::::{tab-set}
:::{tab-item} Unix Shell
:sync: unix

```{code} bash
gdalwarp -of GTiff \
         "/vsicurl/https://nisar.asf.earthdatacloud.nasa.gov/NISAR/NISAR_L2_GCOV_BETA_V1/NISAR_L2_PR_GCOV_005_149_A_024_4005_DHDH_A_20251120T123755_20251120T123830_X05009_N_F_J_001/NISAR_L2_PR_GCOV_005_149_A_024_4005_DHDH_A_20251120T123755_20251120T123830_X05009_N_F_J_001.h5"://science/LSAR/GCOV/grids/frequencyA/HHHH output.tif \
         -cutline "POLYGON((-115.7994 43.887,-113.7599 43.887,-113.7599 44.9751,-115.7994 44.9751,-115.7994 43.887))" \
         -cutline_srs WGS84 \
         -crop_to_cutline \
         -dstalpha \
         --config CPL_VSIL_CURL_CHUNK_SIZE 2097152 \
         --config CPL_VSIL_CURL_CACHE_SIZE 67108864 \
         --config GDAL_CACHEMAX 64000000 \
         --config GDAL_DISABLE_READDIR_ON_OPEN=TRUE \
         --config GDAL_HTTP_MERGE_CONSECUTIVE_RANGES=YES \
         --config GDAL_HTTP_MULTIPLEX=YES \
         --config GDAL_NUM_THREADS=ALL_CPUS \
         --config CPL_VSIL_CURL_CACHE_SIZE=1GB \
         --config GDAL_HTTP_NETRC=YES \
         --config GDAL_HTTP_COOKIEFILE=/tmp/gdal_cookies.txt \
         --config GDAL_HTTP_COOKIEJAR=/tmp/gdal_cookies.txt
```

:::
:::{tab-item} Windows OSGeo4W
:sync: windows

```{code} bash
gdalwarp -of GTiff ^
         "/vsicurl/https://nisar.asf.earthdatacloud.nasa.gov/NISAR/NISAR_L2_GCOV_BETA_V1/NISAR_L2_PR_GCOV_005_149_A_024_4005_DHDH_A_20251120T123755_20251120T123830_X05009_N_F_J_001/NISAR_L2_PR_GCOV_005_149_A_024_4005_DHDH_A_20251120T123755_20251120T123830_X05009_N_F_J_001.h5"://science/LSAR/GCOV/grids/frequencyA/HHHH output.tif ^
         -cutline "POLYGON((-115.7994 43.887,-113.7599 43.887,-113.7599 44.9751,-115.7994 44.9751,-115.7994 43.887))" ^
         -cutline_srs WGS84 ^
         -crop_to_cutline ^
         -dstalpha ^
         --config CPL_VSIL_CURL_CHUNK_SIZE 2097152 ^
         --config CPL_VSIL_CURL_CACHE_SIZE 67108864 ^
         --config GDAL_CACHEMAX 64000000 ^
         --config GDAL_DISABLE_READDIR_ON_OPEN=TRUE ^
         --config GDAL_HTTP_MERGE_CONSECUTIVE_RANGES=YES ^
         --config GDAL_HTTP_MULTIPLEX=YES ^
         --config GDAL_NUM_THREADS=ALL_CPUS ^
         --config CPL_VSIL_CURL_CACHE_SIZE=1GB ^
         --config GDAL_HTTP_NETRC=YES ^
         --config GDAL_HTTP_COOKIEFILE=%TEMP%/gdal_cookies.txt ^
         --config GDAL_HTTP_COOKIEJAR=%TEMP%/gdal_cookies.txt
```

:::
::::

:::::

(gdal-spatial-reproject)=

### Reprojection

The `gdalwarp` utility can also be used to reproject datasets from the [projection used for the source NISAR HDF5 product](#nisar-l2-projections) to a different spatial reference system.

In your `gdalwarp` command, set the `-t_srs <SRS>` flag, where `<SRS>` is the [EPSG code](https://epsg.io/) for the desired output spatial reference system (such as `EPSG:3857` for Web Mercator):

::::{tab-set}
:::{tab-item} Unix Shell
:sync: unix

```{code} bash
gdalwarp -of GTiff \
         "/vsicurl/https://<DOWNLOAD URL>":<VARIABLE PATH> <OUTPUT FILE>.tif \
         -t_srs <SRS> \
         -dstalpha \
         --config CPL_VSIL_CURL_CHUNK_SIZE 2097152 \
         --config CPL_VSIL_CURL_CACHE_SIZE 67108864 \
         --config GDAL_CACHEMAX 64000000 \
         --config GDAL_DISABLE_READDIR_ON_OPEN=TRUE \
         --config GDAL_HTTP_MERGE_CONSECUTIVE_RANGES=YES \
         --config GDAL_HTTP_MULTIPLEX=YES \
         --config GDAL_NUM_THREADS=ALL_CPUS \
         --config CPL_VSIL_CURL_CACHE_SIZE=1GB \
         --config GDAL_HTTP_NETRC=YES \
         --config GDAL_HTTP_COOKIEFILE=/tmp/gdal_cookies.txt \
         --config GDAL_HTTP_COOKIEJAR=/tmp/gdal_cookies.txt
```

:::
:::{tab-item} Windows OSGeo4W
:sync: windows

```{code} bash
gdalwarp -of GTiff ^
         "/vsicurl/https://<DOWNLOAD URL>":<VARIABLE PATH> <OUTPUT FILE>.tif ^
         -t_srs <SRS> ^
         -dstalpha ^
         --config CPL_VSIL_CURL_CHUNK_SIZE 2097152 ^
         --config CPL_VSIL_CURL_CACHE_SIZE 67108864 ^
         --config GDAL_CACHEMAX 64000000 ^
         --config GDAL_DISABLE_READDIR_ON_OPEN=TRUE ^
         --config GDAL_HTTP_MERGE_CONSECUTIVE_RANGES=YES ^
         --config GDAL_HTTP_MULTIPLEX=YES ^
         --config GDAL_NUM_THREADS=ALL_CPUS ^
         --config CPL_VSIL_CURL_CACHE_SIZE=1GB ^
         --config GDAL_HTTP_NETRC=YES ^
         --config GDAL_HTTP_COOKIEFILE=%TEMP%/gdal_cookies.txt ^
         --config GDAL_HTTP_COOKIEJAR=%TEMP%/gdal_cookies.txt
```

:::
::::

:::::{hint} Example
We can utilize this snippet to project the product used in our previous examples into Web Mercator as follows:

::::{tab-set}
:::{tab-item} Unix Shell
:sync: unix

```{code} bash
gdalwarp -of GTiff \
         "/vsicurl/https://nisar.asf.earthdatacloud.nasa.gov/NISAR/NISAR_L2_GCOV_BETA_V1/NISAR_L2_PR_GCOV_005_149_A_024_4005_DHDH_A_20251120T123755_20251120T123830_X05009_N_F_J_001/NISAR_L2_PR_GCOV_005_149_A_024_4005_DHDH_A_20251120T123755_20251120T123830_X05009_N_F_J_001.h5"://science/LSAR/GCOV/grids/frequencyA/HHHH output.tif \
         -t_srs EPSG:3857 \
         -dstalpha \
         --config CPL_VSIL_CURL_CHUNK_SIZE 2097152 \
         --config CPL_VSIL_CURL_CACHE_SIZE 67108864 \
         --config GDAL_CACHEMAX 64000000 \
         --config GDAL_DISABLE_READDIR_ON_OPEN=TRUE \
         --config GDAL_HTTP_MERGE_CONSECUTIVE_RANGES=YES \
         --config GDAL_HTTP_MULTIPLEX=YES \
         --config GDAL_NUM_THREADS=ALL_CPUS \
         --config CPL_VSIL_CURL_CACHE_SIZE=1GB \
         --config GDAL_HTTP_NETRC=YES \
         --config GDAL_HTTP_COOKIEFILE=/tmp/gdal_cookies.txt \
         --config GDAL_HTTP_COOKIEJAR=/tmp/gdal_cookies.txt
```

:::
:::{tab-item} Windows OSGeo4W
:sync: windows

```{code} bash
gdalwarp -of GTiff ^
         "/vsicurl/https://nisar.asf.earthdatacloud.nasa.gov/NISAR/NISAR_L2_GCOV_BETA_V1/NISAR_L2_PR_GCOV_005_149_A_024_4005_DHDH_A_20251120T123755_20251120T123830_X05009_N_F_J_001/NISAR_L2_PR_GCOV_005_149_A_024_4005_DHDH_A_20251120T123755_20251120T123830_X05009_N_F_J_001.h5"://science/LSAR/GCOV/grids/frequencyA/HHHH output.tif ^
         -t_srs EPSG:3857 ^
         -dstalpha ^
         --config CPL_VSIL_CURL_CHUNK_SIZE 2097152 ^
         --config CPL_VSIL_CURL_CACHE_SIZE 67108864 ^
         --config GDAL_CACHEMAX 64000000 ^
         --config GDAL_DISABLE_READDIR_ON_OPEN=TRUE ^
         --config GDAL_HTTP_MERGE_CONSECUTIVE_RANGES=YES ^
         --config GDAL_HTTP_MULTIPLEX=YES ^
         --config GDAL_NUM_THREADS=ALL_CPUS ^
         --config CPL_VSIL_CURL_CACHE_SIZE=1GB ^
         --config GDAL_HTTP_NETRC=YES ^
         --config GDAL_HTTP_COOKIEFILE=%TEMP%/gdal_cookies.txt ^
         --config GDAL_HTTP_COOKIEJAR=%TEMP%/gdal_cookies.txt
```

:::
::::

:::::

(jpl-nisar-hdf5-gdal-plugin)=
## JPL's NISAR HDF5 GDAL Plugin

JPL developed a GDAL plugin that provides streaming capabilities and block-optimized reading for NISAR HDF5 products. While it has not yet been integrated into the mail GDAL distribution, Unix users can install it as a plugin. Installation on Windows operating systems is not yet supported. 

The NISAR HDF5 GDAL Plugin provides substantial performance improvements over using the standard GDAL CLI when extracting datasets from cloud-hosted NISAR HDF5 files. It also provides a range of NISAR-specific functionality, including the ability to read single pixel values, view the full HDF5 structure, or apply a validity mask to an extracted dataset.

- [Learn more about the plugin](https://github.com/ozzp-jpl/nisar-hdf5-gdalplugin/blob/main/docs/HOWTO.md)
- [Access the plugin](https://anaconda.org/channels/nisar-forge/packages/gdal-driver-nisar/overview) 

### NISAR HDF5 GDAL Plugin in Vertex

The [GDAL Snippet Exporter in Vertex](#vertex-gdal-snippet-exporter) generates code snippets that can be used in the GDAL CLI to extract datasets from NISAR products and apply transformations (spatial subsetting, reprojection) as they are being downloaded. The GDAL Snippet Exporter interface provides an option to use JPL's NISAR HDF5 GDAL Plugin rather than the standard GDAL CLI.

To generate code snippets for use with the NISAR HDF5 GDAL Plugin rather than the standard GDAL CLI: 

- You must be using a Unix-based operating system. If you select Windows as your operating system in the GDAL Snippet Exporter interface, the option to use JPL's NISAR HDF5 GDAL Plugin will not be available. 
- The NISAR HDF5 GDAL Plugin must be installed on your computer before you can run the GDAL code snippets. If you select the JPL GDAL Plugin option in the GDAL Snippet Exporter interface, installation commands are provided for a range of package management systems.
