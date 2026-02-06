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
For a description of NISAR's data product types, see @data-products-overview.

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

Downloading (or streaming) NISAR data requires logging in with your [Earthdata Login (EDL)](https://urs.earthdata.nasa.gov/) account. An EDL account is free to create and provides unified access to Earth science data distributed by [NASA'S Earth Observation System Data and Information System (EOSDIS)](https://www.earthdata.nasa.gov/about/esdis/eosdis), independent of the data provider.

Use the `earthaccess.login` method to log in. By default, this will look for a `.netrc`, then for environment variables, and finally prompt you to enter your username and password. For more details and alternatives, please see the `earthaccess` [Authentication guide](https://earthaccess.readthedocs.io/en/stable/user_guide/authenticate/).

Once logged in, you can download products from your search results:
```python
auth = earthaccess.login()

files = earthaccess.download(results, local_path='.')
```
