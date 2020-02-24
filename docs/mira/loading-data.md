---
title: Mira - Loading Data
sidebar_label: Loading Data
---

## Overview

Using the loaders will populate Elasticsearch with:

- Cell type (plus probabilities) and UMAP dimension data for each cell
- Gene expression (normalized log counts) for each cell
- Analysis metadata (patient ID and sample IDs)

There are two ways to load data into Elasticsearch - using a virtual environment or running a pre-build Docker image.

## Input

### .rdata files

Mira's input data comes from the [scRNA pipeline](https://github.com/shahcompbio/SCRNApipeline). It is able to read off the resulting rdata file.

### Metadata Table

Metadata for each sample is contained in a google sheet. We currently pull these columns from the sheet `sample_metadata`:

NOTE: In the future this will be pulled from eLab

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
- R (https://www.r-project.org/)

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
pip install -r mira-requirements.txt
```

Install R packages

```
R -e "install.packages('BiocManager')"

R -e "BiocManager::install()"

R -e "BiocManager::install('SingleCellExperiment')"

R -e "BiocManager::install('scater')"
```

To load properly, you may need to export the following variables (contact Samantha for more information):

```
GOOGLE_APP_ENGINE_DIR
ELAB_API_KEY
ISABL_API_URL
ISABL_CLIENT
```

### Run loader

To load data, you can load as one of the following:

1. Individual dashboard ID
2. All dashboards of a certain type not loaded yet
3. Individual dashboard ID with related samples (e.g. by patient ID and all samples with the same patient ID)

You can also choose to force reload an existing dashboard
NOTE: We assume the dashboard_id matches the file name
NOTE: dashboard_type is currently one of `sample` or `patient`

```
python mira_cli.py --host <ES_host> --port <ES_port> load-analysis --type <dashboard_type> --id <dashboard_id>  /path/to/rdata/file/dir

python mira_cli.py --host <ES_host> --port <ES_port> load-analysis --type <dashboard_type> --load-new /path/to/rdata/file/dir

python mira_cli.py --host <ES_host> --port <ES_port> load-analysis --type <dashboard_type> --id <dashboard_id> --load-support /path/to/rdata/file/dir

python mira_cli.py --host <ES_host> --port <ES_port> load-analysis --type <dashboard_type> --id <dashboard_id> --reload /path/to/rdata/file/dir
```

To delete entire sample from Elasticsearch

```
python mira_cli.py --host <ES_host> --port <ES_port> clean-analysis <type of data> <data ID>
```

To load rho data

```
python --host <ES_host> --port <ES_port> mira_cli.py load-rho
```

To verify load:

- We check for dashboards that may have been loaded multiple times
- We check for missing related samples for every non-sample dashboard (e.g. that all samples related to a certain patient has been loaded)

```
python --host <ES_host> --port <ES_port> mira_cli.py verify-load
```

To check what dashboards have been loaded (against the list of all possible dashboards):

```
python --host <ES_host> --port <ES_port> mira_cli.py missing-dashboards
```

## Docker

**NOTE: Currently outdated as I'm running it all through venv right now.**

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
