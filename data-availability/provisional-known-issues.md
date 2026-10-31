---
short_title: Known Issues
---
# NISAR Products

_Updated July 30, 2026_

(provisional-known-issues)=
## Provisional Product Known Issues

The PROVISIONAL products [released in July 2026](#nisar-provisional-data-july) are calibrated and have undergone validation at a limited set of sites around the world. These data are designated as PROVISIONAL pending more complete calibration and validation over larger areas around the globe.  

These products, processed using the [NISAR Composite Release ID (CRID) P05023](https://www.earthdata.nasa.gov/data/platforms/space-based-platforms/nisar/nisar-composite-release-id-crid), are a significant improvement over the [pre-calibration BETA products](#nisar-sample-data-feb) released in February 2026. There are, however, a few known issues with the PROVISIONAL products that users should be aware of. 

**These issues are currently being reviewed and will be resolved or mitigated in future releases.**

### Ionospheric Effects

At high latitudes, mitigation of ionospheric effects on the propagation path have proven to be challenging. The data are generally usable, but users can expect some degradation in performance, including geolocation errors, patterned decorrelation bands in interferograms, and interferometric phase residuals even after applying the ionospheric estimation layer. 

In cases where local geometric distortions are larger than a fraction of a pixel, phase residuals can be introduced by the processing algorithm themselves. The project and science teams continue to work on improved mitigation methods.

### Radio Frequency Interference

The PROVISIONAL products have been processed with a filter that suppresses or mitigates the effects of radio-frequency interference (RFI). While the filter appears to perform well in general, it underperforms in some places by leaving residual RFI, or overperforms by removing features in high contrast areas.  

### Ripples in SLC Data

Low-level ripples in the SLC data and derived products may occasionally be seen in areas with dark backgrounds. These are introduced in the L0B data, which continue to have low levels of residual energy from the looped-back transmit events present at their edges. The residual signal levels are low and meet requirements, but further work is needed to eliminate them.

### Frequency B Calibration

The calibration of the 5 MHz Frequency B channel, which is designed for split-spectrum processing, has larger systematic radiometric calibration residuals than the main band Frequency A. While there are no radiometric requirements for Frequency B, datasets generated from this channel have been found to be useful in their own right. As such, calibration of the Frequency B channel will be improved.

### Polarimetric Calibration

The relative phase between polarimetric channels is not fully calibrated due to a change in the phase imbalance between H and V after the polarimetric calibration coefficients were derived. 

Users performing coherent dual-pol or quad-pol analysis can compensate with a phase shift of θ = 59° according to the following rule: 

- For RSLC and GSLC products: multiply the HV and VV layers by e<sup>+jθ</sup>
- For GCOV products: multiply the HVVH layer by e<sup>+jθ</sup>, and the HHHV, HHVV, and VHVV layers by e<sup>-jθ</sup>, leaving the HHVH, HVVV, HHHH, HVHV, VHVH, and VVVV layers unaffected

### Incomplete L0B Products

Users will find some products were generated from incomplete L0B datasets, due to missing data in the downlink caused by weather and other capture issues.  The quality flags in the L0B data quality products identify where these data issues occur. The higher-level products generated from these incomplete L0B are included in the archive, since some users may still find them useful.

In a small percentage of the products (around 1-2% of the products), the raw data processor encounters missing data, which introduces undesired shifts to the valid part of the raw data. This in turn may lead to artifacts in downstream products such as defocused RSLC, misplaced products, and decorrelation in InSAR products.

### Diagnostic Mode Frames

Users will find that the L-SAR products using calibration modes in Track 161/174, 161/175, 169/090, 169/091 are not usable. This will be rectified for acquisitions from August 2026 onward.

### Joint Mode 40 MHz Products

Products acquired in joint mode (both L and S band) with 40 MHz bandwidth appear to have residual radiometric bands that are larger than typical. They are still within requirements, but are visually noticeable. 

(provisional-known-issues-sme2)=
### Soil Moisture Products

[Soil Moisture (SME2)](#sme2-product-overview) products require time series of Level 2 [GCOV](#gcov-product-overview) products as input for the processing workflow. Because fully calibrated GCOV products have only recently become available, and the calibration/validation process requires longer time series before some cal/val metrics (e.g., un-biased root mean squared error (UBRMSE)) can be computed, the SME2 products in the PROVISIONAL collection are not yet fully calibrated. 

In areas of quad-pol acquisitions, there are three to six gaps across the swath due to the nature of NISAR’s SweepSAR acquisition and the number of time steps used in the soil moisture algorithm. In these gap areas, there will be occasions where one or more of the three soil moisture algorithms included in the SME2 products may not deliver an estimate.

## Product Maturity

[NISAR PROVISIONAL products](#nisar-provisional-data-july) are available for acquisitions starting June 17, 2026, but [BETA products](#nisar-sample-data-feb) are available for earlier acquisition dates (October 2025 - January 2026) in some areas.

All released data going forward from the PROVISIONAL data release will have a CRID of P05023 or higher, while BETA pre-calibration products have lower CRID numbers. 

Users should exercise caution if they analyze BETA products together with PROVISIONAL products, as differences in the processing software used for these different [product maturities](#nisar-maturity-levels) may impact results.