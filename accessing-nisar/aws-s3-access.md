# AWS S3 Access

(aws-s3-access-overview)=
## Overview

All NISAR data is hosted in [NASA's Earthdata Cloud (EDC)](https://www.earthdata.nasa.gov/about/earthdata-cloud-evolution), which leverages Amazon Web Services (AWS) infrastructure. As such, AWS Simple Storage Service (S3) access methods can be used to interact with NISAR datasets. 

Data users can request temporary AWS credentials enabling direct access to the data in S3. This supports the use of a wide range of S3-aware tooling for interacting with cloud-hosted data as well as for low-latency and high-throughput data access patterns.

## Accessing NISAR Data in S3 Using AWS CLI

(s3-creds-step-1)=
### 1. Visit https://nisar.asf.earthdatacloud.nasa.gov/s3credentials 

If prompted, sign in with your [Earthdata Login (EDL) credentials](https://urs.earthdata.nasa.gov/) to retrieve a set of temporary AWS credentials, which will allow you to list and download contents of the S3 bucket. If you are already signed in, the credentials will display immediately.

The text displayed at the site provides four pieces of information:
* AWS Access Key ID
* AWS Secret Access Key  
* AWS Session Token
* Expiration Time

For example: 
```shell
{  
 accessKeyId: "ASIAIOSFODNN7EXAMPLE",  
 secretAccessKey: "wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY",  
 sessionToken: "LONGSTRINGOFCHARACTERS...6XUxCYEwbjGVKkzSNQh/", 
 expiration: "2026-01-27 00:50:09+00:00"
}
```
   
More details about requesting temporary S3 credentials are [available here](https://nisar.asf.earthdatacloud.nasa.gov/s3credentialsREADME).

### 2. Configure your environment to use the temporary AWS credentials

You will need to set the environment variables in your terminal. 

Linux or Mac users can export their credentials using the following commands:
```shell
$ export AWS_ACCESS_KEY_ID=ASIAIOSFODNN7EXAMPLE
$ export AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
$ export AWS_SESSION_TOKEN=AQoDYXdzEJr...<remainder of session token>
```

Windows users can export their credentials using the following commands:
```shell
C:\> SET AWS_ACCESS_KEY_ID=ASIAIOSFODNN7EXAMPLE
C:\> SET AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
C:\> SET AWS_SESSION_TOKEN=AQoDYXdzEJr...<remainder of token> 
```

For a full list of exportable variables, see [AWS's Temporary Credentials User Guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_use-resources.html).

### 3. Find NISAR products of interest

NISAR data is all hosted in the `sds-n-cumulus-prod-nisar-products` S3 bucket. Each product type has a prefix, and while you cannot list the full bucket contents, you can list the contents of each prefix. Refer to @prefix-structure for more information on the organization of the NISAR bucket.

For example, if you want to see all available GCOV products, you can use this `aws s3 ls` command: 
```
aws s3 ls s3://sds-n-cumulus-prod-nisar-products/NISAR_L2_GCOV_BETA_V1/
```

Within each product type prefix, there is a nested prefix for each individual product, with no additional hierarchy for grouping the individual products. Refer to @finding-s3-paths for tools and methods available to help you find specific products of interest.

:::{warning}Direct S3 Access only available within us-west-2
If you encounter an `Access Denied` error, check to make sure you are in the correct region. Direct S3 access is only available within us-west-2. See @s3-limitations.
:::

### 4. Open or download data files 

Once you have an S3 path for an item of interest, you can download the file to your local computer using the `aws s3 cp` AWS CLI command. You will need to include all relevant prefixes in your path. For example: 

```shell
aws s3 cp s3://sds-n-cumulus-prod-nisar-products/PRODUCT_TYPE_PREFIX/PRODUCT_NAME_PREFIX/PRODUCT_NAME.ext path/to/local/dir
```

This example shows how to download one of the SME2 files from the S3 archive: 

```
aws s3 cp s3://sds-n-cumulus-prod-nisar-products/NISAR_L3_SME2_BETA_V1/NISAR_L3_PR_SME2_008_007_D_073_4005_DHDH_A_20251216T164223_20251216T164300_X05007_N_F_J_001/NISAR_L3_PR_SME2_008_007_D_073_4005_DHDH_A_20251216T164223_20251216T164300_X05007_N_F_J_001.h5 .
```

:::{important}Copying directly to another S3 bucket not supported
Copying data directly from the NISAR S3 bucket to another S3 bucket is not supported. Users can only download content or use tools that interact with the data directly in S3 storage. See @s3-limitations.
:::

## Prefix Structure

@tbl:s3-prefix-list-products lists the prefix for each of the NISAR data product types, and @tbl:s3-prefix-list-supporting lists the prefix for each of the NISAR supporting data types.

:::{table} NISAR data product S3 prefix list
:label: tbl:s3-prefix-list-products

| Product | S3 Prefix              |
|---------|------------------------|
| SME2    | NISAR_L3_SME2_BETA_V1/ |
| GCOV    | NISAR_L2_GCOV_BETA_V1/ |
| GUNW    | NISAR_L2_GUNW_BETA_V1/ |
| GOFF    | NISAR_L2_GOFF_BETA_V1/ |
| GSLC    | NISAR_L2_GSLC_BETA_V1/ |
| RUNW    | NISAR_L1_RUNW_BETA_V1/ |
| RIFG    | NISAR_L1_RIFG_BETA_V1/ |
| ROFF    | NISAR_L1_ROFF_BETA_V1/ |
| RSLC    | NISAR_L1_RSLC_BETA_V1/ |

:::

:::{table} NISAR supporting data S3 prefix list
:label: tbl:s3-prefix-list-supporting

| Product | S3 Prefix |
|---------|-----------|
| DEM     | DEM/      |

:::

## Finding S3 Paths

As more data becomes available, you may want to use wildcard searches when using the `aws s3 ls` command to find specific products of interest. You may want to limit your results to products with specific track and/or frame numbers, acquisition dates, processing version, beam mode/polarization, or orbit direction. The product filenames contain all of this information, so to find the products you're looking for, you may want to consult @nisar-naming-conventions.

<!-- TODO: Add sample code snippet for a wildcard search to narrow down results -->

### S3 Paths from Vertex

When you search for NISAR data products in [Vertex](https://search.asf.alaska.edu/#/?maxResults=1000&dataset=NISAR), you can simply copy the S3 URL from the list of files for a search result, as shown in @vertex-s3-urls. 

```{figure} ../assets/vertex-s3-links.png
:label: vertex-s3-urls
:alt: Screenshot showing how to copy an S3 URL from Vertex search results
:align: center

Select an item from the search results, and click on the copy link icon next to the desired file listed in the right panel (you may need to adjust your screen size to see the third panel). Select S3 URL to copy the path to your clipboard.
```

(s3-limitations)=
## Limitations

Please note that S3 Access for NISAR data is subject to these limitations:
- Temporary credentials only allow access from within the us-west-2 region.
- Temporary credentials expire after one hour. The expiration time is listed in the temporary credential payload, as shown in [Step 1](#s3-creds-step-1). You can revisit [the temporary credential link](https://nisar.asf.earthdatacloud.nasa.gov/s3credentials) for a new set of credentials. 
- Temporary credentials cannot be used to sync content directly to another S3 bucket.
