(nisar-naming-conventions)=
# NISAR Naming Conventions

(naming-convention-overview)=
## Naming Convention Overview

There are three different patterns used for naming NISAR data products, depending on the product type:
1. [Raw Data Products](#raw-data-products)
2. [Products Generated from a Single Acquisition](#products-generated-from-a-single-acquisition)
3. [Products Generated from Pairs of Acquisitions](#products-generated-from-a-pair-of-acquisitions)

(raw-data-products)=
## Raw Data Products

This naming convention is only used for Level 0 products, such as the Level 0B [RRSD](#rrsd-product-overview) products. 

-----

```{figure} ../assets/nisar-naming-conventions-rrsd.png
:label: naming_convention_raw_data
:alt: NISAR naming convention for raw data
:align: center

NISAR naming convention for raw (L0B) data products
```

-----

(products-generated-from-a-single-acquisition)=
## Products Generated from a Single Acquisition

This naming convention is used for products that take a single NISAR acquisition as input for processing, including:
  * L1 [RSLC](#rslc-product-overview)
  * L2 [GSLC](#gslc-product-overview)
  * L2 [GCOV](#gcov-product-overview)
  * L3 [SME2](#sme2-product-overview)

-----

```{figure} ../assets/nisar-naming-conventions-single.png
:label: naming_convention_single_data
:alt: NISAR naming convention for processed data
:align: center

NISAR naming convention for data products generated from a single acquisition
```

-----

(products-generated-from-a-pair-of-acquisitions)=
## Products Generated from a Pair of Acquisitions

This naming convention is used for products that require pairs of NISAR acquisitions as input for processing, including:
  * L1 [RIFG](#rifg-product-overview)
  * L1 [RUNW](#runw-product-overview)
  * L2 [GUNW](#gunw-product-overview)
  * L1 [ROFF](#roff-product-overview)
  * L2 [GOFF](#goff-product-overview)

-----

```{figure} ../assets/nisar-naming-conventions-pair.png
:label: naming_convention_interferometric_data
:alt: NISAR naming convention for interferometric data
:align: center

NISAR naming convention for data products generated from pairs of acquisitions
```

-----