# L2 GSLC

The GSLC product is a Level 2 product derived from the Level-1 RSLC product by geocoding the input RSLC into a map coordinate system such as a UTM Zone or Polar stereographic projection system. 

The geocoding is performed by inverse mapping of the map coordinates with their topographic heights into the radar coordinate system and interpolating the radar signal at the radar location corresponding to the map coordinate. Phase-preserving complex interpolation projects the data onto a uniformly spaced, north-south/east-west aligned geographic grid. 

The phase of the GSLC product is flattened for the orbit used in the RSLC processing. The phase flattening removes the topographic phase contribution in the GSLC. Consequently, cross-multiplying two GSLC products will result in an interferometric phase flattened interferogram.
