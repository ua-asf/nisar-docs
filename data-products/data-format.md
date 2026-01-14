# Data Format

(hdf5)=
## HDF5

All NISAR standard products are in the [Hierarchical Data Format version 5 (HDF5)](https://www.hdfgroup.org/solutions/hdf5/). HDF5 is a general-purpose file format and programming library for storing scientific data. The flexible format allows establishing structure to data and metadata. 

While the files are stored in HDF5 format, the internal structure of the NISAR products is compliant with the [Climate and Forecast (CF) metadata convention](https://cfconventions.org/) of the Network Common Data Form (netCDF) format. This can cause problems when using some HDF5 drivers to read the data. While ArcGIS Pro introduced support for reading NISAR HDF5 files with version 3.4.0, there is not yet a NISAR-compliant HDF5 reader for GDAL.

Those who use GDAL to read files for use in QGIS or programmatic workflows can  replace the ‘.h5’ NISAR product extension to ‘.nc’. This allows GDAL to recognize the spatial coordinate system and project the file appropriately. Refer to [ASF’s documentation on workarounds](https://www.earthdata.nasa.gov/learn/tutorials/work-nisar-sample-data) for accessing NISAR HDF5 files.
