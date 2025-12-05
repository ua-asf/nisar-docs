# Metadata

The complete structure of the metadata is provided in the product specification. Key metadata fields and data dimensions that are embedded in the structure of the respective HDF5 product file are summarized per product in [Appendix D](../appendix-d-nisar-metadata/toc.md).

The metadata cube is a three-dimensional grid designed to simplify the calculation of parameters within a geographic information system (GIS) environment. These grids are defined for all NISAR level 1 (L1) and level 2 (L2) products. Users are advised to use three-dimensional interpolation routines (for Python, use the RegularGridInterpolator function of the open-source software *scipy*) to calculate values for several parameters for useful initial data analysis within a GIS environment. The geolocation error using the grids is estimated to be 1.5 cm. Further analysis is expected to lead to a more robust error estimate.

The example below shows the geolocation grid defined for an L1 RIFG product. Using slant range, zero Doppler time, and height above ellipsoid as the grid axes serve as input to calculate the values of all other parameters.

```{literalinclude} nisar_rifg_data.json
:linenos: False
```

The L2 GCOV example below takes the x coordinates, y coordinates, and heights above the ellipsoid, spaced 500 m between grid points, as grid axes to calculate the values of all other parameters.

```{literalinclude} nisar_gcov_data.json
:linenos: False
```

The table below summarizes which parameters are available for the users’ analysis in the various NISAR L1 and L2 products. The parameters highlighted in gray indicate the input parameters for calculating the values of the remaining parameters.

```{figure} /assets/nisar-cube-metadata.png
:label: cube_metadata
:alt: NISAR cube metadata
:align: center

NISAR cube metadata
```
