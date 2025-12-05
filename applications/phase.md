# Phase

The phase measures the location of the SAR signal along its wave cycle when it returns to the sensor. This can be used as a proxy for distance, and is the basis of SAR Interferometry (InSAR). By differencing the phase values from one acquisition to another with the same footprint, InSAR allows users to identify and quantify surface deformation that occurred in the time between acquisitions. 

InSAR analysis can quantify differences in the line-of-sight of the sensor to the centimeter scale, making it a powerful tool for monitoring deformation over large areas. It can be used in conjunction with GNSS measurements, surveys, and LiDAR measurements to expand these high-accuracy measurements to a much broader scale. 

Phase measurements, especially at L-band wavelengths, are sensitive to atmospheric changes from one acquisition to the next, so it is vital to consider how these changes can impact your interpretation of InSAR measurements. NISAR provides a number of resources packaged in with products such as the GUNWs that can be used for atmospheric corrections, and there are also time-series approaches that can help mitigate the impact of atmospheric conditions.

InSAR analysis can be used to detect and quantify surface movements or changes caused by geophysical processes or human activities that result in the signal having to travel a different distance to interact with the scattering surface. This can be due to volcanic or tectonic activity, earth-moving for construction or extraction purposes, and subsidence or uplift due to changes in groundwater or underground reservoirs.

InSAR also generates a coherence measurement, which may be useful for indicating change. If the phase spectra from one acquisition to another differ so much that they can’t be compared, that can indicate an area that has undergone such drastic change that it can’t be resolved. This indicates the quality of the phase difference calculation, but can also serve as an indicator of change.
