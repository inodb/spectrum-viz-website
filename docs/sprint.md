---
title: Sprint
sidebar_label: Sprint
---

## Current Sprint (September 16 - 30, 2019)

### Aim #1: Prepare Mira for next Spectrum meeting

1. [Quality of life updates](mira/todo#qol-updates)

   1. Alphabetize selection dropdowns for patient and sample
   2. Add ability to clear selection from dropdown
   3. Order QC table by selection (alphabetical)

2. [Bugs](mira/todo#bugs)

   1. Gene selection dropdown has been removed
   2. Patient level view has been removed

3. [Loading Tasks](mira/todo#loading-tasks)

   1. Reload all samples into Spectrum production instance
   2. Write module to parallelize loading
   3. Remove "" gene records when loading

4. [Web summary pages](mira/todo#web-summary-pages)
   1. Transfer files somewhere on the production instance (ws?)
      1. May need to mount new disk for this data
   2. Edit nginx config to redirect URL requests to appropriate folder
   3. Edit QC table to link

5. [Optimize deployment setup](mira/todo#optimize-deployment-setup)
   1. Split docker-compose into a database file, and an app (graphQL + React) file
      1. Propogate on Spectrum staging instance
      2. Create new Spectrum prod instance, and then propogate

### Aim #2: Update Hydra and Sylph for next Spectrum meeting

1. Redeploy Hydra and Sylph with new header
2. Update data for Hydra

### Aim #3: [Authentication layer for Alhena](alhena/todo#authentication-layer)
1. Enable users (or admin) to create their own accounts
2. Enable users to reset their own passwords

### Aim #4: Misc Montage stuff

1. [Load additional data](other-todo#loading-data)

   1. Collaborator data
   2. Cellmine

2. [Montage VM set up docs](other-todo#montage)
3. [is_contaminated field](other-todo#montage)
