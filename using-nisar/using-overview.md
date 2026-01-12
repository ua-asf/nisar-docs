# Using NISAR Data Overview

There are many potential usage patterns for NISAR data, from SAR scientists downloading [RRSD](#rrsd-product-overview) products to perform complex processing workflows to disaster response teams viewing [GCOV](#gcov-product-overview) products in GIS platforms. There are a range of tools and resources available for accessing, processing, analyzing and visualizing NISAR products to support this range of use cases.

## Accessing NISAR Data

NISAR data can be accessed from cloud storage, either by downloading or using cloud computing approaches to work with the data directly in the cloud. There are map-based user interfaces and programmatic solutions for finding and accessing NISAR data. Refer to the [Accessing NISAR Data](#nisar-access-overview) section for more information.

## Processing Software

The processing algorithms used for the NISAR Mission are included in [ISCE3](https://github.com/isce-framework/isce3), the third iteration of the InSAR Scientific Computing Environment (ISCE). ISCE3 is an open source library for processing spaceborne and airborne Interferometric Synthetic Aperture Radar (InSAR) data, and development is currently funded through the NISAR project. 

The NISAR Mission is using ISCE3 functionality to generate the products that are archived by ASF. This software package is also publicly available for users who want to script their own processing workflows, but this requires scientific programming expertise and an understanding of the principles of SAR acquisitions.

## GIS Software

The availability of NISAR [Level 2 (Geocoded)](#level-2-geocoded-products) and [Level 3 (Geophysical)](#level-3-geophysical-products) products makes it easy for users to work with NISAR data in GIS environments. 

The [HDF5 data format](#hdf5) of the NISAR products may be unfamiliar to some users, but there are workflows for adding NISAR layers to GIS projects and performing analysis leveraging existing raster analysis tools. 

Refer to ASF's [NISAR in GIS](https://www.earthdata.nasa.gov/learn/gis/storymaps/nisar-gis) StoryMap tutorial to learn how to work with NISAR data in ArcGIS Pro, and the [QGIS Visualization/Exploration Tutorials](https://www.earthdata.nasa.gov/learn/tutorials/work-nisar-sample-data#QGISVE) section of the [Work with NISAR Sample Data](https://www.earthdata.nasa.gov/learn/tutorials/work-nisar-sample-data) tutorial for guidance on using NISAR data in QGIS.

## Programmatic Approaches

Users who want to develop programmatic workflows to access, analyze, and visualize NISAR data can use a range of existing open-source software packages. Functions from packages designed specifically to work with SAR data can be combined with other packages with more general tools for working with raster and array data to accomplish a range of analyses and visualizations. Refer to the [Tutorials](#tutorials-overview) section for more information and available workflows. 
