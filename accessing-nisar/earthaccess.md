---
short_title: Earthaccess Python Package
---
# Finding NISAR Data with Earthaccess

(earthaccess-package)=
## Earthaccess Python Package

[`earthaccess`](https://earthaccess.readthedocs.io/en/stable/) is a Python library to **search for** and **download** or **stream** NASA Earth science data with just a few lines of code.

## Install

The latest release of `earthaccess` can be installed via `pip`:

```shell
python -m pip install earthaccess
```

or via `conda`:
```shell
conda install -c conda-forge earthaccess
```

`earthaccess` is a highly active, open-source, and community-driven library. As such, we recommend using the latest release of the package whenever possible. You can update your installation of `earthaccess` via `pip` with:
```
python -m pip install --upgrade earthaccess
```
or via `conda` with:
```
conda update earthaccess
```

## Search for NISAR data

To search for a specific product type, provide the corresponding short name from @tbl:earthaccess-search-shortname-list as the `short_name` parameter. For example, to find a single [GCOV](#gcov-product-overview) product, use the following Python code:

```python
import earthaccess

results = earthaccess.search_data(
    short_name='NISAR_L2_GCOV_BETA_V1',
    count=1
)
```
For a description of NISAR's data product types, see @data-products-overview. You can also refine your search by setting time bounds using the [`temporal=`](https://earthaccess.readthedocs.io/en/stable/user_guide/search/#search-for-datasets-or-data-by-time-range) parameter, or by providing an area or region of interest [geometry](https://earthaccess.readthedocs.io/en/stable/user_guide/search/#search-for-datasets-or-data-using-a-region-of-interest).

:::{table} NISAR Data Collection Short Name List
:label: tbl:earthaccess-search-shortname-list

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

## Download NISAR data

Downloading (or streaming) NISAR data requires logging in with your [Earthdata Login (EDL)](https://urs.earthdata.nasa.gov/) account. To learn more about EDL, see @earthdata-login.

Use the `earthaccess.login` method to log in. By default, this will look for a `.netrc`, then for environment variables, and finally prompt you to enter your username and password. For more details and alternatives, please see the `earthaccess` [Authentication guide](https://earthaccess.readthedocs.io/en/stable/user_guide/authenticate/).

Once logged in, you can download products from your search results:
```python
auth = earthaccess.login()

files = earthaccess.download(results, local_path='.')
```

## Stream NISAR data

`earthaccess` also supports streaming data into memory. NISAR data is hosted in the AWS `us-west-2` region and typically served to users through HTTPS CloudFront URLs, or if you are accessing the data from the same region (e.g., a resource in AWS `us-west-2`), you may also use AWS S3 URIs if you obtain temporary S3 access keys. You can stream data through either HTTPS or S3 protocols, but S3 will be faster and will allow you to use AWS S3-aware tools (e.g., the [AWS CLI](https://aws.amazon.com/cli/), [`boto3`](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html), or [`s3fs`](https://s3fs.readthedocs.io/en/latest/)).

Similar to downloading, streaming requires logging in with your  [Earthdata Login (EDL)](https://urs.earthdata.nasa.gov/) account. Once logged in, you can use `earthaccess.open` to create _file-like_ objects via [`fsspec`](https://filesystem-spec.readthedocs.io/en/latest/index.html), which can be used like a file path to stream data. For example:
```python
auth = earthaccess.login()

file_objects = earthaccess.open(results)
```

opens file objects for each data link in `results`. A file object can be passed to tools like [`xarray`](https://docs.xarray.dev/en/stable/) using the [h5netcdf](https://h5netcdf.org/index.html) reader:
```python
import xarray as xr

ds = xr.open_datatree(
    file_objects[0],
    engine='h5netcdf',
    decode_timedelta=False,
    phony_dims="access"
)
```

`earthaccess.open` will use sensible defaults to provide good performance across all NASA data. You can override these default to fine-tune steaming performance for your access pattern. The next two examples show how to use a specific protocol and set `fsspec` options.

### Example: Stream via HTTPS

This end-to-end example searches for a single NISAR GCOV product, retrieves its HTTPS access URL, sets a custom `fsspec` configuration, and opens it with `xarray` using the `h5netcdf` engine.

```python
import earthaccess
import xarray as xr

auth = earthaccess.login()

results = earthaccess.search_data(
    short_name='NISAR_L2_GCOV_BETA_V1',
    count=1
)

https_links = results[0].data_links(access='external')

fsspec_config = {
    'cache_type': 'background',
    'block_size': 16*1024*1024,  # 16 MB
}

fs = earthaccess.get_fsspec_https_session()
ds = xr.open_datatree(
   fs.open(https_links[0], **fsspec_config),
   engine='h5netcdf',
   decode_timedelta=False,
   phony_dims="access"
)
```

### Example: Stream via S3

This end-to-end example searches for a single NISAR GCOV product, retrieves its S3 access URI, sets a custom `fsspec` configuration, and opens it with `xarray` using the `h5netcdf` engine. Behind the scenes, `earthaccess` will request temporary AWS credentials for you, which is described in @aws-s3-access-overview.

:::{warning}Must be in AWS `us-west-2`
Direct AWS S3 access is only available for resources (e.g., EC2) in the AWS `us-west-2` region. See @s3-access-limitations for more details.
:::


```python
import earthaccess
import xarray as xr

auth = earthaccess.login()

results = earthaccess.search_data(
    short_name='NISAR_L2_GCOV_BETA_V1',
    count=1
)

s3_links = results[0].data_links(access='direct')

fsspec_config = {
    'cache_type': 'background',
    'block_size': 16*1024*1024,  # 16 MB
}

endpoint = 'https://nisar.asf.earthdatacloud.nasa.gov/s3credentials'
fs = earthaccess.get_s3_filesystem(endpoint=endpoint)
ds = xr.open_datatree(
   fs.open(s3_links[0], **fsspec_config),
   engine='h5netcdf',
   decode_timedelta=False,
   phony_dims="access"
)
```

:::{warning}`endpoint=` must be specified for NISAR
For the time being, you must specify the `endpoint=` parameter when using functions like `get_s3_filesystem` for NISAR data. Using `daac='ASF'` will result in errors when attempting to access NISAR data. See `earthaccess` issue [#1184](https://github.com/nsidc/earthaccess/issues/1184) for more details.
:::
