# AWS S3 Access

(aws-s3-access-overview)=
## Overview

All NISAR data is hosted in [NASA's Earthdata Cloud (EDC)](https://www.earthdata.nasa.gov/about/earthdata-cloud-evolution), which leverages Amazon Web Services (AWS) infrastructure. As such, AWS Simple Storage Service (S3) access methods can be used to interact with NISAR datasets. 

Data users can request temporary AWS credentials enabling direct access to the data in S3. This supports the use of a wide range of S3-aware tooling for interacting with cloud-hosted data as well as for low-latency and high-throughput data access patterns.

## Accessing NISAR Data via S3 Using AWS CLI

(s3-creds-step-1)=
1. Visit https://nisar.asf.earthdatacloud.nasa.gov/s3credentials. If prompted, sign in with your [Earthdata Login (EDL) credentials](https://urs.earthdata.nasa.gov/) to retrieve a set of temporary AWS credentials. If you are already signed in, the credentials will display immediately.

   These credentials allow users to list and download contents of the S3 bucket. 

   The text displayed at the site will provide three keys: 
    * AWS Access Key ID
    * AWS Secret Access Key
    * AWS Session Token
   
   For example: 
   ```shell
   {  
     accessKeyId: "ASIAIOSFODNN7EXAMPLE",  
     secretAccessKey: "wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY",  
     sessionToken: "LONGSTRINGOFCHARACTERS...6XUxCYEwbjGVKkzSNQh/", 
     expiration: "2026-01-27 00:50:09+00:00"
   }
   ```
   
    >  More details about requesting temporary S3 credentials are [available here](https://nisar.asf.earthdatacloud.nasa.gov/s3credentialsREADME).

2. Configure your environment to use the temporary AWS credentials by setting the environment variables in your terminal. 
   For example, if you are on a Linux operating system, you can export your credentials with the following commands:
   ```shell
   export AWS_ACCESS_KEY_ID=ASIAIOSFODNN7EXAMPLE
   export AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
   export AWS_SESSION_TOKEN=AQoDYXdzEJr...<remainder of session token>
   ```
   > For a full list of exportable variables, see [AWS's Temporary Credentials User Guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_use-resources.html).

3. Explore the `sds-n-cumulus-prod-nisar-products` S3 bucket to find data of interest. The bucket is organized by product type, then by product. Consult @nisar-naming-conventions to understand the product names to help find what you're looking for.
    For example, if you want to see all available products, you can use the `aws s3 ls` command, such as: 
    ```
   aws s3 ls s3://sds-n-cumulus-prod-nisar-products/
   ```
   
4. Open or download data files. For example, you can download a GCOV file with the `aws s3 cp` command with: 
    ```
   aws s3 cp s3://sds-n-cumulus-prod-nisar-products/NISAR_L2_GCOV_BETA_V1/NISAR_FILENAME.h5 path/to/local/dir 
   ```

## Limitations

Please note that S3 Access for NISAR data is subject to these limitations:
- The temporary credentials only allow access from within the us-west-2 region.
- The temporary credentials expire after one hour. You can refresh [the link in Step 1](#s3-creds-step-1) for a new set of credentials. 
- Temporary credentials cannot be used to sync content directly to another S3 bucket.
