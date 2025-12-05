# Glossary

:::{glossary}
## General
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
: The polarimetric covariance matrix $[G_3]$ is then radiometric terrain corrected and geocoded using an area-based projection algorithm, producing the GCOV matrix



## Radar grid (metadata cube)
referenceSlantRange / secondarySlantRange
: The range position of the zero-Doppler grid in maters for each point of the geographical grid of the reference/secondary RSLS

referenceZeroDopplerAzimuthTime / secondaryZeroDopplerAzimuthTime
: The zero-Dopple azimuth time of the zero-Doppler grid in seconds for each point of the geographical grid of the reference/secondary RSLC

coordinateX
: The mapping of the zero-Doppler grid to the geographic grid (x component) in the units of the projection

coordinateY
: The mapping of the zero-Doppler grid to the geographic grid (y component) in the units of the projection

losUnitVectorX
: The East component of the Line-Of-Sight (LOS) unit vector from the target to the sensor in the East-North-Up coordinate system for each point of the geographic grid

losUnitVectorY
: The North component of the Line-Of-Sight (LOS) unit vector from the target to the sensor in the East-North-Up coordinate system for each point of the geographic grid

losUnitVectorZ
: The Up component of the Line-Of-Sight (LOS) unit vector from the target to the sensor in the East-North-Up coordinate system for each point of the geographic grid. The unit vector needs to be derived from the East and North components as:
:::{math}
:enumerated: false
losUnitVectorZ = \sqrt{1 - losUnitVectorX^2 - losUnitVectorY^2}
:::

alongTrackUnitVectorX
: The East component of the along-track unit vector (projection of the along-track vector at the ground height) in UTM coordinates

alongTrackUnitVectorY
: The North component of the along-track unit vector (projection of the along-track vector at the ground height) in UTM coordinates

incidenceAngle
: The angle between the LOS vector and the normal to the ellipsoid at the target height

elevationAngle
: The angle between the LOS vector and the normal to the ellipsoid at the sensor

groundTrackVelocity
: The absolute value of the platform velocity scaled at the target height

perpendicularBaseline
: The perpendicular component of the baseline between reference and secondary RSLCs. The baseline component is only computed for the bottom and top heights of the radar grid cubes

parallelBaseline
: The parallel component of the baseline between reference and secondary RSLCs. The baseline component is only computed for the bottom and top heights of the radar grid cubes

:::