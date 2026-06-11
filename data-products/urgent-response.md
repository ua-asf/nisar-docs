# NISAR Urgent Response Products

##  Urgent Response Product Overview
NISAR Urgent Response (UR) products provide expedited processing in response to major events or natural disasters, such as earthquakes, volcanic activity, flooding, or wildfires. Data delivery of UR products will be flagged for rapid downlink and processing to provide low-latency data to support urgent response.

Within 6 hours of acquisition, data should be processed to Level-2 productions. Each product will be available for 30 days. A comparison of UR processing time estimates compared to nominal products is available in @tbl:ur-processing-estimates.

:::{table} Processing time estimate comparisons for Production and Urgent Response products 
:label: tbl:ur-processing-estimates
:align: center

| Product          | Production Best Estimate | Urgent Response Best Estimate |
|------------------|--------------------------|-------------------------------|
| L0               | 12 Hours                 | 2 Hours                       |
| L1               | 2 Days                   | 4 Hours                       |
| L2               | 3 Days                   | 6 Hours                       |
| L3 Soil Moisture | 4 Days                   | N/A                           |

:::

UR requests are managed through a Smark Tasking Tool, where automated UR requests are triggered by earthquakes and volcanic events. UR products can also be manually requested by authorized users at US government agencies such as USGS and NOAA. Note that NISAR will not acquire data that would not have otherwise been acquired and that UR designation only prioritizes downlinking and processing for acquisitions already in the NISAR acquisition plan. 

### Naming Convention
UR products use the same naming convention as standard @naming-conventions, but the `Product Identifier` parameter will be `UR` and the `Location` will be `J`, since these products are processed at the Jet Propulsion Laboratory.  For example, a RSLC UR product would have the name: 

`NISAR_L1_`**UR**`_RSLC_001_005_A_219_4020_SVNA_A_20220104T182346_20220104T183426_P01101_M_F_`**J**`_001.h5`

### Ancillary Data 
Expedited processing will include lower quality precision orbit files and have fewer ancillary data layers than standard Production products. UR products are processed using Forcast Orbit Ephemera (FOE), which are preliminary predicted and lowest data quality of the @orbit-ephemeris-datasets. A comparison of ancillary data layers in Production and UR products is described in @tbl:ur-ancillary-data-layers. 

:::{table} Ancillary data layers available for Urgent Response and Production products 
:label: tbl:ur-ancillary-data-layers
:align: center

| Data Layer                                                      | Production Products                                                  | Urgent Response Products       |
|-----------------------------------------------------------------|----------------------------------------------------------------------|--------------------------------|
| Orbit Ephemeris                                                 | Near-Realtime Orbit Ephemeris (NOE) and Medium Orbit Ephemeris (MOE) | Forecast Orbit Ephemeris (FOE) |
| Radar Pointing                                                  | Near-Realtime Radar Pointing (NRP) and Precise Radar Pointing (PRP)  | Forecast Radar Pointing (FRP)  |
| Geolocation Correction using Ionospheric Total Electron Content | Yes                                                                  | No                             |
| Tropospheric Correction                                         | Yes                                                                  | No                             |

:::

### Finding UR Products in Vertex
Once processed, UR products will be available through @vertex. To filter for UR products, select the **Urgent Response** filter option under **Product Configuration** in **Product Filters**, as shown in @vertex-urgent-response-filter. 

```{figure} ../assets/vertex-urgent-response-filter.png
:label: vertex-urgent-response-filter
:alt: Screenshot of the Urgent Response filter in Vertex selected in the Product Configuration menu. 
:align: center

Search for Urgent Response products in Vertex by selecting Urgent Response in the Product Configuration dropdown menu in the Product Filters section.  
```

