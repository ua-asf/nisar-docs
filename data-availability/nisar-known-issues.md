# Known Issues

NISAR products have been released with three different [maturity levels](#nisar-maturity-levels), and each release has a unique suite of known issues. This page focuses on known issues with the VALIDATED product collections. 

To learn about the known issues for PROVISIONAL or BETA products, click the buttons below. 

{button}`PROVISIONAL Known Issues <https://nisar-docs.asf.alaska.edu/provisional-known-issues/>`     {button}`BETA Known Issues <https://nisar-docs.asf.alaska.edu/product-known-issues/>`

(nisar-validated-known-issues)=
## Validated Product Known Issues

The VALIDATED products [released in November 2026](#nisar-validated-data-nov) are fully calibrated and validated.

While these products meet calibration and validation requirements for the mission, there are some known issues that users should be aware of. Some of these issues are inherent to the mission data, while others have the potential to be addressed in the future using new processing approaches. 

Known issues with the NISAR data are tracked in @tbl:known-issues, and additional issues that surface over time will be added as information becomes available. Entries will be updated as issues are resolved or determined to be permanent. 

If you encounter issues with NISAR products that are not addressed here, please post them to [NASA's Earthdata Forum](#nisar-in-earthdata-forum).

### Known Issues Table

Each known issue is summarized in @tbl:known-issues, which provides a link to a more detailed description of the issue.

:::{table} NISAR Known Issues Table
:label: tbl:known-issues
:align: center

| Issue Summary                                                                                       | Date Added  | Status                                                                                 |
|-----------------------------------------------------------------------------------------------------|-------------|----------------------------------------------------------------------------------------|
| [Calibration of earlier data](#issue-calibration-earlier-data)                                      | 12 Nov 2026 | Expect to fix in reprocessing campaign                                                 |
| [GUNW phase artifact from squint compensation](#issue-gunw-phase-artifact-squint)                   | 12 Nov 2026 | Expect to be fixed with next release                                                   |
| [Customized Copernicus DEM v1.3 latitude band transitions](#issue-cop-dem-lat-band-transition)      | 12 Nov 2026 | Issue ongoing                                                                          |
| [Valid mask fraction metadata not yet searchable](#issue-valid-mask-fraction-metadata)              | 12 Nov 2026 | Expected to be resolved Dec 2026                                                       |
| [Stripes in SLC data from loopback residuals](#issue-stripes-in-slc-loopback)                       | 12 Nov 2026 | Working to develop mitigation techniques                                               |
| [Joint mode 40 MHz products](#issue-joint-mode-products)                                            | 12 Nov 2026 | Issue ongoing                                                                          |
| [Joint mode data gaps](#issue-joint-mode-data-gaps)                                                 | 12 Nov 2026 | Working to develop mitigation techniques                                               |
| [Mixed CRIDS for transitional interferometry products](#issue-mixed-crids-transitional-insar)       | 12 Nov 2026 | Will be reprocessed in future                                                          |
| [Incomplete L0B Products](#issue-timestamp-incomplete-l0b)                                          | 05 Nov 2026 | Resolved with CRID P05036 <!--[#TODO: add link to CRID on NIAR page once available]--> |
| [Permanent NISAR instrument data gap between 2026-07-27 and 2026-08-10](#permanent-data-gap-july26) | 10 Aug 2026 | Permanent issue                                                                        |


:::


### Current Known Issues

These issues are currently impacting VALIDATED products. Some issues are unresolvable, but others may be mitigated in future updates to the NISAR processing software.

#### Known Issues: P05036 Release

Known issues associated with CRID P05036 (the software version used for first validated data release) are documented in the [release notes](#p05036-known-issues). Issue descriptions from the release notes are linked in @tbl:known-issues.

(permanent-data-gap-july26)=
#### Permanent data gap

No data was collected by the NISAR platform between 2026-07-27T22:03:25Z and 2026-08-10T00:55:27Z. There are not currently any VALIDATED products available for this time range, but the data gap will also be present in the VALIDATED collections once the [reprocessing campaign](#validated-reprocessing) is complete.

### Resolved Known Issues

(issue-timestamp-incomplete-l0b)=
#### Incomplete L0B Products

***Resolved with CRID P05036*** <!--[#TODO: add link to CRID on NISAR page once available]-->

One of the most critical issues with the PROVISIONAL products was a [timestamp issue that resulted in incomplete L0B products](#provisional-issue-incomplete-l0b-products). This manifested in downstream product types as a range of artifacts, including defocused RSLC images, missing data, and decorrelation in InSAR products. The majority of issues with PROVISIONAL products reported to the Earthdata Forum were caused by this issue, but it was resolved before VALIDATED data products were processed. 
