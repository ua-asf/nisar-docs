# Overview

The table below summarizes the characteristics of NISAR data products with respect to pixel spacing and primary as well as ancillary data layers. 

:::{table} NISAR data product overview
:label: tbl:overview-html

<table style="width: 750px; position: relative; border: 2px solid #000;">
    <tr style="vertical-align: bottom; height: 125px;">
        <th style="width: 25px; text-align: center; border: 1px solid black;">Product</th>
        <th style="width: 75px; text-align: center; border: 1px solid black;">Ground<br>spacing<br>[m]</th>
        <th style="width: 125px; height: 33px; text-align: left; transform: rotate(-90deg); transform-origin: left; position: absolute; left: 153px; top: 109px; border: 1px solid black;">&nbsp;Interferometric</th>
        <th style="width: 125px; height: 33px; text-align: left; transform: rotate(-90deg); transform-origin: left; position: absolute; left: 185px; top: 109px; border: 1px solid black;">&nbsp;Geocoded</th>
        <th style="width: 177px; height: 125px; position: absolute; left: 201px; top: 1px; border: 1px solid black;"><br><br><br><br>&nbsp;Layers</th>
        <th style="width: 177px; height: 125px; position: absolute; left: 377px; top: 1px; border: 1px solid black;"><br><br><br><br>&nbsp;Additional layers</th>
        <th style="width: 197px; height: 125px; position: absolute; left: 553px; top: 1px; border: 1px solid black;"><br><br><br><br>&nbsp;Comments</th>
    </tr>
    <tr>
        <td style="border: 1px solid black">RSLC</td>
        <td style="text-align: center; border: 1px solid black;">NA</td>
        <td style="width: 32px; border: 1px solid black">&nbsp;</td>
        <td style="width: 32px; border: 1px solid black">&nbsp;</td>
        <td style="width: 180px; border: 1px solid black">individual binary raster layers representing complex signal return for each polarization layer</td>
        <td style="width: 180px; border: 1px solid black">2D LUTs provided to convert from digital numbers to beta-naught, sigma-naught, and gamma-naught</td>
        <td style="width: 200px; border: 1px solid black">zero-Doppler geometry,<br>constant azimuth time interval and one-way slant range spacing</td>
    </tr>
    <tr>
        <td style="border: 1px solid black">GSLC</td>
        <td style="text-align: center; border: 1px solid black;">5 to 40<sup>*</sup</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="border: 1px solid black">input RSLC into a geocoded map coordinate system</td>
        <td style="border: 1px solid black">2D LUTs provided to convert from digital numbers to beta-naught, sigma-naught, and gamma-naught;<br>mask layer indicating water bodies and shadow-layover</td>
        <td style="border: 1px solid black">flattened with respect to the orbit used in the RSLC processing, which eliminates the topographic phase contribution in the GSLC</td>
    </tr>
    <tr>
        <td style="border: 1px solid black">ROFF</td>
        <td style="text-align: center; border: 1px solid black;">90</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="border: 1px solid black">along-track offset, slant range offset<br>(three layers)</td>
        <td style="border: 1px solid black">offset variances,<br>correlation surface peak,<br>cross offset variance,<br>signal-to-noise ratio</td>
        <td style="border: 1px solid black">distributed without performing any conventional post-processing operation i.e., layers might contain offsets outliers and are not low pass filtered to reduce noise in the data</td>
    </tr>
    <tr>
        <td style="border: 1px solid black">GOFF</td>
        <td style="text-align: center; border: 1px solid black;">80</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="border: 1px solid black">along-track offset, slant range offset<br>(three layers)</td>
        <td style="border: 1px solid black">offset variances,<br>correlation surface peak,<br>cross offset variance,<br>signal-to-noise ratio</td>
        <td style="border: 1px solid black">distributed without performing any conventional post-processing operation i.e., layers might contain offsets outliers and are not low pass filtered to reduce noise in the data</td>
    </tr>
    <tr>
        <td style="border: 1px solid black">RIFG</td>
        <td style="text-align: center; border: 1px solid black;">30</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="border: 1px solid black">wrapped interferogram</td>
        <td style="border: 1px solid black">coherence magnitude</td>
        <td style="border: 1px solid black">ellipsoid and topography flattened, multi-looked</td>
    </tr>
    <tr>
        <td style="border: 1px solid black">RUNW</td>
        <td style="text-align: center; border: 1px solid black;">80</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="border: 1px solid black">unwrapped interferogram</td>
        <td style="border: 1px solid black">coherence magnitude,<br>connected components,<br>ionospheric phase screen,<br>ionospheric phase screen uncertainty</td>
        <td style="border: 1px solid black">ellipsoid- and topography-flattened, multi-looked</td>
    </tr>
    <tr>
        <td rowspan="2">GUNW</td>
        <td style="text-align: center; border: 1px solid black;">80</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="border: 1px solid black">unwrapped interferogram</td>
        <td style="border: 1px solid black">coherence magnitude,<br>connected components,<br>ionospheric phase screen,<br>ionospheric phase screen uncertainty</td>
        <td style="border: 1px solid black">interpolation method during geocoding depends on layer data type</td>
    </tr>
    <tr>
        <td style="text-align: center; border: 1px solid black;">80</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="border: 1px solid black">wrapped interferogram</td>
        <td style="border: 1px solid black">&nbsp;</td>
        <td style="border: 1px solid black">&nbsp;</td>
    </tr>
    <tr>
        <td style="border: 1px solid black">GCOV</td>
        <td style="text-align: center; border: 1px solid black;">20</td>
        <td style="text-align: center; border: 1px solid black;">&nbsp;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="border: 1px solid black">polarimetric covariance terms</td>
        <td style="border: 1px solid black">mask,<br>number of looks,<br>RTC gamma to sigma factor</td>
        <td style="border: 1px solid black">radiometrically terrain-corrected gamma-naught</td>
    </tr>
    <tr>
        <td style="border: 1px solid black">SME2</td>
        <td style="text-align: center; border: 1px solid black;">200</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="text-align: center; border: 1px solid black;">&#x2714;</td>
        <td style="border: 1px solid black">three soil moisture estimates: disaggregation (DSG),<br>physical model inversion (PMI),<br>time series ratio (TSR)</td>
        <td style="border: 1px solid black">soil moisture uncertainty,<br>DSG algorithm parameters,<br>PMI crop type and vegetation water content,<br>TSR algorithm parameters</td>
        <td style="border: 1px solid black">&nbsp;</td>
    </tr>
</table>
:::
$^*$ depending on range bandwith
