# Frequencies and polarizations

NISAR is equipped to acquire data in two slightly different frequencies. The table below summarizes the frequency A and the frequency B settings that define the acquisition modes.

:::{table} NISAR acquisition modes
:label: tbl:areas-html

<table>
    <tr>
        <td><strong>L-band bandwdith [MHz]</strong></td>
        <td colspan="2" align="center"><strong>Center frequency [MHz]</strong></td>
    </tr>
    <tr>
        <td></td><td><strong>Frequency A</strong></td>
        <td><strong>Frequency B</strong></td>
    </tr>
    <tr><td>77</td><td>1257.5</td><td>NA</td></tr>
    <tr><td>40+5</td><td>1239</td><td>1293.5</td></tr>
    <tr><td>20+5</td><td>1229</td><td>1293.5</td></tr>
    <tr><td>20+20</td><td>1229</td><td>1286</td></tr>
    <tr><td>5+5</td><td>1221.5</td><td>1236.5</td></tr>
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

