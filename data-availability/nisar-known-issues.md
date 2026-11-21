---
short_title: Known Issues
---

# Known Issues and Limitations

NISAR products have been released with three different [maturity levels](#nisar-maturity-levels), and each release has a unique suite of known issues. This page focuses on known issues with the VALIDATED product collections. 

To learn about the known issues for PROVISIONAL or BETA products, click the buttons below. 

{button}`PROVISIONAL Known Issues <https://nisar-docs.asf.alaska.edu/provisional-known-issues/>`     {button}`BETA Known Issues <https://nisar-docs.asf.alaska.edu/product-known-issues/>`

(nisar-validated-known-issues)=
## Validated Product Known Issues

The VALIDATED products [released in November 2026](#nisar-validated-data-nov) are fully calibrated and validated, and have been approved for use in scientific analysis. There are, however, some known issues and limitations (summarized in @tbl:known-issues) that are important to be aware of when using the data.

To learn more about the issues and limitations for a specific processing version (CRID), refer to the [Release Notes](#release-notes) page. Additional issues that surface over time will be added to @tbl:known-issues as information becomes available, and entries will be updated as issues are resolved. 

If you encounter issues with NISAR products that are not addressed here, please post them to [NASA's Earthdata Forum](#nisar-in-earthdata-forum).

### Known Issues and Limitations Table

:::{table} Summary of known issues and limitations for NISAR products, including links to descriptions.
:label: tbl:known-issues
:align: center

| Issue Summary                                                                                          | Date Added  | Status                                                                                                                                                                                           |
|--------------------------------------------------------------------------------------------------------|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Calibration of earlier data](#issue-calibration-earlier-data)                                         | 12 Nov 2026 | Only impacts data acquired before November 12, 2026. Expect to correct the issue for data acquired between 2025-12-29 and 2026-11-12 during the [reprocessing campaign](#validated-reprocessing) |
| [Mixed CRIDS for transitional interferometry products](#issue-mixed-crids-transitional-insar)          | 06 Nov 2026 | Will be corrected in the [reprocessing campaign](#validated-reprocessing)                                                                                                                        |
| [GUNW phase artifact from squint compensation](#issue-gunw-phase-artifact-squint)                      | 06 Nov 2026 | Expect to be fixed with next release                                                                                                                                                             |
| [Valid mask fraction metadata not yet searchable](#issue-valid-mask-fraction-metadata)                 | 06 Nov 2026 | Expect to be resolved Dec 2026                                                                                                                                                                   |
| [Ionospheric effects](#issue-ionospheric-effects)                                                      | 06 Nov 2026 | Improved by [new coregistration approach](#new-insar-coregistration); working to develop additional mitigation techniques                                                                        |
| [Joint mode data gaps](#issue-joint-mode-data-gaps)                                                    |             | Working to develop mitigation techniques                                                                                                                                                         |
| [Residual radiometric and polarimetric ripples across the swath](#issue-residual-ripples-across-swath) |             | Working to develop mitigation techniques                                                                                                                                                         |
| [Phase unwrapping in challenging environments](#issue-phase-unwrapping)                                |             | Working to develop mitigation techniques                                                                                                                                                         |
| [Residual Radio Frequency Interference (RFI)](#issue-rfi)                                              |             | Under assessment to determine if additional improvements are possible                                                                                                                            |
| [Customized Copernicus DEM v1.3 latitude band transitions](#issue-cop-dem-lat-band-transition)         |             | Issue ongoing                                                                                                                                                                                    |
| [Unrecoverable Data Loss in some modes prior to 2026-11-12](#issue-unrecoverable-data-modes)           | 12 Nov 2026 | Permanent issue for acquisitions prior to November 12, 2026                                                                                                                                      |
| [Permanent NISAR instrument data gap between 2026-07-27 and 2026-08-10](#permanent-data-gap-july26)    | 10 Aug 2026 | Permanent issue                                                                                                                                                                                  |

:::


### Current Known Issues

These issues are currently impacting VALIDATED products. Some issues are unresolvable, but others may be mitigated in future updates to the NISAR processing software.

#### Known Issues: P05036 Release

Known issues associated with CRID [P05036](https://www.earthdata.nasa.gov/data/platforms/space-based-platforms/nisar/nisar-composite-release-id-crid#toc-p05036) (the software version used for the first validated data release) are documented in the [release notes](#p05036-known-issues). Issue descriptions from the release notes are linked in @tbl:known-issues.

(permanent-data-gap-july26)=
#### Permanent data gap

No data was collected by the NISAR platform between 2026-07-27T22:03:25Z and 2026-08-10T00:55:27Z. There are not currently any VALIDATED products available for this time range, but the data gap will also be present in the VALIDATED collections once the [reprocessing campaign](#validated-reprocessing) is complete.

### Resolved Known Issues

#### Resolved with [CRID P05036](https://www.earthdata.nasa.gov/data/platforms/space-based-platforms/nisar/nisar-composite-release-id-crid#toc-p05036)

The processing version used for the [first release of VALIDATED data](#nisar-validated-data-nov) ([CRID P05036](https://www.earthdata.nasa.gov/data/platforms/space-based-platforms/nisar/nisar-composite-release-id-crid#toc-p05036)) implemented fixes for [many of the issues](#p05036-whats-new) that impact [PROVISIONAL products](#nisar-provisional-data-july). 

Notably, this version of the processor [fixes an issue](#p05036-fix-l0b) that is the source of many of the artifacts users encounter in PROVISIONAL products: a [timestamp issue that resulted in incomplete L0B products](#provisional-issue-incomplete-l0b-products).
