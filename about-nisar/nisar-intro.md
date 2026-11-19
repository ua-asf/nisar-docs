# About NISAR

## The NISAR Mission

NISAR is a joint Earth-observing mission between the [National Aeronautics and Space Administration (NASA)](https://www.nasa.gov/) and the [Indian Space Research Organization (ISRO)](https://www.isro.gov.in/), with the goal to make global measurements of the causes and consequences of land surface changes using advanced radar imaging. Access to NISAR mission data is free and open.

The NISAR platform collects data using both [L-band](#l-band) and [S-band](#s-band) SAR sensors. NASA hosts the data acquired by the L-band sensor, and ISRO hosts the data collected by the S-band sensor.

- L-band data is collected globally, providing acquisitions over most landmasses and sea ice on a regular repeat cycle.
- S-band data is collected over select areas, as described in the [mission observation plan](#nisar-reference-observation-plan). 

### NISAR Mission Concept

The mission concept and the resulting partnership were in response to the [National Academy of Science's 2007 Decadal Survey](https://doi.org/10.17226/11820) [@decadalSurvey2007] of Earth observational priorities for the next decade. 

One of the top priorities identified in this survey was to gain data and insight in three Earth science domains:
* Ecosystems
* Deformation of Earth's Crust 
* Cryospheric Sciences

Refer to NASA's [NISAR Mission](https://science.nasa.gov/mission/nisar/) website for more information.

<a href="https://science.nasa.gov/mission/nisar/">
<img id="nisar-mission-page" src="../assets/nisar-mission-page.png" alt="NASA NISAR Mission Website Image">
</a>

### NISAR Science Objectives

The NISAR Mission Science Users' Handbook [@nisarMissionHandbook2025] defines the key scientific objectives as follows:

>NISAR addresses the needs of Solid Earth, Ecosystems, Cryospheric, and Soil Moisture science disciplines, with a specific focus on the following key scientific objectives to:
>
>1. Determine the likelihood of earthquakes, volcanic eruptions, landslides, and land subsidence
>2. Understand the dynamics of carbon storage and uptake in wooded, agricultural, wetland, and permafrost systems
>3. Understand the response of ice sheets to variations in the climate, the interaction of sea ice and climate, and impacts on sea level rise worldwide
>4. Constrain global patterns of soil moisture and their temporal variability, across a wide range of land cover types and climate regimes

### NISAR Mission Science Users' Handbook

The [NASA-ISRO SAR (NISAR) Mission Science Users' Handbook](https://doi.org/10.48577/jpl.UD4HV3) [@nisarMissionHandbook2025] provides a wealth of information about all aspects of the mission. It describes the mission goals, requirements, characteristics and instrumentation. It also provides an overview of the mission data products and the range of scientific applications supported by the mission. 

Published by [JPL](#jet-propulsion-laboratory), this valuable resource is a PDF publication available online. It is a large document that can either be viewed directly in a browser or downloaded for offline use.

Note that all references to the NISAR Mission Science Users' Handbook on this site link to the second edition, which was published in 2025. This edition supersedes the previous edition, published in 2019, and we advise users to reference this second edition instead of the older publication.

<a href="https://doi.org/10.48577/jpl.UD4HV3">
<img id="nisar-handbook-cover" src="../assets/nisar-handbook-v2-cover.png" alt="NASA-ISRO SAR (NISAR) Mission Science Users' Handbook Image" width="50%">
</a>

(jet-propulsion-laboratory)=
### Jet Propulsion Laboratory

The [Jet Propulsion Laboratory (JPL)](https://www.jpl.nasa.gov/) is located on the outskirts of Pasadena, California. Founded in 1936 by California Institute of Technology (Caltech) researchers, JPL is a research and development lab federally funded by NASA and managed by Caltech.

JPL leads the U.S. portion of the NISAR project on behalf of NASA, including project management, providing physical components of the satellite, testing, coordinating science product development, developing and processing data products, and publishing product specifications and algorithm theoretical basis documents. 

JPL generates a suite of products from NISAR mission data, ranging from Level 0 to Level 3, which ASF makes available to the public. Refer to the [data products](#data-products-overview) section of this site for more information on NISAR data products. 

(alaska-satellite-facility)=
### Alaska Satellite Facility

The [Alaska Satellite Facility (ASF)](https://asf.alaska.edu/) has been selected to archive the data from the NISAR mission. ASF maintains the NASA archive of Synthetic Aperture Radar (SAR) data from various satellites and aircraft, providing these data and associated services to the public in support of NASA’s Earth Science Data and Information System ([ESDIS](https://earthdata.nasa.gov/about/esdis-project?_ga=2.174193322.963840534.1558367114-1499519562.1541105389)) project.

ASF utilizes NASA's [Earthdata Cloud](https://www.earthdata.nasa.gov/about/earthdata-cloud-evolution) for processing, storage and distribution of the data. This environment leverages Amazon Web Service (AWS) infrastructure, allowing datasets to be accessed directly and efficiently in cloud computing workflows. 

(nisar-instrumentation)=
## NISAR Instrumentation

### SweepSAR

NISAR was designed to deliver global coverage at full resolution and with polarimetric diversity. The technical innovation that allows this performance is the scan-on-receive [SweepSAR design](https://science.nasa.gov/mission/nisar/sweepsar/), conceived and refined collaboratively by NASA and the German Space Agency (DLR).

```{figure} ../assets/sweep-sar.png
:label: sweep-sar
:alt: Figure illustrating the SweepSAR approach to imaging
:align: center

SweepSAR technique, which allows full-resolution, multipolarimetric observations across an extended swath (> 240 km). By transmitting energy across the full feed aperture, a wide swath is illuminated on the ground. Each patch element on  the feed can receive independently, allowing localization in time, hence space, of the return echo scattered from the ground. *Note: Transmit and scanning receive events overlap in time and space. Alongtrack offset shown is for clarity of presentation only*. Credit: [NISAR Mission Handbook](https://doi.org/10.48577/jpl.UD4HV3) [pg. 44, -@nisarMissionHandbook2025]
```

A more detailed description of the NISAR instrument design is in section 4.7 of the [NISAR Mission Handbook](https://doi.org/10.48577/jpl.UD4HV3) [@nisarMissionHandbook2025].

#### Pulse Repetition Frequency

SweepSAR is able to generate gapless imagery by varying the Pulse Repetition Frequency (PRF). Because the radar cannot receive echoes while it is transmitting, there are gaps in the imagery when the PRF is fixed. By varying the PRF, or _dithering_, NISAR moves the gaps around as data is acquired, allowing for interpolation across the gaps. 

Most of NISAR's acquisition modes make use of variable PRFs, generating gapless imagery. There are, however, some fixed PRF modes. In the current acquisition plan, fixed PRFs are only used for [quad-pol acquisitions](#fixed-prf-quad-pol).

(fixed-prf-quad-pol)=
##### Quad-pol acquisitions 

All NISAR [quad-pol](#nisar-polarization) observations currently use a fixed PRF because of the operational constraints of quad-pol acquisitions. Using variable PRFs degrades image quality, so the tradeoff for high image quality is the presence of bands of data gaps in the imagery, as seen in @quad-pol-gaps-image.

```{figure} ../assets/quad-pol-gaps.png
:label: quad-pol-gaps-image
:alt: Figure showing the data gaps caused by the fixed PRF used to acquire a quad-pol NISAR image
:align: center

The data gaps caused by the fixed PRF used for quad-pol acquisitions are visible as black bands in this Frequency A HHHH covariance dataset from the quad-pol NISAR<wbr>_L2<wbr>_PR<wbr>_GCOV<wbr>_026<wbr>_055<wbr>_D<wbr>_068<wbr>_2005<wbr>_QPDH<wbr>_A<wbr>_20260724T003402<wbr>_20260724T003437<wbr>_P05023<wbr>_N<wbr>_F<wbr>_J<wbr>_001.h5 product.
```

These gaps are moved from cycle to cycle to allow complete coverage over time, but any individual image will have some data missing. This is a permanent and expected feature of standard NISAR quad-pol acquisitions. 

The NISAR mission is experimenting with variable PRF acquisitions, and products generated using this approach may be made available in the future, but this experimental mode is still being evaluated.

### Look Direction

SAR sensors are always [side looking](https://www.earthdata.nasa.gov/learn/earth-observation-data-basics/sar#toc-flight-and-directional-terminology), with data being collected at an angle from the nadir (@observation-geometry-diagram). 

```{figure} ../assets/observation-geometry.png
:label: observation-geometry-diagram
:alt: Figure illustrating the observation geometry of the NISAR platform
:align: center
:width: 30%

The observing geometry of the NISAR platform, showing the area imaged by the 240 km NISAR swath relative to the nadir. _Diagram modified from the [Harnessing NISAR: Next-Generation Radar Observations for Earth Applications](https://www.earthdata.nasa.gov/learn/trainings/harnessing-nisar-next-generation-radar-observations-earth-applications) course from the NASA Applied Remote Sensing Training Program (ARSET), 2026._
```

NISAR is a left-looking mission, which allows for complete coverage over Antarctica. The tradeoff is an area around the North Pole where coverage is not available (@arctic-gap). 

```{figure} ../assets/north-pole-hole.png
:label: arctic-gap
:alt: Figure illustrating the area around the North Pole where NISAR acquisitions are not available
:align: center
:width: 75%

Area around the North Pole where NISAR aquisitions are not available, as visualized in the [NISAR Reference Observation Plan app](#ref-obs-plan-app).
```

### Bands

The NISAR mission collects data using two different SAR sensors, each acquiring data in a different [band](https://www.earthdata.nasa.gov/learn/earth-observation-data-basics/sar#toc-the-roles-of-frequency-and-wavelength), or range of wavelengths.

(l-band)=
#### L-Band

The L-band Synthetic Aperture Radar (L-SAR) instrument is the focus of the NASA-chartered science goals for NISAR, and provides global coverage. The L-SAR instrument operates at a wavelength of 24 cm. 

Most L-band acquisitions have a swath width of about 240 km, an along-track resolution of 7 m, and a cross-track resolution of 2 to 8 m (depending on mode).

(s-band)=
#### S-Band

The S-band SAR (S-SAR) instrument, developed in a collaboration between NASA and the Indian Space Research Organization (ISRO), operates at a wavelength of 9.3 cm and is primarily used for acquisitions over India.

(nisar-frequencies)=
### Frequencies

NISAR is equipped to acquire data in two slightly different frequencies at each bandwidth. @tbl:areas-html summarizes the Frequency A and the Frequency B settings that define the acquisition modes. 

Frequency A is the primary frequency used for generating scientific products, while Frequency B data is collected primarily for use in atmospheric corrections. Many NISAR products include datasets for both Frequency A and Frequency B data, and some users may find the Frequency B data useful in its own right. 

Frequency B datasets are generally posted at a coarser pixel spacing than Frequency A datasets, so analysis workflows requiring higher resolution are better served by the Frequency A data. The larger pixels of Frequency B datasets result in them being much smaller files, which take less time to download and render, making them useful for regional analysis workflows or a quick look at the data.

:::{table} Center frequencies (MHz) for NISAR acquisition bandwidths
:label: tbl:areas-html

<table style="border: 2px solid #000">
    <tr>
        <td rowspan="2" align="center" style="vertical-align: bottom; border: 1px solid #000"><strong>L-band bandwidth [MHz]</strong></td>
        <td colspan="2" align="center" style="border: 1px solid #000"><strong>Center frequency [MHz]</strong></td>
    </tr>
    <tr>
        <td align="center" style="border: 1px solid #000"><strong>Frequency A</strong></td>
        <td align="center" style="border: 1px solid #000"><strong>Frequency B</strong></td>
    </tr>
    <tr>
        <td align="center" style="border: 1px solid #000">77</td>
        <td align="center" style="border: 1px solid #000">1257.5</td>
        <td align="center" style="border: 1px solid #000">NA</td>
    </tr>
    <tr>
        <td align="center" style="border: 1px solid #000">40+5</td>
        <td align="center" style="border: 1px solid #000">1239</td>
        <td align="center" style="border: 1px solid #000">1293.5</td>
    </tr>
    <tr>
        <td align="center" style="border: 1px solid #000">20+5</td>
        <td align="center" style="border: 1px solid #000">1229</td>
        <td align="center" style="border: 1px solid #000">1293.5</td>
    </tr>
    <tr>
        <td align="center" style="border: 1px solid #000">20+20</td>
        <td align="center" style="border: 1px solid #000">1229</td>
        <td align="center" style="border: 1px solid #000">1286</td>
    </tr>
    <tr>
        <td align="center" style="border: 1px solid #000">5+5</td>
        <td align="center" style="border: 1px solid #000">1221.5</td>
        <td align="center" style="border: 1px solid #000">1236.5</td>
    </tr>
</table>
:::

### Polarization

The polarization refers to the direction that an electromagnetic wave travels. This can be horizontal, vertical, or circular. Circular polarizations, where the wave is rotating in a constant plane to the left or right, are much less commonly used for SAR sensors than linear (horizontal or vertical) polarizations. 

<!-- Add figure or link to polarization section in hyp3-docs or reference https://www.earthdata.nasa.gov/learn/earth-observation-data-basics/sar#toc-polarization-and-scattering-mechanisms -->

The antennas of a SAR system can be configured to transmit and receive electromagnetic waves using various combinations of these polarizations. The polarimetric properties of the observed surface can reveal the structure, orientation and environmental conditions of the surface elements.

Signals that are transmitted and received in the same polarization are called co-polarized (co-pol). Signals that are received in a different polarization from the transmitted polarization are called cross-polarized (cross-pol).

(nisar-polarization)=
#### NISAR Polarimetric Channels

For the NISAR mission, the polarimetric channels available in a product will vary based on the acquisition mode. The 2-digit polarization code, indicating the transmit polarization followed by the receive polarization, is indicated as part of each dataset name.

Each product filename indicates the polarimetric channels available for the datasets contained in that product. Refer to [NISAR Naming Conventions](#naming-convention-overview) to see where the polarization is indicated in the filename for different product types. 

The potential polarization configurations for NISAR products are as follows:

- ##### Single polarization (single-pol)
  - SH: HH single-pol data
  - SV: VV single-pol data
- ##### Dual polarization (dual-pol)
  - DH: HH+HV dual-pol data 
  - DV: VV+VH dual-pol data
- ##### Quad polarization (quad-pol)
  - QP: HH+HV+VH+VV quad-pol data
- ##### Compact polarization (circular)
  - RH: right-circular HH data 
  - RV: right-circular VV data

<style>section {page-break-before: avoid}</style>