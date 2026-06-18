---
short_title: Urgent Response
---

# NISAR Urgent Response Products

(urgent-response-product-overview)=
## Urgent Response Product Overview

NISAR is a powerful tool for monitoring surface dynamics, but most standard NISAR products are not made available until 36-72 hours after data acquisition.

NISAR Urgent Response (UR) products provide expedited processing in response to major events or natural disasters, such as earthquakes, volcanic activity, flooding, or wildfires. Acquisitions designated for UR data delivery will be flagged for rapid downlink and expedited processing to provide [lower-latency](#ur-latency) data in support of response efforts.

UR products use lower-quality orbit ephemeris files for product processing than are used to process standard Production (PR) products, and do not have all atmospheric corrections applied. This may impact data quality, but allows the UR products to be made available much more quickly than PR products. Users should consider whether these tradeoffs are acceptable for their use case. 

(ur-latency)=
### Latency

Processing time for UR products varies based on product level, from 2 hours for [Level 0](#level-0-unfocused-raw-products) (raw) products to 6 hours for [Level 2](#level-2-geocoded-products) (geocoded) products. Level 3 products are not generated as part of the UR workflow. 

Refer to @tbl:ur-processing-estimates for a comparison of data processing latency between PR and UR products.

:::{table} Processing time estimate comparisons for Production (PR) and Urgent Response (UR) products 
:label: tbl:ur-processing-estimates
:align: center

| Product          | PR Best Estimate | UR Best Estimate |
|------------------|------------------|------------------|
| L0               | 1-12 hours       | 2 hours          |
| L1               | 36-72 hours      | 4 hours          |
| L2               | 36-72 hours      | 6 hours          |

:::

### Tasking

The NISAR mission system is capable of providing revised scheduling for new acquisitions in response to an event or an event forecast notification, and delivering data on an expedited timeline. This capability will be used when possible, providing that it does not interfere with the base [NISAR observation plan](#nisar-reference-observation-plan).

In most cases, UR products will be generated for acquisitions that are already in the reference observation plan. The acquisitions will simply be prioritized for downlink and flagged for expedited processing. Only in rare circumstances would additional acquisitions be considered.

NISAR's Smart Tasking Tool triggers UR requests automatically in response to:

- Significant earthquakes 
    - Earthquake with USGS [Prompt Assessment of Global Earthquakes for Response (PAGER)](https://earthquake.usgs.gov/data/pager/background.php) level of Red or Orange
    - Earthquake is in U.S. or India and has a PAGER level of Yellow
    - Earthquake is in U.S. or India and is greater than 7.0 magnitude and less than 50 km deep
- Volcanic events that trigger [USGS Volcano Notifications for Aviation](https://volcanoes.usgs.gov/hans-public/) levels of Orange or Red

UR products can also be manually requested by authorized users at government agencies such as USGS and NOAA.

### Naming Convention

UR products use the same [naming conventions](#naming-convention-overview) as standard NISAR products. They can be identified by the **Product Identifier** component, which is `UR` for Urgent Response instead of `PR` for Production.

Example RSLC UR product filename:

_NISAR_L1__***UR***__RSLC_001_005_A_219_4020_SVNA_A_20220104T182346_20220104T183426_P01101_M_F_J_001.h5_

### Ancillary Data 

UR products include lower precision orbit files and have fewer ancillary data layers than PR products. UR products are processed using Forecast Orbit Ephemera (FOE), which are preliminary predicted and lowest data quality of the @orbit-ephemeris-datasets. A comparison of ancillary data layers in Production and UR products is described in @tbl:ur-ancillary-data-layers. 

:::{table} Ancillary data layers available for Production (PR) and Urgent Response (UR) products 
:label: tbl:ur-ancillary-data-layers
:align: center

| Data Layer                                                      | PR Products                                                          | UR Products                    |
|-----------------------------------------------------------------|----------------------------------------------------------------------|--------------------------------|
| Orbit Ephemeris                                                 | Near-Realtime Orbit Ephemeris (NOE) and Medium Orbit Ephemeris (MOE) | Forecast Orbit Ephemeris (FOE) |
| Radar Pointing                                                  | Near-Realtime Radar Pointing (NRP) and Precise Radar Pointing (PRP)  | Forecast Radar Pointing (FRP)  |
| Geolocation Correction using Ionospheric Total Electron Content | Yes                                                                  | No                             |
| Tropospheric Correction                                         | Yes                                                                  | No                             |

:::

## Finding UR Products 

UR products can be found using the same [search and discovery mechanisms](#nisar-access-overview) as PR products. UR products are available for 30 days, after which they are removed from the archive and only the standard PR products for that acquisition will be available. 

(ur-vertex)=
### Vertex

To search for UR products in [Vertex](#vertex-overview), select `Urgent Response` under the **Product Configuration** filter in the **Product Filters** section, as shown in @vertex-urgent-response-filter. 

```{figure} ../assets/vertex-urgent-response-filter.png
:label: vertex-urgent-response-filter
:alt: Screenshot of the Urgent Response filter in Vertex selected in the Product Configuration menu. 
:align: center

Search for Urgent Response products in Vertex by selecting `Urgent Response` in the **Product Configuration** dropdown menu in the **Product Filters** section.  
```

(ur-earthdata-search)=
### Earthdata Search

The easiest way to search for UR datasets in [Earthdata Search](#earthdata-search-overview) is to type `nisar_ur` into the search bar. This will return only the NISAR UR collections in your search results. 

```{figure} ../assets/earthdata-search-ur.png
:label: earthdata-urgent-response-filter
:alt: Screenshot of the Urgent Response results in Earthdata Search. 
:align: center

Search for Urgent Response products in Earthdata Search by typing `nisar_ur` into the search bar.
```

Unlike the PR products, there is one NISAR UR collection for each [product level](#nisar-product-levels), rather than a collection for each product type. As such, different product types may be included in each UR collection.
