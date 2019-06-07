---
id: mira-loading-data
title: Mira - Loading Data
sidebar_label: Loading Data
---

## Overview

Using the loaders will populate Elasticsearch with:

- Cell type, cluster, and tSNE dimension data for each cell
- Gene expression (normalized log counts) for each cell
- Analysis metadata (patient ID and sample IDs)

There are two ways to load data into Elasticsearch - using a virtual environment or running a pre-build Docker image.

## Required files

### JSON data files

Mira's input data comes from the [scRNA pipeline](https://github.com/shahcompbio/SCRNApipeline) as a collection of JSON files - one for each sample. These JSON files are contained in a directory (one per patient).

### Metadata YAML

This should be in the same directory as the JSON files and should be named `patient_metadata.yaml`

Here is an example:

```
patient_id: Patient_09443_D
sample_ids:
  - ABDOM-CD45N_IGO_09443_D_2
  - ABDOM-CD45P_IGO_09443_D_1
  - ASC-CD45P_IGO_09443_D_13
```

## Virtual Environment (Development)

This method is recommended while doing development on the loaders.

### System Requirements

- Python 3

### Setup Virtual Environment

Clone Mira's database repository:

```
git clone https://github.com/shahcompbio/mira-db
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

```
python dim_red_loader.py /path/to/json/directory
```

## Docker

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
