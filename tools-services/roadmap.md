# Roadmap

(tools-services-roadmap)=
## Tools and Services Roadmap

ASF will be developing a range of NISAR tools and services as more NISAR data becomes available. Development effort is underway for some of these tools and services, others are slated for development in future cycles, and others are stretch goals that are not currently funded for development.

We will update this page as efforts are released and new work is undertaken. If you would like to advocate for specific tools and services, please post to the [Earthdata Forum](#nisar-in-earthdata-forum). We value user input, and will take it into consideration as we prioritize future development efforts. 

### Scheduled Development

@tbl:scheduled-work presents development efforts that are currently underway or planned for the near future.

:::{table} Tools and Services Development Schedule
:label: tbl:scheduled-work
:align: center

| Tool or Service                                         | Type                       | Description                                                                               | Development Status |
|---------------------------------------------------------|----------------------------|-------------------------------------------------------------------------------------------|--------------------|
| NISAR GCOV Variable Subsetting                          | [Harmony](#ed-harmony)     | Extract variable(s) from an HDF5 file, and save as Cloud-Optimized GeoTIFF(s)             | In Progress        |
| NISAR GCOV Worldview Visualization                      | [Worldview](#ed-worldview) | Daily RGB Decomposition mosaics of GCOV acquisitions available in NASA Worldview          | In Progress        |
| NISAR GCOV Image Service                                | [EGIS](#ed-egis)           | Image service of GCOV acquisitions published to Earthdata GIS                             | Pending            |
| NISAR GCOV Variable Spatial Subsetting and Reprojection | [Harmony](#ed-harmony)     | Clip variable COG to specified spatial extent and optionally change the output projection | Pending            |
| NISAR GCOV Spatial Subsetting                           | [Harmony](#ed-harmony)     | Clip full HDF5 file to specified spatial extent                                           | Pending            |

:::

### Unscheduled Development

@tbl:unscheduled-work presents development efforts that we intend to undertake in the longer term. 

:::{table} Tools and Services Development List
:label: tbl:unscheduled-work
:align: center

| Tool or Service                              | Type                       | Description                                                                   |
|----------------------------------------------|----------------------------|-------------------------------------------------------------------------------|
| Variable Subsetting for other NISAR products | [Harmony](#ed-harmony)     | Extract variable(s) from an HDF5 file, and save as Cloud-Optimized GeoTIFF(s) |
| Spatial Subsetting for other NISAR products  | [Harmony](#ed-harmony)     | Clip full HDF5 file or individual variable COG(s) to specified spatial extent |
| Additional Worldview visualizations          | [Worldview](#ed-worldview) | Publish additional visualization layers for display in Worldview              |


:::

### Potential Development

@tbl:unfunded-work presents tools and services that would be valuable to the user community, but are not currently eligible for development using DAAC funding.   

:::{table} Unfunded Work
:label: tbl:unfunded-work
:align: center

| Tool or Service      | Type                                      | Description                                                                                      |
|----------------------|-------------------------------------------|--------------------------------------------------------------------------------------------------|
| Custom GUNW products | [HyP3](https://hyp3-docs.asf.alaska.edu/) | On-demand generation of GUNW products commensurate with mission products using custom date pairs |
|                      |                                           |                                                                                                  |