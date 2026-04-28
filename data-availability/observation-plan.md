# NISAR Observation Plan

The NISAR observation plan is complex. In order to meet the broad science goals of the mission, different 
radar modes are used to collect data for different geographic areas, as described in the 
[NISAR Observation Strategy](https://science.nasa.gov/mission/nisar/observation-strategy/).

(nisar-reference-observation-plan)=
## NISAR Reference Observation Plan

The reference observation plan for the first six months of the mission is documented in Figure 4-1 of the 
[NISAR Mission Handbook](https://doi.org/10.48577/jpl.UD4HV3), which is presented here 
in @ref-obs-plan-image.

```{figure} ../assets/nisar-reference-observation-plan-handbook.png
:name: ref-obs-plan-image
:alt: NISAR Reference Observation Plan, Figure 4-1 in the [NISAR Mission Handbook](https://doi.org/10.48577/jpl.UD4HV3)
:align: left

NISAR Reference Observation Plan coverage maps for global ascending (a) and descending (b) passes, and joint L-band and S-band ascending (c), and descending (d) data takes. This plan will be in place for the initial six months of the mission. 

- The project plans to review and adjust the plan every six months, depending on science team input, available resources, and other programmatic factors. The legend describes the modes that will be employed.
- There are some variations in coverage seasonally, for example over the poles as sea ice comes and goes, but largely the acquisition plan is intended to be static geographically to allow generation of consistent time series over the life of the mission. The mnemonics for the modes follow the scheme given in Table 4-1.
- For S-band, the mnemonic scheme is similar: S:XX:MM:BBP:WW:DD:FFF. Here, the beam forming mode XX for the S-band instrument is added (DB = beamform; DR = raw channels of the beamformer; NR = no beamforming). For joint modes, the PRF scheme is left off the mnemonic because it is the same as for L-band.  
```

(observation-plan-apps)=
## Interactive Apps

The NISAR Reference Observation Plan can be explored interactively using a series of web applications. Apply filters to view the spatial extent of planned L-band acquisitions based on flight direction, track/frame, polarization, bandwidth, frequency, date, mode changes, or product type. Zoom or pan to view your area of interest, and click on a footprint to learn about the acquisition information for that frame. 

There are different applications available, one displaying the currently available set of [pre-calibration data](#feb-2026-obs-plan-app), and the other for the full [reference observation plan](#ref-obs-plan-app) once calibrated data is available. Refer to @availability-overview to view the release timeline for the different collections of data. 

Each of these applications also has a companion app optimized for viewing acquisitions over Antarctica. These apps use a south polar stereographic projection to improve the rendering of frame footprints for Antarctic acquisitions.

(feb-2026-obs-plan-app)=
### Pre-Calibration Data Apps

These applications provide an overview of the L-band NISAR images included in the @nisar-sample-data-feb data release. Click an app image or header to open it in a new tab.

#### [NISAR February 2026 Released Data - Global](https://experience.arcgis.com/experience/0042193b06104889971cd77f505190e0/)

<a href="https://experience.arcgis.com/experience/0042193b06104889971cd77f505190e0/">
<img id="obs-plan-app-feb2026-global-image" src="../assets/obs-plan-app-feb2026-global.png" alt="Click to open the NISAR February 2026 Released Data app (global view)" width="75%">
</a>

#### [NISAR February 2026 Released Data - Antarctic](https://experience.arcgis.com/experience/8d4533b5909e4ac395acaf6712f58d9f/)

<a href="https://experience.arcgis.com/experience/8d4533b5909e4ac395acaf6712f58d9f/">
<img id="obs-plan-app-feb2026-antarctic-image" src="../assets/obs-plan-app-feb2026-antarctic.png" alt="Click to open the NISAR February 2026 Released Data app (Antarctic view)" width="75%">
</a>

(ref-obs-plan-app)=
### Reference Observation Plan Apps

These applications provide an overview of the L-band NISAR acquisitions that will be available once [calibrated data is released](#timeline-calibrated-forward-processing).

#### [NISAR Reference Observation Plan - Global](https://experience.arcgis.com/experience/6052a864cd01459393884a7f751558e3)

<a href="https://experience.arcgis.com/experience/6052a864cd01459393884a7f751558e3">
<img id="obs-plan-app-calibrated-global-image" src="../assets/obs-plan-app-calibrated-global.png" alt="Click to open the NISAR Reference Observation Plan app (global view)" width="75%">
</a>

#### [NISAR Reference Observation Plan - Antarctic](https://experience.arcgis.com/experience/83942599aec64c1c8ea8a8b913d22539)

<a href="https://experience.arcgis.com/experience/83942599aec64c1c8ea8a8b913d22539">
<img id="obs-plan-app-calibrated-antarctic-image" src="../assets/obs-plan-app-calibrated-antarctic.png" alt="Click to open the NISAR Reference Observation Plan app (Antarctic view)" width="75%">
</a>



