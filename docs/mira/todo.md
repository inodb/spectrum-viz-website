---
title: Mira - To Do
sidebar_label: "Mira: To Do"
---

## CURRENT SPRINT

### Cell type proportion bar chart

1. On main page, shows proportion of cells (for only samples)
2. On sample-level, should see counts of cells

### Filter cells shown

1. By site, cell type, surgery, pre/post
1. Add support for subsetting / coloring / proportion bar charts:
   1. Activated vs Exhausted Cytotoxic T cells
   2. HR vs HRD Cancer cells
   3. M1 vs M2 Macrophages

### Prototyping

1.  Gene enrichment plot
2.  Correlation plot
3.  Housekeeping gene expression

## Backlog

### Prototyping

1.  Bulk export of plots given label
2.  Volcano plots

### Legend improvements

1. More descriptive tooltip (# cells in that group, ranges where needed)
2. Proper highlighting of parts of legend (outline? also somewhere where it states what's been highlighted)
3. "Select" to hold highlight (so we can do additional interactions with individual cells)
4. Legend should alphabetize labels

### QoL updates

1. Label selection dropdown should prioritize exact matches

### Optimize deployment setup

1. Write ansible script to automate creation of nodes
   1. Elasticsearch DB nodes

### Automate build

1. Automate rebuilding of images when pushed into staging / master branches
2. Automate redeploying of those images when it is done being rebuilt
   1. Propogate on Spectrum staging instance
   2. Propogate on Spectrum prod instance

### Web summary pages

Web summaries are provided by CellRanger and is packaged when the raw data is downloaded

1. Transfer files somewhere on the production instance (ws?)
   1. May need to mount new disk for this data
2. Edit nginx config to redirect URL requests to appropriate folder
3. Edit QC table to link

### Polish up Spectrum version

1. Have all Spectrum-specific components appear only on Spectrum-related builds (important for indepdent instances - like for the BCCRC)
   1. Favicon
   2. Web title
   3. Header

### Deploy instance for BCCRC

### Automate loading

1. Later, also transfers the HTML web summary files into the right place

### Download data

1. Users can download underlying data for further analysis
