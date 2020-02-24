---
title: Timeline
sidebar_label: Timeline
---

## Q4 (Oct - Dec 2019)

### Alhena

Montage rewrite is underway, codenamed as Alhena. We aim to have a deployed production instance with the following features:

1. Browse panel with ability to filter over sample, library, and JIRA ticket ID
2. Authentication layer to enable easier creation of user accounts, and to enable restricted access of libraries for collaborators
3. Fully featured Cellscape plot, with faster initial load and better interactivity

### Hydra

Continue the push to reduce amount of manual curation the data currently needs.

### Mira

Would like to clean up Mira's current code base (reduce tech debt), then focus on these features:

1. Cell type proportion bar chart
2. Viewing data on cohort level

### Deployment

1. For all dashboards in Spectrum, set up automated deployment when updates are pushed into `staging` and `master` branches.
2. Have fully set up and well documented staging and production environment
3. Enable each dashboard to also be set up in a separate instance (via environmental configs)
4. Add ansible scripts to automatically create VMs for loading, webservers, and ES nodes

### Elasticsearch Loaders

TBD

## Q1 2020 (Jan - Mar 2020)

### Alhena

1. Chip heatmap
2. GC bias plot with more dynamic aggregation (based off user selection)
3. Facades from chip heatmap to other plots
4. Quality filter

### Mira

1. Automate loading of data
2. Multiple gene expression plots

## Q2 2020

### Hydra

1. Connect Hydra to eLab / REDCap / Isabl
2. Revamp front end
3. Add status for WGS, scRNA, scDNA data

### Alhena

1. Remainder of QC plots

### Mira

1. Add prototypes to support Nick's analysis
2. Add support for T-cell exhaustion, HRD composition
