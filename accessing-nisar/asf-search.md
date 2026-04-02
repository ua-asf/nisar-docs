---
short_title: ASF Search Python Package
---
# Finding NISAR Data with ASF Search

(asf-search-package)=
## ASF Search Python Package

ASF's [`asf_search`](https://pypi.org/project/asf-search/) Python package enables quick and customizable programmatic access to NISAR data. 

## ASF Search Version
The `asf_search` package is always under development to add functionality in support of new platforms and products, to manage dependencies, and to comply with security best practices. In particular, NISAR support in `asf_search` will be evolving as more data products are added to the archive and preferred search patterns emerge. 

As such, we recommend using the latest release of the package whenever possible. You can update your installation of `asf_search` via `pip` with:
```
python -m pip install --upgrade asf_search
```
or via `conda` with:
```
conda update asf_search
```
<!-- TODO: Add in minimum asf_search version that allows for NISAR searches -->

## Search for NISAR Data

To quickly begin exploring NISAR data, search by setting the `dataset` parameter to `'NISAR'` and the `processingLevel` parameter to the four-letter acronym corresponding to your desired product. For example, to search for NISAR GCOV products, use the following Python code:
```python
import asf_search as asf

results = asf.search(dataset='NISAR', processingLevel='GCOV')
``` 
A list of accepted `processingLevel` constants for data from all missions hosted by ASF, including NISAR, is available [here](https://github.com/asfadmin/Discovery-asf_search/blob/master/asf_search/constants/PRODUCT_TYPE.py). 

Refer to the [Searching page of the ASF Data Search Manual](https://docs.asf.alaska.edu/asf_search/searching/)
 for more details on available search filters and their possible values.

## Download data

Downloading NISAR data requires authentication through [Earthdata Login (EDL)](https://urs.earthdata.nasa.gov/). For more information, see @earthdata-login. 

EDL credentials can be provided to `asf_search` using the `ASFSession` class. After creating an authenticated `ASFSession`, pass the session object to the download function along with the target directory path where the data will be saved:
```python 
session = asf.ASFSession().auth_with_creds('username', 'password')
results.download(path='path/to/data/', session=session) 
```
Alternatively, users may [configure a local `.netrc` file](https://nsidc.org/data/user-resources/help-center/creating-netrc-file-earthdata-login) to store their EDL credentials. Once the `.netrc` file is properly set up, downloads can be performed without explicitly passing credentials:
```python
results.download(path='path/to/data/')
```

## Stream data

NISAR data can be streamed into memory using `asf_search` combined with other libraries such as `fsspec` and `xarray`. This allows specific data from a NISAR product to be accessed without downloading the entire data file.

Like all data access, streaming requires an [EDL account](https://urs.earthdata.nasa.gov/).

### Example: Stream via HTTPS

This example uses streaming to retrieve a specific byte of information from a 30 GB RSLC product.

Run the following command to install the required Python packages:
```
conda install aiohttp asf_search fsspec h5netcdf xarray
```

`asf_search` is used to retrieve an HTTPS access url, then the data is opened with [`fsspec`](https://filesystem-spec.readthedocs.io/en/latest/) and [`xarray`](https://docs.xarray.dev/en/stable/) using the `h5netcdf` engine.

```python
import aiohttp
import asf_search as asf
import fsspec
import xarray as xr

results = asf.search(
    dataset='NISAR',
    granule_list=['NISAR_L1_PR_RSLC_004_122_D_067_4005_DHDH_A_20251106T160541_20251106T160622_X05009_N_F_J_001'],
)
access_url = results[0].get_urls()[0]

fs = fsspec.filesystem(protocol='https', client_kwargs={'auth': aiohttp.BasicAuth('username', 'password')})

ds = xr.open_datatree(
    fs.open(
        path=access_url,
        cache_type='background',
        block_size=16*1024*1024,  # 16 MB
    ),
    engine='h5netcdf',
    decode_timedelta=False,
    phony_dims='access',
)

print(ds.science.LSAR.identification.isDithered.values)
```
