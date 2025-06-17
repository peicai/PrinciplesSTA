# Orchestrating Spatial Transcriptomics Analysis with Bioconductor

[![biocbook](https://img.shields.io/github/actions/workflow/status/lmweber/OSTA/biocbook.yml?label=Book%20build)](https://github.com/lmweber/OSTA/actions/workflows/biocbook.yml)  
[![depbuild](https://img.shields.io/github/actions/workflow/status/lmweber/OSTA/depbuild.yml?label=Dependencies%20build)](https://github.com/lmweber/OSTA/actions/workflows/depbuild.yml)


## Overview

This repository contains source files for the "Orchestrating Spatial Transcriptomics Analysis with Bioconductor" book.


## Link to book

The development version of the book is available at: https://lmweber.org/OSTA/


## For developers

### GitHub Actions

The book is built by the GitHub Actions workflows in `.github/workflows/`.

The GitHub Actions workflows are split into two files:
- `depbuild.yml` installs dependencies and stores these in a Docker image (triggered only if there are changes to `DESCRIPTION` or `deps.Dockerfile`)
- `biocbook.yml` builds the book and runs checks (triggered by changes to any other files)

A new public version of the book is deployed if changes are pushed to `devel` branch.


### Pull requests

Please send pull requests into `sandbox` branch (instead of `devel`). This will trigger GitHub Actions to build the book and run checks, but will not deploy a new version of the book. The maintainers will then merge into `devel` to deploy a new version of the book after reviewing and accepting the pull request.


### Local build

To build a local version of the book, first install all dependency packages (from `DESCRIPTION`) manually. Then, run `quarto_render()` in an R session in the `inst/` directory as follows:

```
setwd("inst")
quarto::quarto_render(cache = TRUE)
```

To compile a complete fresh local build, delete all existing build files by deleting the following directories and files: `inst/.quarto/`, `inst/docs/`, `inst/index_cache/`, any files and directories except `.qmd` files and `images/` directory in `inst/pages/` (e.g. directory names ending with `_cache/` or `_files/`, `.md` files, and `.rds` files). You may also need to empty the `BiocFileCache` cache directory if any data files stored in the OSF data repository have changed.


### Instructions

In each analysis / method chapter, we aim to include the following:
- brief background and overview
- mention any relevant benchmark papers
- demonstrate 1-2 key methods available in Bioconductor using code examples
- (optional) mention any other important methods in text (but keep concise)

Workflow chapters are longer and are intended to demonstrate a comprehensive workflow for a given data type / technological platform.

Please keep any added file sizes (e.g. images) as small as possible, and/or commit only code files.
