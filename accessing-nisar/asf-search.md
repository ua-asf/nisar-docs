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

* stream data into memory
* typically served to users through HTTPS CloudFront URLs
* hosted on us-west-2
* Access from a resource in the same region (us-west-2)
* Stream data through https or S3 protocols

### Example: Stream via HTTPS
* similar to downloading data, streaming requires entering your EDL credentials using a Bearer Token
* This example searches for a single RSLC product. 
* Retrieves its HTTPS access url, sets a fsspec configuration, and opens with xarray using the h5netcdf engine. 
* If not already installed, Might need to install h5netcdf and aiohttp to run
```python
import asf_search as asf
import fsspec
import xarray as xr

results = asf.search(dataset='NISAR', processingLevel='RSLC', maxResults=1)

token = ... # Requires Earthdata Login Bearer Token :https://urs.earthdata.nasa.gov/documentation/for_users/user_token
fs = fsspec.filesystem('https', client_kwargs={'headers': {'Authorization': f'Bearer {token}'}, 'trust_env': False})

fsspec_config = {
    'cache_type': 'background',
    'block_size': 16*1024*1024,  # 16 MB
}

ds = xr.open_datatree(
    fs.open(results[0].get_urls()[0], **fsspec_config),
    engine='h5netcdf',
    decode_timedelta=False,
    phony_dims='access',
)

print(ds.science.LSAR.identification.isDithered.values) 
```

### Example: Stream via S3

* Prior to running, get the S3 credentials and export. Ensure you run the code within 60 minutes of obtaining the credentials
* Ensure s3fs and h5netcdf are installed
* Ensure the s3 link is a h5 file

```python 
import asf_search as asf
import s3fs
import xarray as xr

results = asf.search(dataset='NISAR', processingLevel='RSLC', maxResults=1)

s3_links = results[0].properties["s3Urls"]
s3_h5_link = [link for link in s3_links if link.endswith(f'{results[0].properties["sceneName"]}.h5')]

fsspec_config = {
    'cache_type': 'background',
    'block_size': 16*1024*1024,  # 16 MB
}

s3 = s3fs.S3FileSystem(anon=False)
ds = xr.open_datatree(
   s3.open(s3_h5_link[0], **fsspec_config),
   engine='h5netcdf',
   decode_timedelta=False,
   phony_dims="access"
)
```