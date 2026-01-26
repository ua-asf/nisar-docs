---
short_title: Available Data
---

# Available NISAR Data

NISAR launched July 30, 2025, and has been successfully collecting data through its Commissioning phase and into the Science phase. The calibration-validation process is underway, and a small collection of sample data generated from NISAR acquisitions is now available to the public.

(nisar-sample-data-jan)=
## NISAR Sample Data: January 2026

{button}`Find NISAR Sample Data <https://search.asf.alaska.edu/#/?dataset=NISAR&prodConfig=PR&resultsLoaded=true>`

NISAR mission data was processed to generate products from Level-1 to Level-3. These datasets are available for a range of geographic locations, and give users a first look at products generated from NISAR acquisitions. These sample products are a preview for a larger global product release of sample products, expected by the end of February 2026. 

The NISAR project is still in the early phases of calibration, so these products are not yet fully calibrated, and contain artifacts, as described in @sample-product-limitations. The products will be improved in [future product releases](#data-release-timeline), but these sample products allow users to become familiar with NISAR data products and develop methods for working with the data and metadata.

For more information about this data release, refer to the [NISAR Sample Products Release Announcement](https://www.earthdata.nasa.gov/news/nisar-sample-data-products-available).

## Product Availability

The January release of NISAR sample data includes data from five different locations around the world. @tbl:sample-jan-overview-html summarizes the data products available for each location and the polarization of the acquisitions.

For areas with two acquisition dates listed, a single product is available for each of the pair-wise product types (GUNW, RIFG, RUNW, ROFF, GOFF), while product types generated from a single acquisition (RSLC, GSLC, GCOV) have a product available for each acquisition date.

:::{table} NISAR Sample Data Product Overview
:label: tbl:sample-jan-overview-html

| Location                    | Product Types                                  | Acquisition Dates            | Polarization       |
|-----------------------------|------------------------------------------------|------------------------------|--------------------|
| Antarctica                  | RSLC, GSLC, GCOV, GUNW, RIFG, RUNW, ROFF, GOFF | 2025-10-21, <br />2025-11-02 | HH (Single)        |
| Horn of Africa              | RSLC, GSLC, GCOV, GUNW                         | 2025-11-22, <br />2025-12-04 | HH+HV (Dual)       |
| Madhya Pradesh, <br />India | RSLC, GSLC, GCOV                               | 2025-10-17                   | HH+HV (Dual)       |
| Illinois, <br />USA         | RSLC, GSLC, GCOV                               | 2025-11-03                   | HH+HV+VH+VV (Quad) |
| Nile Delta, <br />Egypt     | SME2                                           | 2025-12-16                   | N/A                |
:::

(sample-product-limitations)=
## Sample Product Limitations

There are known limitations in the sample products. Keep these in mind when working with the data.

1. Radiometric banding across the swath. This is due to incomplete calibration, specifically:
   * Inter-beam channel calibration:  The on-board digital beamforming is controlled by amplitude and phase weights for each of the receive channels.  These weights have not yet been updated based on diagnostic mode analysis.  These adjustments are expected to be very small, with a minor improvement to SNR and phase variability.  As can be seen in this release, the beamforming is working very well even without adjustments. 
   * Antenna pattern calibration, which is still being refined.

1. Very low amplitude radiometric ripple aligned with the azimuth direction, only noticeable in some radar dark areas, and at a spatial scale of about 600 m and shorter. We are working ito improve radiometric uniformity at this low level, but SNR may still exhibit some banding at this scale.

1. Polarimetric channel imbalance. Polarimetric calibration and estimation of channel imbalances in the presence of a highly active ionosphere have not yet been performed. These steps will follow the radiometric corrections described above.

1. Quad-polarimetric (QP) product noise layers: In the QP products, the noiseEquivalentBackscatter layer for the HH polarimetric channel is incorrectly populated with zeros. The noiseEquivalentBackscatter layers for the HV and VV polarimetric channels are populated with correct (uncalibrated) values.

1. The Geocoded Unwrapped (GUNW) interferogram product has three known limitations:
   * The wrapped interferogram layer within the GUNW products is incorrectly georeferenced. This limitation does not apply to other layers in the GUNW product.
   * The boundary of the ionospheric phase layer has edge-effect artifacts. These artifacts will be minimized in a future release.
   * Interferogram generation does not yet use the full “rubbersheeting” algorithm to estimate local image distortions due to deformation. This capability is important for fast-moving areas in global production but is not critical for the present sample products, which exhibit modest deformation.  The algorithm used here for alignment of radar imagery (coregistration) is based on geometrical offsets (derived from imaging geometry of the NISAR acquisitions, orbit, and a digital elevation model) refined with a polynomial fit to the data-driven dense offsets computed from amplitude cross correlation of the radar data.

(data-release-timeline)=
## Data Release Timeline

As of January 2026, the _expected_ timeline for additional NISAR product releases is as follows: 

- Release of a larger volume of global data products by the end of February 2026
- Release of fully calibrated and algorithmically improved global products in May/June 2026