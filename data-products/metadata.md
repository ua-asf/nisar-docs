# Metadata

The complete structure of the metadata is provided in the product specification.

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

:::{table} NISAR cube metadata
:label: tbl:cube-metadata-html
<table style="text-align: center; border: 2px solid black;">
    <tr>
        <th rowspan="2" style="text-align: center; border: 1px solid black;">&nbsp;</th>
        <th colspan="4" align="center" style="text-align: center; border: 1px solid black;">Level 1</th>
        <th colspan="4" align="center" style="text-align: center; border: 1px solid black;">Level 2</th>
    </tr>
    <tr>
        <th align="center" style="width: 55px; text-align: center; border: 1px solid black;">RIFG</th>
        <th align="center" style="width: 55px; text-align: center; border: 1px solid black;">ROFF</th>
        <th align="center" style="width: 55px; text-align: center; border: 1px solid black;">RSLC</th>
        <th align="center" style="width: 55px; text-align: center; border: 1px solid black;">RUNW</th>
        <th align="center" style="width: 55px; text-align: center; border: 1px solid black;">GCOV</th>
        <th align="center" style="width: 55px; text-align: center; border: 1px solid black;">GOFF</th>
        <th align="center" style="width: 55px; text-align: center; border: 1px solid black;">GSLC</th>
        <th align="center" style="width: 55px; text-align: center; border: 1px solid black;">GUNW</th>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;coordinateY</th>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;coordinateX</th>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;incidenceAngle</th>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;losUnitVectorX</th>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;losUnitVectorY</th>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;alongTrackUnitVectorX</th>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;alongTrackUnitVectorY</th>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;elevationAngle</th>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;parallelBaseline</th>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;perpendicularBaseline</th>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;slantRange</th>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;referenceSlantRange</th>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;secondarySlantRange</th>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;zeroDopplerAzimuthTime</th>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;referenceZeroDopplerAzimuthTime</th>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;secondaryZeroDopplerAzimuthTime</th>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;groundTrackVelocity</th>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;hydrostaticTroposphericPhaseScreen</th>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;wetTroposphericPhaseScreen</th>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;slantRangeSolidEarthTidesPhase</th>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
    </tr>
    <tr>
        <th style="border: 1px solid black;">&nbsp;heightAboveEllipsoid</th>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; background-color: #ccc; border: 1px solid black;">&nbsp;</td>
    </tr>
</table>
:::
