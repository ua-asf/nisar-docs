# Instrumentation

NISAR was designed to deliver fast sampling, free and open access, and global coverage at full resolution and with polarimetric diversity. The technical innovation that allows this performance is the scan-on-receive *SweepSAR* design, conceived and refined collaboratively by NASA and the German Space Agency (DLR).

A more detailed description of the NISAR instrument design is in section 4.7 of the @nisarMissionHandbook2025.

## Bands

The L-band Synthetic Aperture Radar (L-SAR) instrument is the focus of the NASA-chartered science goals for NISAR, and provides global coverage. The L-SAR is a side-looking, fully polarimetric, interferometric SAR at a wavelength of 24 cm, with a swath width of about 240 km, an along-track resolution of 7 m, and a cross-track resolution of 2 to 8 m (depending on mode).

The S-band SAR (S-SAR) instrument, developed in a collaboration between NASA and the Indian Space Research Organization (ISRO), operates at a wavelength of 9.3 cm and is primarily used for acquisitions over India.

## Frequencies

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

## Polarization

The polarization refers to the direction that an electromagnetic wave travels. This can be horizontal, vertical, or circular. Circular polarizations, where the wave is rotating in a constant plane to the left or right, are much less commonly used for SAR sensors than the linear (horizontal or vertical) polarizations. 

The antennas of a SAR system can be configured to transmit and receive electromagnetic waves using various combinations of these polarizations. The polarimetric properties of the observed surface can reveal the structure, orientation and environmental conditions of the surface elements.

For the NISAR mission, the combination of polarizations vary based on the acquisition mode, and the 2-digit polarization code is indicated as part of the filename for each data product. The potential polarizations are as follows:
- Single polarization
  - SH: HH single-pol data
  - SV: VV single-pol data
- Dual polarization
  - DH: HH+HV dual-pol data 
  - DV: VV+VH dual-pol data
- Quad-pol data
  - QP: HH+HV+VH+VV quad-pol data
- Compact polarization (circular)
  - RH: right-circular HH data 
  - RV: right-circular VV data

```{figure} /assets/nisar-acquisition-modes.png
:label: acquisition_modes
:alt: NISAR acquisition modes
:align: center

NISAR acquisition modes
```

For interferometric NISAR product, frequency A only data are used. All other NISAR products can be acquired in a combination of frequency A and frequency B as shown above.

