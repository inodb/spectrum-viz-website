---
title: Mira - To Do
sidebar_label: "Mira: To Do"
---

## CURRENT SPRINT

1. Add support for patient level dashboard
   1. Loading patient data
   2. GraphQL layer
   3. React
2. Add support for subsetting / coloring:
   1. Activated vs Exhausted Cytotoxic T cells
   2. HR vs HRD Cancer cells
   3. M1 vs M2 Macrophages

## Backlog

### Bugs

1. SPECTRUM-OV-007_CD45P has exactly 10000 cytotoxic T cells, which I suspect is due to hitting max return value as opposed to it being the actual number
2. Suspcious lack of highlighting for certain sites
3. Table header shows > when you scroll up
4. Fairly sure I'm hitting query limits on patient level data

### Legend improvements

1. More descriptive tooltip (# cells in that group, ranges where needed)
2. Proper highlighting of parts of legend (outline? also somewhere where it states what's been highlighted)
3. "Select" to hold highlight (so we can do additional interactions with individual cells)

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

1. Should specify what patient to load
2. Downloads from Juno (via Isabl?)
3. Later, also transfers the HTML web summary files into the right place

### Cell type proportion bar chart

1. On main page, shows proportion of cells per patient.
   1. Should also be able to see per patient, split by site
2. On patient-level dashboard, should see per site
3. On sample-level, should see counts of cells

### View data on various levels

1. Cell type level
2. Site specific level

### Filter cells shown

1. By site, cell type, surgery, pre/post

### Additional colouring categories

1. Additional categorical/numerical things that can be scraped from the data
2. By surgery, pre/post treatment
3. By probability of cell type assignment

### Support multiple gene expression plots

1. Want to compare gene expression across multiple genes simultaneously

### Download data

1. Users can download underlying data for further analysis
