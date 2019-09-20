---
title: Mira - To Do
sidebar_label: "Mira: To Do"
---

## Tasks

### QoL updates

1. Alphabetize selection dropdowns for patient, sample
2. Add ability to clear selection from dropdown
3. Order QC table by selection (alphabetical)
4. Split QC table sample_id column into sample, then CD45 sort status
5. Format sample_id string better (remove "\_", maybe not all caps)
6. Gene selection dropdown should prioritize exact matches
7. Refactor code to use React hooks

### Bugs

1. Gene selection dropdown has been removed
2. Patient level view has been removed
3. URL doesn't update when sample is selected

### Optimize deployment setup

1. Split docker-compose into a database file, and an app (graphQL + React) file
   1. Propogate on Spectrum staging instance
   2. Create new Spectrum prod instance, and then propogate
2. Finish refactoring out environment configs
   1. Propogate on dev + document
   2. Progogate on Spectrum staging instance + document
   3. Propogate on Spectrum production instance + document
3. Write ansible script to automate creation of nodes
   1. Elasticsearch DB nodes

### Loading Tasks

1. Reload all samples into Spectrum production instance
2. Write module to parallelize loading
3. Remove "" gene records when loading

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

1. Add Spectrum favicon
2. Have all Spectrum-specific components appear only on Spectrum-related builds (important for indepdent instances - like for the BCCRC)
   1. Favicon
   2. Web title
   3. Header

### Deploy instance for BCCRC

### Automate loading

1. Should specify what patient to load
2. Downloads from Azure blob
3. Unzips and feeds it into the right python call
4. Later, also transfers the HTML web summary files into the right place

## Features

### Cell type proportion bar chart

1. Shows proportion of cells amongst samples on a cohort, patient, sample level

### View data on various levels

1. Cohort level
2. Cell type level (cohort, patient, sample)

### Support multiple gene expression plots

1. Want to compare gene expression across multiple genes simultaneously

### Download data

1. Users can download underlying data for further analysis
