---
short_title: Release Notes
---

# NISAR Validated Products 

## Release Notes: CRID P05036

### Release Overview

Starting with this release, NISAR Level 0 through Level 2 products are designated VALIDATED. The Level 3 Soil Moisture (SME2) products remain PROVISIONAL.

The project and science teams have examined hundreds of thousands of data products at global and regional scales, both synoptically and through detailed scene analysis. From this analysis, the team has determined that the L0–L2 products are validated and suitable for science, with remaining issues reported below and tracked on the @nisar-validated-known-issues page. 

New L0–L2 products starting with this release are marked VALIDATED and will be found in the Earthdata validated archive.

These products are processed with [NISAR Composite Release ID (CRID) P05036](https://www.earthdata.nasa.gov/data/platforms/space-based-platforms/nisar/nisar-composite-release-id-crid)<!--[#TODO: add link to specific CRID once it's available]-->. Documented known issues are being worked on and will be resolved or mitigated in future releases.

### Product Maturity

These release notes document the [VALIDATED](#nisar-validated-data-nov) data products. Refer to documentation for the [PROVISIONAL](#nisar-provisional-data-july) and [BETA](#nisar-sample-data-feb) products.

:::{table} NISAR Data Maturity Levels
:label: tbl:data-maturity
:align: center

| Maturity               | CRID                   | Products | Archive                     |
|:-----------------------|:-----------------------|:---------|:----------------------------|
| VALIDATED              | P05036 and higher      | L0–L2    | Earthdata validated archive |
| PROVISIONAL            | P05036 and higher      | L3 SME2  | Provisional collection      |
| PROVISIONAL            | P05023 to below P05036 | All      | Provisional collection      |
| BETA (pre-calibration) | Below P05023           | All      | Beta collection             |

:::

Users should take care when analyzing products of different maturity levels together, since differences in processing software may affect results. Earlier data affected by the radiometric calibration issue will be replaced by VALIDATED products after the [reprocessing campaign](#validated-reprocessing) planned for early 2027.

### What's New

#### Radiometric and Polarimetric Calibration

Products processed after November 12, 2026, have significantly improved radiometric and polarimetric calibration, including corrections for polarimetric channel imbalance. P05036 products processed after this date do not require the 59° phase correction previously published for provisional products. Calibration issues affecting P05035 products produced earlier than November 12 are described under Known Issues.

#### L0B Update

The timestamp issue that caused incomplete L0B products has been resolved in VALIDATED products. This issue affected downstream products, causing defocused RSLC images, missing data, and decorrelation in InSAR products. It accounted for most issues reported to the Earthdata Forum for PROVISIONAL products.

#### Masking

Missing-data masks and other mask layers are now more complete and consistent across products. A small percentage of data (~1–2%) may be lost due to downlink issues. Data processed with CRID P05036 and above include additional information used to generate missing-data masks and statistics across products. 

#### Interferogram Coregistration

GUNW/RUNW/RIFG interferograms now consistently use data-driven offsets in addition to geometrical offsets to align reference and secondary images in the coregistration step referred to as “rubbersheeting”.  This configuration reduces residual misalignment between image pairs, improving coherence and the continuity of the interferometric phase across the scene. As a result, the validated GUNW products over solid earth regions now include data-driven pixel offsets instead of a polynomial fit in the provisional products. These pixel offsets can capture large ground movements such as those caused by earthquakes and volcanic activities. 

#### Phase Unwrapping 

The quality of phase unwrapping in the validated products has been improved by 1) fixing an edge case in the bridging algorithm 2) allowing to produce connected components with smaller size and 3) by using valid data masks for generating connected components.  

#### Digital Elevation Model (DEM)

Products are now processed with the NISAR Customized Copernicus DEM (CC-DEM) v1.3, which includes several fixes that improve overall product quality compared with v1.2. These include removal of the artifact along the prime meridian and at DEM tile boundaries at high latitudes. The DEM will remain identical at mid latitudes. Remaining DEM issues are listed under Known Issues. 

#### Other Improvements

Other bug fixes and improvements make this data set more complete and robust than previous releases. 

### Known Issues 

#### Calibration of earlier data

About 30% of the data acquired in specific radar modes and processed before November 12, 2026, are affected by a calibration issue, with radiometric residuals of approximately 1 dB and polarimetric phase inconsistencies. The radar modes affected by this issue are listed in @tbl:degraded-radar-modes; they were fixed for data acquired after November 12, 2026. 

Affected data will be corrected during a reprocessing campaign planned for early 2027, covering acquisitions from the start of the science phase on December 29, 2025. Until reprocessed data are available, users combining products processed before and after November 12 should expect radiometric differences and polarimetric phase inconsistencies.

:::{table} Science radar modes degraded before November 12, 2026, and fixed for subsequent acquisitions
:label: tbl:degraded-radar-modes
:align: center

For details on how to interpret the mode mnemonics, refer to @nisar_summary or @mnemonic-scheme.

| RCID | Mode mnemonics            | Science Target                                          |
|:-----|:--------------------------|:--------------------------------------------------------|
| 151  | L:SCI:SH:40M05N:FS:B4:D11 | Land Ice Low Res                                        |
| 156  | L:SCI:DH:40M05N:FS:B4:D02 | L-only Background Land                                  |
| 217  | L:SCI:DH:40M05N:FS:B4:D02 | High-Res Deformation (Urban/Landslide)                  |
| 223  | L:SCI:SH:40M05N:FS:B4:D02 | Land Ice Low Res                                        |
| 236  | L:SCI:DH:40M05N:FS:B4:D02 | Glacial Ice-Himalayas                                   |
| 237  | L:SCI:QP:20M05N:FS:B4:F05 | ISRO Cal/Val                                            |
| 238  | L:SCI:DH:40M05N:FS:B4:D02 | ISRO Background Land and Global Science Cal/Val targets |
| 247  | L:SCI:SH:40M05N:FS:B4:D02 | Land Ice - Antarctica                                   |
| 248  | L:SCI:SH:40M05N:FS:B4:D02 | ISRO Bohai Bay and NASA Urban Area                      |

:::

#### GUNW phase artifact from squint compensation

GUNW products contain an interferometric phase artifact caused by incomplete squint compensation during the interpolation step of rubbersheeting. The artifact is a function of data-driven azimuth offsets used during coregistration and is observed in areas with significant ionospheric phase gradient in along-track direction (usually in high latitudes). The phase artifact is deterministic and users can apply a correction using [link to notebook]()<!--[#TODO: Add link when available from JPL)]-->. This issue will be fixed in the next release, removing the need for users to apply the correction.

#### Customized Copernicus DEM v1.3 latitude band transitions

Small elevation errors of approximately ±5 m can occur where terrain changes sharply across latitude band boundaries in the Customized Copernicus DEM (CC-DEM) v1.3, which is derived starting from the Copernicus COP-DEM_GLO-30-DGED/2023_1. Customization is described in the readme.txt distributed with the CC-DEM product.

#### Valid mask fraction metadata not yet searchable

Products include new valid mask fraction metadata fields, but these fields are currently not searchable in CMR. Until the DAAC production ingest is updated, expected in December 2026, products remain searchable using only existing metadata fields.

#### Stripes in SLC data from loopback residuals

Low-level stripes may occasionally appear in SLC and derived products over dark backgrounds. These arise from residual energy from looped-back transmit events at the edges of the L0B data. Stripe levels remain within requirements, and work is ongoing to eliminate them.

#### Joint mode 40 MHz products

Products acquired in joint L- and S-band mode at 40 MHz bandwidth show residual radiometric bands that are larger than typical. They are within requirements but visually noticeable.

#### Joint mode data gaps

A small fraction of data contain along-track gaps of approximately 2 seconds when transitioning between to/from joint L+S acquisition and an L-only acquisition. Less frequent gaps of approximately 0.25 seconds occur when an onboard file reaches its size limit and a new file is opened. The team is working to minimize these gaps in future acquisitions.

#### Mixed CRIDS for transitional interferometry products

In the transition between provisional to validated products, interferometric products are produced by interfering provisional (CRID=P05023) with validated RSLC products (CRID=P05036). Differences in calibration and phase characteristics between the two versions introduce an additional interferometric phase component.

These interferograms will be available for later acquisitions dated October 21, 2026 onward, paired with acquisitions 12 days earlier, or at longer 12-day intervals where needed to find the first suitable earlier acquisition. They will be reprocessed in a future campaign using consistent CRIDs.

### Product characteristics and limitations

#### Soil Moisture (SME2) products

SME2 products remain PROVISIONAL. They require a time series of L2 GCOV inputs, and some cal/val metrics such as unbiased RMSE need longer time series before they can be computed. In quad-pol areas, three to six gaps across the swath arise from NISAR's SweepSAR acquisition and the number of time steps in the algorithm. In that case, one or more of the three SME2 algorithms may not deliver an estimate.

#### Residual radiometric and polarimetric ripples across the swath

Low-level systematic radiometric ripples remain across the swath, with amplitudes below 0.25 dB in both frequency A and frequency B, well within requirements. A residual ripple of 2–3° is also present in the HH–VV and HV–VH polarimetric phase differences. The project is investigating further radiometric and polarimetric ripple reductions to be addressed in future releases.

#### Phase unwrapping

Phase unwrapping in challenging environments remains difficult. The project will continue to improve unwrapping performance throughout the mission.

#### Ionospheric effects

Residual ionospheric effects remain challenging to mitigate at high latitudes. Data are generally usable, but users may encounter geolocation errors, patterned decorrelation bands in interferograms, and residual phase errors after applying the ionospheric correction layer. Local geometric distortions exceeding a fraction of a pixel can also cause the processing algorithms to introduce additional phase errors. The updated interferogram coregistration, which now incorporates data-driven offsets (see "What's new in this release - Interferogram coregistration"), helps reduce misalignment caused by these distortions, although residual ionospheric effects may persist. 

#### Radio frequency interference

The RFI mitigation filter generally performs well, but residual interference remains in some areas. The filter can also remove real features in areas with strong signal contrasts.

### Ongoing monitoring and assessment

#### Corner reflector radiometric trends

The team is investigating possible temporal trends in radar cross section (RCS) measured over corner reflectors. These trends will be better characterized and documented as more data become available.
