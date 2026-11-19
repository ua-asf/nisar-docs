# Known Issues

NISAR products have been released with three different [maturity levels](#nisar-maturity-levels), and each release has a unique suite of known issues. This page focuses on known issues with the VALIDATED product collections. 

To learn about the known issues for PROVISIONAL or BETA products, click the buttons below. 

{button}`PROVISIONAL Known Issues <https://nisar-docs.asf.alaska.edu/provisional-known-issues/>`     {button}`BETA Known Issues <https://nisar-docs.asf.alaska.edu/product-known-issues/>`

(nisar-validated-known-issues)=
## Validated Product Known Issues

The VALIDATED products [released in November 2026](#nisar-validated-data-nov) are fully calibrated and validated, and have been approved for use in scientific analysis. There are, however, some known issues that are important to be aware of when using the data.

Known issues are summarized in @tbl:known-issues. To learn more about the issues and limitations for a specific processing version (CRID), refer to the [Release Notes](#release-notes) page. Additional issues that surface over time will be added as information becomes available, and entries will be updated as issues are resolved. 

If you encounter issues with NISAR products that are not addressed here, please post them to [NASA's Earthdata Forum](#nisar-in-earthdata-forum).

### Known Issues Table

:::{table} Summary of known issues for NISAR products, including links to descriptions.
:label: tbl:known-issues
:align: center

| Issue Summary                                                                                              | Date Added  | Status                                                                                                                    |
|------------------------------------------------------------------------------------------------------------|-------------|---------------------------------------------------------------------------------------------------------------------------|
| [Calibration of earlier data](#issue-calibration-earlier-data)                                             | 12 Nov 2026 | Expect to fix in reprocessing campaign                                                                                    |
| [GUNW phase artifact from squint compensation](#issue-gunw-phase-artifact-squint)                          | 12 Nov 2026 | Expect to be fixed with next release                                                                                      |
| [Valid mask fraction metadata not yet searchable](#issue-valid-mask-fraction-metadata)                     | 12 Nov 2026 | Expected to be resolved Dec 2026                                                                                          |
| [Mixed CRIDS for transitional interferometry products](#issue-mixed-crids-transitional-insar)              | 12 Nov 2026 | Will be reprocessed in future                                                                                             |
| [Ionospheric effects](#issue-ionospheric-effects)                                                          |             | Improved by [new coregistration approach](#new-insar-coregistration); working to develop additional mitigation techniques |
| [Joint mode data gaps](#issue-joint-mode-data-gaps)                                                        |             | Working to develop mitigation techniques                                                                                  |
| [Residual radiometric and polarimetric ripples across the swath](#issue-residual-ripples-across-swath)     |             | Working to develop mitigation techniques                                                                                  |
| [Phase unwrapping in challenging environments](#issue-phase-unwrapping)                                    |             | Working to develop mitigation techniques                                                                                  |
| [Radio Frequency Interference (RFI)](#issue-rfi)                                                           |             |                                                                                                                           |
| [Customized Copernicus DEM v1.3 latitude band transitions](#issue-cop-dem-lat-band-transition)             |             | Issue ongoing                                                                                                             |
| [Unrecoverable Data Loss](#issue-unrecoverable-data-modes)                                                 |             | Permanent issue                                                                                                           |
| [Permanent NISAR instrument data gap between 2026-07-27 and 2026-08-10](#permanent-data-gap-july26)        | 10 Aug 2026 | Permanent issue                                                                                                           |

:::


### Current Known Issues

These issues are currently impacting VALIDATED products. Some issues are unresolvable, but others may be mitigated in future updates to the NISAR processing software.

#### Known Issues: P05036 Release

Known issues associated with CRID [P05036](https://www.earthdata.nasa.gov/data/platforms/space-based-platforms/nisar/nisar-composite-release-id-crid#toc-p05036) (the software version used for first validated data release) are documented in the [release notes](#p05036-known-issues). Issue descriptions from the release notes are linked in @tbl:known-issues.

(permanent-data-gap-july26)=
#### Permanent data gap

No data was collected by the NISAR platform between 2026-07-27T22:03:25Z and 2026-08-10T00:55:27Z. There are not currently any VALIDATED products available for this time range, but the data gap will also be present in the VALIDATED collections once the [reprocessing campaign](#validated-reprocessing) is complete.

### Resolved Known Issues

(issue-timestamp-incomplete-l0b)=
#### Incomplete L0B Products

***Resolved with [CRID P05036](https://www.earthdata.nasa.gov/data/platforms/space-based-platforms/nisar/nisar-composite-release-id-crid#toc-p05036)***

One of the most critical issues with the PROVISIONAL products, which was resolved before any VALIDATED data products were processed, was a [timestamp issue that resulted in incomplete L0B products](#provisional-issue-incomplete-l0b-products). The majority of Earthdata Forum posts about PROVISIONAL products stem from this issue, but it is not an issue for VALIDATED products. 
