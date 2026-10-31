---
short_title: Available Data
---

# Available NISAR Data

NISAR launched July 30, 2025, and has been successfully collecting data through its Commissioning phase and into the Science phase. The calibration-validation process is underway, and fully calibrated NISAR PROVISIONAL products for the full observation plan are now available to the public.

In addition, a limited set of [NISAR S-band sample data products](https://bhoonidhi.nrsc.gov.in/NISAR/NisarProducts.html) can now be accessed through ISRO's [Bhoonidhi data hub](https://bhoonidhi.nrsc.gov.in/bhoonidhi/home.html). This S-band product release includes RSLC, GSLC, and GCOV products generated from NISAR acquisitions in January and February 2026. Refer to the [Bhoonidhi NISAR Mission site](https://bhoonidhi.nrsc.gov.in/NISAR/) for more information.

(nisar-validated-data-nov)=
## NISAR VALIDATED Data: November 2026

{button}`Find NISAR VALIDATED L-Band Data <https://search.asf.alaska.edu/#/?prodConfig=PR&dataMaturity=VALIDATED>`

NISAR VALIDATED datasets were released November 4, 2026. These products are fully calibrated and validated, and acquisitions prior to the release date have been reprocessed. NISAR VALIDATED collections are available for all mission products from Level 0 through Level 2, and include products globally from [#TODO: add date] onward.

VALIDATED Level 3 [Soil Moisture (SME2)](#sme2-product-overview) products are not yet available, as additional validation efforts using the PROVISIONAL and VALIDATED GCOV datasets are still underway. 

(validated-known-issues)=
Most of the known issues identified in the [BETA](./product-known-issues.md) and [PROVISIONAL](./provisional-known-issues.md) products have been resolved in the VALIDATED products, but there are still some [known issues](#nisar-validated-known-issues) in the VALIDATED data products.

There are no plans for another full-archive reprocessing campaign, but updates to the processing software may be released periodically as algorithms are further refined, resulting in products that are generated using different NISAR Composite Release ID (CRID) versions. 

CRID version updates, including descriptions of the changes introduced with each version, are tracked on the [NISAR CRID page](https://www.earthdata.nasa.gov/data/platforms/space-based-platforms/nisar/nisar-composite-release-id-crid).

(nisar-provisional-data-july)=
## NISAR PROVISIONAL Data: July 2026

{button}`Find NISAR PROVISIONAL L-Band Data <https://search.asf.alaska.edu/#/?prodConfig=PR&dataMaturity=PROVISIONAL>`

NISAR PROVISIONAL datasets were released July 20, 2026. These products are fully calibrated and have undergone validation at a limited set of sites around the world. These datasets are designated as PROVISIONAL pending more complete validation over larger areas around the globe, but are a significant improvement over the [BETA products](#nisar-sample-data-feb) released in Feburary 2026.

NISAR PROVISIONAL collections are available for all mission products from Level 0 to Level 3, including raw Level-0B [RRSD](#rrsd-product-overview) products. Prior data releases did not include RRSD products.

(known-issues)=
Most of the known issues with the BETA products have been resolved in this release, and the PROVISIONAL products generally meet radiometric and geolocation requirements in lower-latitude areas where ionospheric variability is low, but there are still a few [known issues](./provisional-known-issues.md) users should be aware of when working with the PROVISIONAL products. 

:::{important}NISAR Data Gap
Permanent NISAR instrument data gap exists between `2026-07-27T22:03:25Z` and `2026-08-10T00:55:27Z`.

:::

The PROVISIONAL products are generated using the [NISAR Composite Release ID (CRID) P05023](https://www.earthdata.nasa.gov/data/platforms/space-based-platforms/nisar/nisar-composite-release-id-crid), and are available for all acquisitions starting June 17, 2026. Users should take care if they choose to combine PROVISIONAL products with BETA products (generated at lower CRID numbers than 05023) in analysis workflows, as some differences will be due to changes in the processing software.

### Supplemental Provisional Products

The PROVISIONAL collections also include longer time series for specific frames that were selected by the science team for use in time-series validation work.

(nisar-sample-data-feb)=
## NISAR BETA Data: February 2026

{button}`Find NISAR BETA L-Band Data <https://search.asf.alaska.edu/#/?prodConfig=PR&dataMaturity=BETA>`

Prior to the release of the PROVISIONAL products, a selection of pre-calibration BETA NISAR L-band products was made available through the ASF DAAC. These BETA products were released to allow users to develop workflows to access the data and metadata for each product type, to become familiar with the characteristics of the L-band products, and to begin working with the data in a substantive way.

(sample-product-limitations)=
The BETA products are not fully calibrated, and there are a number of [known issues](./product-known-issues.md) users should be aware of when working with these datasets. The PROVISIONAL products released in July 2026 are fully calibrated and partially validated, and are a significant improvement over the BETA products. Users should exercise care if attempting to analyze BETA products together with PROVISIONAL products.

The February 2026 release includes all Level-1 to Level-3 products for a subset of the data acquired between October 17, 2025 and January 20, 2026. This includes up to 8 acquisitions per track (both ascending and descending), and is a representative distribution of the production observation plan. @feb-26-data-release displays the spatial extent of the data included in this release. For a more detailed acquisition map, see the interactive [NISAR February 2026 Released Data](https://experience.arcgis.com/experience/0042193b06104889971cd77f505190e0) map.

```{figure} ../assets/feb-26-data-release.png
:label: feb-26-data-release
:alt: Map of the spatial extent of archived pre-calibration products included in the February 2026 data release.
:align: center

Spatial distribution of the archived pre-calibration NISAR data products, highlighted in green, included in the February 2026 data release.  
<span style="font-size: 12px;">_Basemap credits: Esri, TomTom, Garmin, FAO, NOAA, USGS, (c) OpenStreetMap contributors, and the GIS User Community._</span>
```

(data-release-timeline)=
## L-Band Data Release Timeline

NISAR has continually collected L-band data over nearly all global landmasses since August 2025. @data-acquisition-extent shows the spatial extent of the collected data. The [NISAR Reference Observation Plan](https://experience.arcgis.com/experience/6052a864cd01459393884a7f751558e3) provides a more detailed, interactive map of NISAR data acquisitions.

```{figure} ../assets/data-acquisition-extent.png
:label: data-acquisition-extent
:alt: Map of the spatial extent of NISAR data collection.
:align: center

Spatial extent of NISAR L-band data collection, highlighted in green.
<span style="font-size: 12px;">_Basemap credits: Esri, TomTom, Garmin, FAO, NOAA, USGS, (c) OpenStreetMap contributors, and the GIS User Community._</span>
```

All L-band data products processed by the mission will be available to the public through the Alaska Satellite Facility.

The nominal data release timeline as of July 2026 is described below.

(timeline-january)=
### Jan 2026: Sample products
An [initial release](https://www.earthdata.nasa.gov/news/nisar-sample-data-products-available) of 25 pre-calibration sample data products were made available on January 23, 2026. This release included one or more products of each of the nine Level 1-3 product types.

(timeline-february)=
### Feb 2026: Pre-calibration products
A [larger volume](https://www.earthdata.nasa.gov/news/nisar-release-over-100000-new-data-product-files) of pre-calibration global data products were made available on February 27, 2026. This release included over 100,000 Level 1-3 products totaling over 500 TB of science data. These datasets are marked as BETA, as they are not yet fully calibrated.

(timeline-calibrated-forward-processing)=
### Jul 2026: Provisional products
Global L-band NISAR Provisional products were released on July 20, 2026. These datasets are marked as PROVISIONAL, indicating that they are calibrated and partially validated, but processing improvements are still underway. Provisional datasets are available for all acquisitions starting from June 17, 2026, through [#TODO: add end date].

This release was the first to include [L0B RRSD](#rrsd-product-overview) products, which have a nominal latency of 2-10 hours from data acquisition to availability. Level 1-3 products have a nominal latency of 36-72 hours. Products are continuously generated and made publicly available for all areas shown in @data-acquisition-extent and in the [NISAR Reference Observation Plan](#nisar-reference-observation-plan). 

(validated-reprocessing)=
### Nov 2026: Validated reprocessing

Validated NISAR Level 0-2 products were released on November 4, 2026. This release included reprocessed products going back to [#TODO: add reprocessing start date], providing consistent products globally from the start of the science phase of the NISAR mission.

### 2027: Validated SME2 products

Once there are sufficiently long time series of validated GCOV products available to validate and refine the Level 3 Soil Moisture (SME2) products, there will be a VALIDATED SME2 collection added to the archive. Until that time, the PROVISIONAL SME2 collection will include products generated using multiple CRIDs. 


