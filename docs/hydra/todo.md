---
title: Hydra - To Do
sidebar_label: "Hydra: To Do"
---

## Future Features

- Links to other dashboards according to data type

## Tasks

### QoC

1. Update Spectrum header

### Optimize deployment setup

1. Refactoring out environment configs
   1. Propogate on dev + document
   2. Progogate on Spectrum staging instance + document
   3. Propogate on Spectrum production instance + document

### Automate build

1. Automate rebuilding of images when pushed into staging / master branches
2. Automate redeploying of those images when it is done being rebuilt

   1. Propogate on Spectrum staging instance
   2. Propogate on Spectrum prod instance

### redCAP reconnection

RedCAP has started doing nightly syncs with IDB. It'll be good to assess how much of the data that we need we can pull, if there is any leading data we need (like IDs?) and reconnect if it is viable.

1. Document what columns are needed (and current source of data)
2. Assess what is being stored in RedCAP and how that aligns with our columns
3. Rewrite graphQL layer to pull from RedCAP

## Features

### Less binary representation of data

Should be able to differentiate between `Collected --> Sequenced --> Processed --> Loaded`

### Incorporate treatment information in extended panel

Currently dependent on whether it can be curated

### Incorporate lab work in timeline

There's a lot of different types of lab work done so we'll also need to figure out which ones to include.
