---
title: Mira - Changelog
sidebar_label: Changelog
---

All notable changes to Mira will be documented here. The unreleased version is contained in the `staging` branch. The current released version is in `master`.

## 0.1.0

### Added (released - Nov 25, 2019)

- Coloring on site, surgery, treatment for non-sample dashboards

### Changed

- Metadata table support for merged dashboards
- Metadata table aesthetic changes
- CLI for loader
- Loading support for patient dashboards
  - bulk loading by type
  - memory improvements for gene matrix
  - merged metadata and dashboard entry together
- Bug fixes

## 0.0.3 (released - Nov 12, 2019)

### Added

- Selection based off patient, sample, CD45 sorting
- `.env` files for base URLs to enable quicker setup of instances

### Changed

- Spectrum header update
- Revamp of QC table, to combine with sample selection and filtering
- Scatterplot -> hexbin density plot with scatterplot by cell type overlaid
- Readded gene selection
- Removal of abundance plot in favor of proper plot legend
- Loader pulls from rdata, not JSON
- Loader pulls metadata from Google Sheets

## 0.0.2 (released - August 1 2019)

### Added

- Patient-level dashboard
- CellAssign table

### Changed

## 0.0.1 (released - May 1 2019)

### Added

- Patient, then sample selection
- tSNE plot with individual cell highlighting
- Searchable selection to colour tSNE plot by cell type, cluster, or gene name
- Bar / Line plot to show abundance of each colouring type, with cross highlighting
- python scripts to load JSON files into Elasticsearch
