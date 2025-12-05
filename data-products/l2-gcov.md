# L2 GCOV

The GCOV product is an L2 product derived from the L1 Range Doppler Single Look Complex (RSLC) product, providing terrain-corrected polarimetric covariance projected onto a predefined UTM or polar stereographic projection system grid. RSLC radar samples, organized as a polarimetric scattering vector, are cross-correlated with the scattering vector’s conjugate transpose, originating the polarimetric covariance matrix expressed in the same grid as the RSLC range-Doppler grid. 

The magnitude of the resulting polarimetric covariance terms is strongly affected by the topography, with areas facing the sensor becoming brighter and areas away from the sensor turning darker in the images, biasing covariance measurements. To reduce the effect of the topography, an area-based radiometric terrain correction (RTC) is applied over the covariance terms, normalizing the backscatter coefficient beta0 to gamma0. The normalized covariance terms are then geocoded onto the output grid using area-based adaptive multi-looking. 

```{figure} /assets/nisar-gcov.png
:label: covariance
:alt: Covariance polarimetric matrix elements
:width: 400px
:align: left

Covariance polarimetric matrix elements
```

Since the polarimetric covariance matrix is Hermitian, only the upper triangular covariance terms are provided. The diagonal terms of the polarimetric covariance matrix (highlighted in darker gray) are real-valued (HHHH, HVHV, VHVH, and VVVV, or RHRH and RVRV), representing the radar backscatter associated with each polarimetric channel. The off-diagonal terms of the polarimetric covariance matrix (highlighted in lighter gray) are complex-valued (HHHV, HHVH, HHVV, HVVH, and VHVV, or RHRV) and may or may not be present depending on the GCOV processing mode.
