# Glossary

## General

:::{glossary}

Full-polarimetric covariance matrix
: Calculated by
    :::{math}
    :enumerated: false
    [G_{3}] =
    \begin{bmatrix}
    <S_{HH}S^*_{HH}> & <S_{HH}\overline{S}^*_{HV}> & <S_{HH}S^*_{VV}> \cr
    <\overline{S}_{HV}S^*_{HH}> & <\overline{S}_{HV}\overline{S}^*_{HV}> & <\overline{S}_{HV}S^*_{VV}> \cr
    <S_{VV}S^*_{HH}> & <S_{VV}\overline{S}^*_{HV}> & <S_{VV}S^*_{VV}>
    \end{bmatrix}
    :::
: The polarimetric covariance matrix $[G_3]$ is then radiometric terrain corrected and geocoded using an area-based projection algorithm, producing the GCOV matrix.

Geolocation accuracy
: The NISAR geolocation accuracy can be potentially affected by {term}`tropospheric delay`, {term}`solid earth tides (SET)` and {term}`ionospheric delay` [@yunjun2022].

Ionospheric delay
: At altitudes above ∼50 km, radiation (mainly from the Sun) ionizes atmospheric atoms and molecules forming the ionosphere. Its refractivity is mainly controlled by the {term}`total electron content`. The propagation of the microwave signal traveling through the ionosphere results in a group delay and a phase advance.

Radio Frequency Interference (RFI)
: The undesired signal in the form of wideband or narrowband interference that overlaps with the in-band frequency spectrum of NISAR. The main sources of high-power RFI are electromagnetic signals from civilian and military ground-based communication or radar platforms. RFI detection is performed on L0B raw data before focusing.

Radiometric Terrain Correction (RTC)
: The NISAR geocoded covariance (GCOV) product is radiometrically terrain
corrected to normalize the SAR backscatter to gamma-naught $\gamma^0$. The GCOV algorithm is using an area-projection algorithm [@shiroma2022] to compute RTC correction factor and to geocode the data.

Solid Earth Tides (SET)
: The motion of the Earth’s surface is driven by the gravitational pull from the Sun and the Moon (solid Earth tides), the change of the rotational axis (pole tides), the loading
effects from the ocean tides (OTL), the atmospheric and hydrological loading as well as the surface deformation. Displacements from tidal and loading effects are periodic with different time scales and amplitudes [@yunjun2022]. SET often reaches 40 and 10 cm in vertical and horizontal directions, respectively [@iersConventions2010].

Total Electron Content
: Two components of the Total Electron Content (TEC) data from the Global Navigation Satellite System (GNSS) are sampled every 10 seconds along the NISAR orbit: the integrated TEC from surface to the GNSS orbit and the top-side TEC. The difference of the two results in sub-orbital TEC is used to estimate range delay and the azimuth shifts.

Tropospheric delay
: At altitudes up to ~ 30 km, which forms the troposphere, refractivity is mainly controlled by temperature, water vapor, and dry air partial pressure [@berradaBaby1988]. The zenith hydrostatic delay is ~2.3 m at sea level at typical meteorological conditions, while the zenith wet delay varies from a few mm at the polar region to ∼40 cm at the equatorial region [@boehm2013]. The tropospheric delay is corrected using a static tropospherical model (European Centre for Medium-Range Weather Forecasts) during focusing the raw data.

:::

## Radar grid (metadata cube)

:::{glossary}

referenceSlantRange / secondarySlantRange
: The range position of the zero-Doppler grid in maters for each point of the geographical grid of the reference/secondary RSLS.

referenceZeroDopplerAzimuthTime / secondaryZeroDopplerAzimuthTime
: The zero-Dopple azimuth time of the zero-Doppler grid in seconds for each point of the geographical grid of the reference/secondary RSLC.

coordinateX
: The mapping of the zero-Doppler grid to the geographic grid (x component) in the units of the projection.

coordinateY
: The mapping of the zero-Doppler grid to the geographic grid (y component) in the units of the projection.

losUnitVectorX
: The East component of the Line-Of-Sight (LOS) unit vector from the target to the sensor in the East-North-Up coordinate system for each point of the geographic grid.

losUnitVectorY
: The North component of the Line-Of-Sight (LOS) unit vector from the target to the sensor in the East-North-Up coordinate system for each point of the geographic grid.

losUnitVectorZ
: The Up component of the Line-Of-Sight (LOS) unit vector from the target to the sensor in the East-North-Up coordinate system for each point of the geographic grid. The unit vector needs to be derived from the East and North components as:
    :::{math}
    :enumerated: false
    losUnitVectorZ = \sqrt{1 - losUnitVectorX^2 - losUnitVectorY^2}
    :::

alongTrackUnitVectorX
: The East component of the along-track unit vector (projection of the along-track vector at the ground height) in UTM coordinates.

alongTrackUnitVectorY
: The North component of the along-track unit vector (projection of the along-track vector at the ground height) in UTM coordinates.

incidenceAngle
: The angle between the LOS vector and the normal to the ellipsoid at the target height.

elevationAngle
: The angle between the LOS vector and the normal to the ellipsoid at the sensor.

groundTrackVelocity
: The absolute value of the platform velocity scaled at the target height.

perpendicularBaseline
: The perpendicular component of the baseline between reference and secondary RSLCs. The baseline component is only computed for the bottom and top heights of the radar grid cubes.

parallelBaseline
: The parallel component of the baseline between reference and secondary RSLCs. The baseline component is only computed for the bottom and top heights of the radar grid cubes.

:::