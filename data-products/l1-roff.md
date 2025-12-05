# L1 ROFF

The ROFF product contains a collection of dense pixel offset layers obtained from applying incoherent cross-correlation on a pair of coarsely coregistered L1 Range Doppler Single Look Complex (RSLC) products in the range-Doppler geometry of the earlier reference RSLC product. 

The pair of RSLCs used to produce ROFF is first coarsely aligned with geometrical coregistration using the best available sensor orbit ephemeris and a DEM. The spacing, the window size, and the search radius used to generate the ROFF offsets layers for L-SAR data are organized by sensor mode and area of observation. 

Irrespective of the mode, the pixel offset layers are provided with a nominal posting of 90 m on the ground. It is assumed that pixel offset layers within ROFF share the same spacing and the same starting pixel along slant range and azimuth directions. 

Each pixel offset layer is distributed without performing any conventional post-processing operation, i.e., layers might contain offset outliers and are not low-pass filtered to reduce noise in the data.
