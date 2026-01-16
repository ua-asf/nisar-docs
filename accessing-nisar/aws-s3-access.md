# AWS S3 Access

## Overview
All NISAR data is hosted in the Amazon Web Services (AWS) cloud via the Simple Storage Service (S3). Data users can request temporary AWS credentials enabling direct access to the data in S3. This supports the use of a wide range of S3-aware tooling for interacting with cloud-hosted data as well as for low-latency and high-throughput data access patterns.

## Limitations

S3 Access for NISAR data is subject to these limitations:
- The temporary credentials only allow access from within the us-west-2 region
- The temporary credentials expire after one hour.
- Temporary credentials cannot be used to sync content directly to another S3 bucket

## Accessing NISAR Data via S3

1. Visit https://nisar.asf.earthdatacloud.nasa.gov/s3credentials and sign in with your Earthdata Login credentials to retrieve a set of temporary AWS credentials (an access key, a secret key, and a session token).
   2. https://nisar.asf.earthdatacloud.nasa.gov/s3credentialsREADME
2. Configure your environment to use the temporary AWS credentials.
   3. https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_use-resources.html
3. Explore the `sds-n-cumulus-prod-nisar-products` S3 bucket to find data of interest. The bucket is organized by product type, then by product. Consult @nisar-naming-conventions to understand the product names to help find what you're looking for.
4. Open or download data files.

CMR granule records include s3 URIs in addition to http URLs.

earthaccess can do a lot of this for you

https://tea-docs.asf.alaska.edu/s3access/
