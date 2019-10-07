---
title: Sprint
sidebar_label: Sprint
---

## Current Sprint (October 7 - 21, 2019)

### Aim #1: Full release of Mira on production

1.  [Optimize deployment setup](mira/todo#optimize-deployment-setup)

    1.  Split docker-compose into a database file, and an app (graphQL + React) file
        1. Create new Spectrum prod instance, and then propogate

2.  [Loading Tasks](mira/todo#loading-tasks)

    1. Reload all samples into Spectrum production instance
    2. Remove "" gene records when loading

3.  REVIEW [Bugs](mira/todo#bugs)

    1.  Gene selection dropdown has been removed
    2.  Patient level view has been removed
    3.  URL doesn't update when sample is selected

4.  [Quality of life updates](mira/todo#qol-updates)

    1.  Alphabetize selection dropdowns for patient, sample
    2.  Add ability to clear selection from dropdown
    3.  Order QC table by selection (alphabetical)
    4.  Split QC table sample_id column into sample, then CD45 sort status
    5.  Format sample_id string better (remove "\_", maybe not all caps)
    6.  Gene selection dropdown should prioritize exact matches
    7.  Refactor code to use React hooks

5.  [Reorganization of dashboards](mira/todo#reorganization-of-dashboards)
    1.  GraphQL layer for new db schema
    2.  React graphQL queries are updated
    3.  React-Router URLs are adjusted

### Aim #2: [Reconnect Hydra with RedCAP](hydra/todo#redcap-reconnection)

1. Document what columns are needed (and current source of data)
2. Assess what is being stored in RedCAP and how that aligns with our columns
3. Rewrite graphQL layer to pull from RedCAP

### Aim #3: [Authentication layer for Alhena](alhena/todo#authentication-layer)

1. Enable users (or admin) to create their own accounts **- (done but not deployed)**
2. Check into whether we can connect to MSK's ldap system
   1. If not, then create admin panel + mail server

### Aim #4: Misc Montage stuff

1. [Load additional data](other-todo#loading-data)

   1. Collaborator data
      1. Data is still being loaded
      2. Set up webserver + certificates for instances to redirect to different
   2. Cellmine
      - NOTE: Everything is currently loaded, but is just awaiting some checking and minor cleanup.

## Past Sprints

<details>
      <summary>September 16 - 30, 2019</summary>
### September 16 - 30, 2019
#### Aim #1: Prepare Mira for next Spectrum meeting

1. [Quality of life updates](mira/todo#qol-updates) **- not started**

   1. Alphabetize selection dropdowns for patient and sample
   2. Add ability to clear selection from dropdown
   3. Order QC table by selection (alphabetical)

2. [Bugs](mira/todo#bugs)

   1. Gene selection dropdown has been removed **- (done but not reviewed)**
   2. Patient level view has been removed **- (done but not reviewed)**
   3. URL doesn't update when sample is selected **- (done but not reviewed)**

3. [Loading Tasks](mira/todo#loading-tasks)

**Started refactoring effort to accommodate different types of dashboards (patient, cohort, celltype, site). The loading is done (tested on staging), and the graphQL layer is being redone.**

1.  Reload all samples into Spectrum production instance
2.  Write module to parallelize loading
3.  Remove "" gene records when loading
4.  Pull data from rdata, not from JSON (Nick will write API for this) **- (done)**

5.  [Web summary pages](mira/todo#web-summary-pages) **- not started**

    1.  Transfer files somewhere on the production instance (ws?)
        1. May need to mount new disk for this data
    2.  Edit nginx config to redirect URL requests to appropriate folder
    3.  Edit QC table to link

6.  [Optimize deployment setup](mira/todo#optimize-deployment-setup)
    1.  Split docker-compose into a database file, and an app (graphQL + React) file
        1. Propogate on Spectrum staging instance **- (done)**
        2. Create new Spectrum prod instance, and then propogate

#### Aim #2: Update Hydra and Sylph for next Spectrum meeting **- not started**

1. Redeploy Hydra and Sylph with new header
2. Update data for Hydra

#### Aim #3: [Authentication layer for Alhena](alhena/todo#authentication-layer)

1. Enable users (or admin) to create their own accounts **- (done but not deployed)**
2. Enable users to reset their own passwords **- not started**

#### Aim #4: Misc Montage stuff

1. [Load additional data](other-todo#loading-data)

   1. Collaborator data **- (in progress)**
   2. Cellmine **- (in progress)**

2. [Montage VM set up docs](other-todo#montage) **- (done)**
3. [is_contaminated field](other-todo#montage) **- (done, but not in prod)**
   </details>
