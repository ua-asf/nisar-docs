# Frequencies and polarizations

NISAR is equipped to acquire data in two slightly different frequencies. The table below summarizes the frequency A and the frequency B settings that define the acquisition modes.

:::{table} NISAR acquisition modes
:label: tbl:areas-html

<table style="border: 2px solid #000">
    <tr>
        <td rowspan="2" align="center" style="vertical-align: bottom; border: 1px solid #000"><strong>L-band bandwdith [MHz]</strong></td>
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

The polarization refers to the direction that an electromagnetic wave travels. This can be horizontal (left to right), vertical, (up and down), or circular (rotating in a constant plane left or right). The antennas of the SAR system can transmit and receive electromagnetic waves with the various polarizations. These polarimetric properties of the observed surface can reveal the structure, orientation and environmenal conditions of the surface elements.

For the NISAR mission, the following polarizations have been selected. The single polarizations (SH for HH polarized data and SV for VV polarized data), the dual polarizations (DH for HH+HV dual-polarized data and DV for VV+VH dual-polarized data) as well as quad-polal data (HH+HV+VH+VV) have been used in the past. The compact polarization (CP) introduces circular polarization (RH for right-circular HH data and RV for right-circular VV) has not been used routinely with satellite data.

```{figure} /assets/nisar-acquisition-modes.png
:label: acquisition_modes
:alt: NISAR acquisition modes
:align: center

NISAR acquisition modes
```

For interferometric NISAR product, frequency A only data are used. All other NISAR products can be acquired in a combination of frequency A and frequency B as shown above.

