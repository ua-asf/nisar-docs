---
short_title: ASF Roadmap
---

# ASF Development Roadmap

(tools-services-roadmap)=
## Tools and Services Roadmap

ASF will be developing a range of NISAR tools and services as more NISAR data becomes available. Development effort is underway for some of these tools and services, while others are slated for development in future cycles.

We will update this page as efforts are released and new work is undertaken. If you would like to advocate for specific tools and services, please post to the [Earthdata Forum](#nisar-in-earthdata-forum). We value user input, and will take it into consideration as we prioritize future development efforts. 

### Scheduled Development

@tbl:scheduled-work presents development efforts that are currently underway or planned for the near future.

:::{table} Tools and Services Development Schedule
:label: tbl:scheduled-work
:align: center

| Tool or Service                                                        | Type                       | Description                                                                                                             | Development Status | Target Release |
|------------------------------------------------------------------------|----------------------------|-------------------------------------------------------------------------------------------------------------------------|--------------------|----------------|
| NISAR GCOV [Dataset](#h5-datasets) Subsetting                          | [Harmony](#ed-harmony)     | Extract individual [dataset](#h5-datasets) layer(s) from an HDF5 file, and save as Cloud-Optimized GeoTIFF(s)           | In Progress        | June 2026      |
| NISAR GCOV Worldview Visualization                                     | [Worldview](#ed-worldview) | Daily RGB Decomposition mosaics of GCOV acquisitions available in NASA Worldview                                        | In Progress        | July 2026      |
| NISAR GCOV Image Service                                               | [EGIS](#ed-egis)           | Image service of GCOV acquisitions published to Earthdata GIS                                                           | Pending            | Q3 2026        |
| NISAR GCOV [Dataset](#h5-datasets) Spatial Subsetting and Reprojection | [Harmony](#ed-harmony)     | Clip an extracted [dataset](#h5-datasets) layer to specified spatial extent and optionally change the output projection | Pending            | Q4 2026        |
| NISAR GCOV Spatial Subsetting                                          | [Harmony](#ed-harmony)     | Clip full HDF5 file to specified spatial extent                                                                         | Pending            | 2027           |

:::

### Unscheduled Development

@tbl:unscheduled-work presents development efforts that we intend to undertake in the longer term. 

:::{table} Tools and Services Development List
:label: tbl:unscheduled-work
:align: center

| Tool or Service                                                       | Type                       | Description                                                                                                                                                                                                                                        |
|-----------------------------------------------------------------------|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Dataset](#h5-datasets) Subsetting for other NISAR Level 2/3 products | [Harmony](#ed-harmony)     | Extract [dataset(s)](#h5-datasets) from an HDF5 file, and save as Cloud-Optimized GeoTIFF(s)                                                                                                                                                       |
| Spatial Subsetting for other NISAR Level 2/3 products                 | [Harmony](#ed-harmony)     | Clip full HDF5 file or individual [dataset(s)](#h5-datasets) COG(s) to specified spatial extent                                                                                                                                                    |
| Additional Worldview visualizations                                   | [Worldview](#ed-worldview) | Publish additional visualization layers for display in Worldview                                                                                                                                                                                   |
| Custom GUNW products                                                  | [HyP3](#ed-hyp3)           | On-demand generation of GUNW products commensurate with mission products using custom date pairs, in collaboration with the [VolcSARvatory](https://www.uaf.edu/news/alaska-developed-volcano-monitoring-system-will-expand-across-us.php) project |
| On Demand Level 3 Algorithms                                          | [HyP3](#ed-hyp3)           | On-demand generation of Level 3 products using the [NISAR Science Algorithms](https://gitlab.com/nisar-science-algorithms), in collaboration with the [Earth Action](https://appliedsciences.nasa.gov/) program through the NISAR Bridge project   |

:::
