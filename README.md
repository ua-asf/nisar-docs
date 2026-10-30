# NISAR Data User Guide

Source for the public documentation of the NASA-ISRO Synthetic Aperture Radar (NISAR) mission hosted at https://nisar-docs.asf.alaska.edu.

[![DOI](https://img.shields.io/badge/DOI-10.5281%2Fzenodo.20075813-blue.svg)](https://doi.org/10.5281/zenodo.20075813)


## Contributing

1. Create a fork of https://github.com/ua-asf/nisar-docs/
1. Clone the repository and navigate to the repository root
1. Create and activate the conda environment
    ```
   mamba env create -f environment.yml
   mamba activate nisar-docs
    ```
1. Run `myst start` to render the website on your local machine
1. Make and commit your changes
1. Push changes to your fork in GitHub
1. Make sure your branch is synced and up to date with `ua-asf/nisar-docs:develop`
1. Open a pull request to `ua-asf/nisar-docs:develop`
1. Once your pull request has been approved and merged to `ua-asf/nisar-docs:develop`, verify the changes at `https://nisar-docs-test.asf.alaska.edu/`
1. Your changes will be published to the production website at https://nisar-docs.asf.alaska.edu with the next release.

### Page redirects

Renaming the markdown file for an existing content page in nisar-docs changes the URL for that content, which can
result in broken links. Myst does not have a builtin page redirect feature, so we implemented our own solution.

> [!IMPORTANT]
> These steps may change in the future, per https://github.com/ua-asf/nisar-docs/issues/93.
> This section will be updated if a new approach is implemented.

To add a new page redirect, follow the steps below (for example, to redirect page `/foo` to `/bar`):

1. Create a new subdirectory in [`redirects`](./redirects/) with the same name as the old page, e.g. `redirects/foo`.
1. Copy the `index.html` file from one of the existing subdirectories into your new subdirectory,
   then edit the file to update all occurrences of the redirect URL.
   - For example, copy [`redirects/product-limitations/index.html`](./redirects/product-limitations/index.html)
   to `redirects/foo/index.html`, then replace all references to `/product-known-issues` in the new file with `/bar`.
1. Because the redirect feature depends on some custom build steps in the [deploy workflow](./.github/workflows/deploy.yml),
   you won't be able to test your new redirect locally.
   You'll need to push to a fork with GitHub Pages enabled (see [Contributing](#contributing)) to verify redirect behavior.
1. After the site for your fork has successfully rendered, confirm that `/foo` redirects to `/bar`.
