# Data Format: HDF5

(hdf5)=
## What is HDF5?

All NISAR standard products are in [Hierarchical Data Format version 5 (HDF5)](https://www.hdfgroup.org/solutions/hdf5/). HDF5 is a programming library and file format designed to store, organize, and access large scientific datasets. NISAR uses HDF5 to systematically organize radar data and metadata in a way that is both efficient and easy to read, share, and analyze.

:::{caution}Accessing NISAR HDF5 files
While the files are stored in HDF5 format, the internal structure of the NISAR products is compliant with the [Climate and Forecast (CF) metadata convention](https://cfconventions.org/) of the Network Common Data Form (netCDF) format. This can cause problems when using some HDF5 drivers to read the data. While ArcGIS Pro introduced support for reading NISAR HDF5 files with version 3.4.0, there is not yet a NISAR-compliant HDF5 reader for GDAL.

Those who use GDAL to read files for use in QGIS or programmatic workflows can replace the `.h5` NISAR product extension with `.nc`. This allows GDAL to recognize the spatial coordinate system and project the file appropriately. Refer to [ASF’s documentation on workarounds](https://www.earthdata.nasa.gov/learn/tutorials/work-nisar-sample-data) for accessing NISAR HDF5 files.
:::

HDF was originally developed by the University of Illinois' National Center for Supercomputing Applications (NCSA) to support data sharing within the scientific community. HDF5 represents a significant redesign compared to earlier versions of HDF, with a more flexible and powerful internal structure. For additional details, users can consult the official HDF documentation at
<https://support.hdfgroup.org/documentation/>.

At a high level, an HDF5 file functions as a container that organizes data into a hierarchy of objects, such as **{abbr}`groups(A folder within an HDF5 file)`**, **{abbr}`datasets(The actual data values stored in an HDF5 file)`**, and **{abbr}`datatypes(The type and format of data)`**. In general, radar layers are organized into two groups: **{abbr}`frequencyA(Lower portion of the radar bandwidth)`**/ and (potentially) **{abbr}`frequencyB(Higher portion of the radar signal)`**/. Note that nothing is stored at the root `/`.

## Groups

An HDF5 **{abbr}`group(A folder within an HDF5 file)`** is a folder within an HDF5 file. Groups can hold datasets, datatypes, and other groups (subfolders). In essence, groups act like directories on computers. In a NISAR product, datasets are organized through nesting. For example, in a NISAR GCOV product, a dataset may be stored at a path such as:

```
/science/LSAR/GCOV/grids/frequencyA/HH
```

In this path, `science`, `LSAR`, `GCOV`, `grids`, and `frequencyA` are groups, and `HH` is a dataset contained within the `frequencyA` group.

## Datasets

An HDF5 **{abbr}`dataset(A collection of data values stored in an HDF5 file)`** is where the actual data lives. This might be an array or a table stored within the HDF5 file. Each dataset will include the data, a **{abbr}`dataspace(Describing the shape of the data)`**, a **{abbr}`datatype(What values are: integers, floats, etc)`**, and additional (optional) attributes such as units, range, time, and other descriptions.

## Attributes

An HDF5 **attribute** is a small piece of information that describes a **{abbr}`group(A folder within an HDF5 file)`** or **{abbr}`dataset(A collection of data values stored in an HDF5 file)`**. Note that an attribute does not store the data itself. Attributes provide important context that help correctly interpret values within a dataset. Common examples include:
- Units of measurement
- Descriptions of what the data represent
- Valid ranges, dates of acquisition
- Processing details

Storing this information with the data helps ensure that datasets can be understood and used correctly without relying on external documentation.

## Datatypes

An HDF5 datatype describes the kind of data that is being stored. A datatype explains both how to interpret a dataset and how it is stored. Datatypes fall into three categories: **{abbr}`atomic datatypes(Basic building blocks)`**, **{abbr}`composite datatypes(Combinations of atomic types)`**, and **{abbr}`named datatypes(Ways of storing and sharing datatypes)`**.

A summary of some important datatypes is given below. For more details on HDF5 datatypes and their uses, see the official HDF5 documentation on datatypes:
<https://support.hdfgroup.org/documentation/hdf5/latest/_h5_t__u_g.html>.

### Atomic Datatypes

**{abbr}`Atomic datatypes(Basic building blocks)`** are typically the simplest datatypes. They serve as building blocks for more complex datatypes. Common atomic datatypes include:
- Time
- Bitfield
- String
- Reference
- Opaque
- Integer
- Float

**{abbr}`Derived datatypes(Customized versions of atomic datatypes)`** are customized atomic types, commonly used for N-bit integers, floating-point formats, and other nonstandard data representations. They enable efficient and precise storage when data do not conform to standard numeric formats. Derived datatypes are useful because they:
- Allow custom storage with specific bit lengths
- Support values that do not follow standard integer or floating-point formats
- Preserve the original format in which the data were recorded

### Composite Datatypes

Some important **{abbr}`composite datatypes(Combinations of atomic types)`** are described below:

**Array datatypes** represent multidimensional arrays with a fixed shape.

- *NISAR example:* a fixed-size array used to store a per-pixel covariance matrix in a GCOV product, where each pixel always contains the same number of polarization or frequency components.

**Variable-length datatypes** represent variable-length, one-dimensional arrays of elements.

- *NISAR example:* a variable-length array used to store lists of contributing looks, burst indices, or quality flags, where the number of entries may vary between pixels.

**Compound datatypes** represent collections of named fields, each with its own datatype.

- *NISAR example:* storing several related per-pixel values together (e.g., coherence, incidence angle, and a validity flag) as one record instead of separate datasets.

**Enumeration datatypes** map integer values to a predefined set of named labels, improving user readability and consistency.

- *NISAR example:* using named labels such as `nominal`, `low_quality`, or `invalid` to represent processing or quality states instead of raw numeric codes.

### Named Datatypes

**{abbr}`Named datatypes(Ways of storing and sharing datatypes)`** are stored as objects within an HDF5 file. Any datatype (atomic, derived, or composite) can be named or referenced throughout the file.
Naming allows datatypes to be:
- Shared across datasets and attributes
- Reused simply and consistently
