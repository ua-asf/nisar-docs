# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).


## [0.4.28]

### Changed
- Added [nisarqa](https://github.com/isce-framework/nisarqa) to the [Open Source Software](using-nisar/using-open-source.md) page

## [0.4.27]

### Added
- [Open Source Software](using-nisar/using-open-source.md) page listing open source software packages that support working with NISAR data

## [0.4.26]

### Added
- [GDAL](accessing-nisar/gdal.md) page to Accessing Data section
- Page describing projections used for Level 2 and 3 products
- Redirect placeholder page for Static Layers

### Changed
- Edited formatting of summary table on the products page
- Updated QGIS page to announce support for NISAR starting with version 4.2 and highlight netCDF driver prepend option when adding data

## [0.4.25]

### Added
- [Satellite Needs Working Group (SNWG)](resources/snwg.md) page
- Pixel spacing table to [GSLC page](data-products/level-2/gslc.md)
- Pulse Repetition Frequency (PRF) information to SweepSAR section, referencing the data gaps in quad-pol data collected with a fixed PRF

### Changed
- Updated [Provisional Known Issues](data-availability/provisional-known-issues.md) page 

## [0.4.24]

### Added
- Links to the [ARSET NISAR training course](https://www.earthdata.nasa.gov/learn/trainings/harnessing-nisar-next-generation-radar-observations-earth-applications) on the [Webinars](resources/webinars.md) page

## [0.4.23]

### Added
- [NISAR in Worldview product page](tools-services/worldview.md)
- Pixel spacing reference table to [GCOV product page](data-products/gcov.md)

### Changed
- Updated Tools and Services overview page and development roadmap with new Worldview content
- Added more information on frequency A/B acquisitions in the About NISAR page
- Added a reference to Worldview in the Earthdata Search section of the Accessing NISAR Data overview page

## [0.4.22]

### Changed
- Updated the [Data Availability](https://nisar-docs.asf.alaska.edu/availability-overview/) page with the PROVISIONAL data release information
- Replaced the [Known Issues](https://nisar-docs.asf.alaska.edu/provisional-known-issues/) page content with information specific to the PROVISIONAL data, and hid the known issues page for the BETA datasets from the navigation menu (still accessible by link)
- Included information about [data maturity levels](https://nisar-docs.asf.alaska.edu/products-overview#nisar-maturity-levels) on the Data Products overview page
- Added disclaimer to SME2 product page that PROVISIONAL SME2 datasets are not fully calibrated

## [0.4.21]

### Added
- References to the new [NISAR GCOV in ArcGIS Pro 3.7](https://storymaps.arcgis.com/stories/07ec769f0a2f44469c3de3809269d3c0) StoryMap tutorial describing the new features in ArcGIS Pro 3.7 supporting use of NISAR GCOV products

## [0.4.20]

### Added
- [Urgent Response product page](data-products/urgent-response.md)

## [0.4.19]

### Changed
- Additional processing timeline edit related to the scope of the validated reprocessing campaign.

## [0.4.18]

### Added
- Information about S-band data availability and access through [Bhoonidhi](https://bhoonidhi.nrsc.gov.in/bhoonidhi/index.html)
- Additional information about look direction and polarizations on the [About NISAR page](https://nisar-docs.asf.alaska.edu/nisar-intro/)

## Changed
- Added trailing slash to URLs in sitemap.xml when deploying to GitHub pages. Fixes https://github.com/ua-asf/nisar-docs/issues/144.
- Updated processing timeline

## [0.4.17]

## Changed
- Updated development status of the Harmony GCOV dataset extraction service (released June 2026)

## [0.4.16]

## Changed
- Updated data release timeline with more precise latency estimates for forward processing.

## [0.4.15]

### Changed
- Updated nominal data release timeline as of June 2026. Forwarding processing is now expected to begin "in July",
  rather than "in early July".

## [0.4.14]

### Added
- Citation information to landing page

## [0.4.13]

### Changed
- Updated data release timeline to reflect no changes as of May 2026.

## [0.4.12] 

### Added
- Tools and Services section describing development efforts leveraging Earthdata tools and services
- Roadmap outlining ASF's development efforts in support of Earthdata tools and services
- Removed Appendices section and moved content into Resources section

## [0.4.11]

### Added
- A GitHub Actions workflow to ensure all (git) contributors have been added to the `citation.cff` file
- A `.mailmap` file to connect the varying ways contributors represent their names and emails to their entry in `citation.cff`

## [0.4.10]

### Added
- A `citation.cff` file to provide citation metadata for this guide.
- A GitHub action to validate chages to the `citation.cff` file.
- Add Zenodo "project" DOI to README that will always resolve to the latest version on Zenodo. 

## [0.4.9]

### Added
- Guidance for searching for products in Antarctica
- More links to [Earthdata Login documentation](https://www.earthdata.nasa.gov/data/earthdata-login)

## [0.4.8]

### Added
- README section documenting how to add a page redirect.

## [0.4.7]

### Added
- Site footer with contact information
- Contact section with additional content on using the Earthdata Forum as the primary venue for asking questions about NISAR
- Swath width description in the S-band mnemonic schema section
- References to the observation plan kmz files available for download

## [0.4.6]

### Added
- [Observation plan page](data-availability/observation-plan.md)

## [0.4.5]

### Changed
- Updated the Data Release Timeline as of April 2026, now targeting the start of forward processing in early July 2026

## [0.4.4]

### Added
- Added link to NISAR Cookbook in NISAR Tutorials section

## [0.4.3]

### Fixed
- Fixed header on Data Processing Algorithms page

## [0.4.2]

### Added
- Added an example of streaming data via asf_search

## [0.4.1]

### Changed
- Specified SME2 products are not single acquisition products on the Naming Convention page 

## [0.4.0]

### Added
- Guidance page for working with NISAR data in QGIS
- Guidance page for working with NISAR data in ArcGIS Pro
- Links to NISAR ATBD GitLab site
- Link to the NISAR Science Team Meeting Data Access Webinar

### Changed
- Added NISAR summary article to White Papers and Documents page and rearranged order of contents
- Edited GUNW product page to clarify what products are generated by the mission
- Expanded GSLC product page content
- Expanded Amplitude and Phase page content
- Expanded GIS Software section of the Using NISAR Data overview page
- Edits to the Known Issues page
- Changed the name of the `User Support` section to `Resources`

## [0.3.2]

### Changed
- Expanded the description of the future Data Release Timeline on the Available Data page

## [0.3.1]

### Added
- Added a link to the detailed L-SAR Product File Naming Conventions document on the NISAR Naming Conventions page.

## [0.3.0]

### Changed
- Changed references to product limitations to product known issues, and redirect https://nisar-docs.asf.alaska.edu/product-limitations/ to https://nisar-docs.asf.alaska.edu/product-known-issues/

## [0.2.13]

### Fixed
- Updated all links to the `earthaccess` GitHub Repository due to the [decision](https://earthaccess.readthedocs.io/en/latest/governance/decisions/929-move-repository/) to move from NSIDC's GitHub Org to the new `earthaccess-dev` GitHub org.

## [0.2.12]

### Added
- Dedicated page for pre-calibration data product limitations

### Changed
- Updated data availability to include February 27, 2026 pre-calibration data release
- Make headings more obvious via custom CSS

### Fixed
- Limit Google Analytics to production website

## [0.2.11]

### Added
- Custom `404` page. Fixes https://github.com/ua-asf/nisar-docs/issues/49

## [0.2.10]

### Changed
- Expanded Earthdata Search guidance page
- Updated the processing levels diagram
- Updated guidance on the NISAR earthaccess endpoint

## [0.2.9]

### Added
- "Download data" section to `asf-search` page

## [0.2.8]

### Added
- Page documenting the NISAR Orbit Ephemeris supporting product

## [0.2.7]

### Added
- Page documenting searching for NISAR products using Vertex
- Added Earthdata Login summary to accessing overview page 

## [0.2.6]

### Changed
- Revised and expanded the HDF5 documentation in [`data-products/data-format.md`](data-products/data-format.md).

## [0.2.5]

### Added
- Page documenting searching for, downloading, and streaming NISAR products using `earthaccess`
- A section to `aws-s3-access.md` detailing using `earthaccess` to get temporary S3 credentials

## [0.2.4]

### Added
- Page documenting searching for NISAR products using Earthdata Search

## [0.2.3]

### Added
- Page documenting the modified Copernicus DEM used for NISAR processing

### Changed
- Figure numbering now restarts at 1 on each page, rather than continuing across the entire site

## [0.2.2]

### Fixed
- Use a personal access token for the `tag-release.yml` workflow. Fixes the bug described in https://github.com/ASFHyP3/actions/pull/320

## [0.2.1]

### Changed
- Default Myst favicon has been replaced by custom University of Alaska favicon.

## [0.2.0]

### Changed
- Set the overview content for each first-level navigation menu item to display when the menu item is clicked, rather than having a separate overview page included under the expanded menu

### Removed
- Removed the Software Options page from the Using NISAR Data section

## [0.1.2]

### Added
- Direct AWS S3 Access page

## [0.1.1]

### Added
- Content describing the January release of the NISAR Sample Data

## [0.1.0]

### Added
- Initial release.
