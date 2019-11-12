---
title: Mira - Loading Data
sidebar_label: Loading Data
---

## Overview

Using the loaders will populate Elasticsearch with:

- Cell type, cluster, and tSNE dimension data for each cell
- Gene expression (normalized log counts) for each cell
- Analysis metadata (patient ID and sample IDs)

There are two ways to load data into Elasticsearch - using a virtual environment or running a pre-build Docker image.

## Input

### .rdata files

Mira's input data comes from the [scRNA pipeline](https://github.com/shahcompbio/SCRNApipeline). It is able to read off the resulting rdata file.

### Metadata Table

Metadata for each sample is contained in a google sheet. We currently pull these columns from the sheet `sample_metadata`:

- nick_unique_id
- patient_id
- tumour_site
- sort_parameters
- therapy
- time

## Virtual Environment (Development)

This method is recommended while doing development on the loaders.

### System Requirements

- Python 3

### Setup Virtual Environment

Clone Mira's database repository:

```
git clone https://github.com/shahcompbio/es-loaders
```

Create and start a new python3 environment

```
python3 -m venv /path/to/new/virtual/environment

source /path/to/new/virtual/environment/bin/activate
```

Install dependencies

```
pip install -r requirements.txt
```

### Run loader

There are many different scripts:

To bulk load all new libraries (it will compare google sheet list to what's in Mira's ES instance and load the new ones IF that rdata file is available in the directory)

```
python mira_bulk_loader /path/to/rdata/directory/ <ES_host> <ES_port>
```

To load an individual file:

```
python mira_loader.py /path/to/rdata/file
```

To delete entire sample from Elasticsearch

```
python mira_cleaner.py <type of data> <data ID> <ES_host> <ES_port>

python mira_cleaner.py "sample" SPECTRUM-OV-003_S1_CD45N_RIGHT_ADNEXA ... ...
```

To load rho data
NOTE: You need to go into rho_loader.py and update the host name because I haven't done that yet

```
python rho_loader.py
```

At some point I needed to check for duplicate loading instances, this script will do that and delete duplicate libraries (then you can reload them again).

```
python mira_data_checker.py
```

## Docker

NOTE: Currently outdated as I'm running it all through venv right now.

This method is recommended in all other situations.

### System Requirements

- Docker

### Instructions

Pull the Docker image for the loader

```
docker pull shahcompbio/spectrum-scrna-loader
```

Then run the container

```
sudo docker run -v /path/to/json/directory/:/usr/data/  -e FILEPATH=/usr/data/ --network="host" -it --cpus 4 shahcompbio/spectrum-scrna-loader
```
