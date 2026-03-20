# Phase

(sar-phase)=
## SAR Phase

The phase component of the SAR dataset indicates the location of the SAR signal along its wave cycle when it returns to the sensor. This can be used as a proxy for distance, and is the basis of SAR Interferometry (InSAR). By differencing the phase values from one acquisition to another with the same footprint, InSAR allows users to identify and quantify surface deformation that occurred in the time between acquisitions. 

## InSAR

InSAR analysis can quantify differences in the line-of-sight of the sensor to the centimeter scale, making it a powerful tool for monitoring deformation over large areas. It can be used in conjunction with GNSS measurements, surveys, and LiDAR measurements to expand these high-accuracy measurements to a much broader scale. 

InSAR analysis can be used to detect and quantify surface movements or changes that cause the SAR signal to travel a different distance to interact with the scattering surface. This can be due to geophysical processes, such as volcanic or tectonic activity, or human activities, such as earth-moving for construction or extraction or subsidence or uplift due to changes in groundwater or underground reservoirs.

<!-- #TODO: Add content on time series analysis -->

## Atmospheric Impacts

Phase measurements, especially at L-band wavelengths, are sensitive to atmospheric changes from one acquisition to the next, so it is vital to consider how these changes can impact your interpretation of InSAR measurements. NISAR provides a number of resources packaged in with products such as the GUNWs that can be used for atmospheric corrections, and there are also time-series approaches that can help mitigate the impact of atmospheric conditions.

(nisar-coherence)=
## Coherence

Coherence indicates the level of correlation between the phase spectra of two SAR acquisitions. Values range from 0 to 1, with 0 being complete decorrelation and 1 being complete correlation. Areas with low correlation, where phase spectra from one acquisition to another have little to no overlap, may not generate reliable InSAR values. 

Coherence values can be used to determine the quality of a phase difference calculation, but can also serve as an indicator of change, as these differences in phase spectra are generally caused by significant disturbance to the scattering surface. 