---
title: Alhena - To Do
sidebar_label: "Alhena: To Do"
---

## Tasks

### Deployment

1. Write docker-compose files for both db and app
2. Setup Spectrum staging VM + deploy
3. Setup Spectrum production VM + deploy
4. Automate docker image rebuild when pushed to master / staging
5. Automate update on instances when docker image has been rebuilt
6. Add environmental configs for dev + document
7. Add environmental configs for staging + document
8. Add environmental configs for prod + document

### Loading

1. Stress test db using Loading

NOTE: Currently old Montage loader is being rewritten. Want to see how much of it we can port over. I think eventually we will want to use a bulk of that code for this new loader.

NOTE: We want to share a lot of the common modules with Mira. And as we expand and continue to use ES, to other dashboards as well.

## Features

### Authentication Layer

1. Allow users to create their own accounts
   1. Needs to be deployed
2. Check into whether we can connect to MSK's ldap system
   1. If not, then create admin panel + mail server
3. Once logged in, only show content that user is permitted to see

### Cellscape

1. Summarized copy number heatmap
2. Minimap copy number heatmap
3. Individual copy number profile
4. Labeling of cell call / experimental condition for each row

NOTE: Will probably rewrite this with canvas with voronoi overlay, to render faster

### Accompanying QC plots

1. Scatterplot
2. GC bias
3. Violin
4. Chip heatmaps
5. Metadata table

### Filters and Facades

1. Easily add / remove filters on entire data set
2. Easily add / remove facades (selections in one plot to update the others)

### Download data

1. Enable users to download underlying data for further analysis
   - NOTE: Need to figure what kinds of data
