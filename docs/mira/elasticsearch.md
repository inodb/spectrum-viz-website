---
title: Mira - Elasticsearch
sidebar_label: Elasticsearch
---

Data for Mira is stored in Elasticsearch. This page will lay out the schema within Elasticsearch. For information on how to load data, see [here](mira/loading-data.md)

## Terminology

- `sample`: a patient + site + sort unit
- `dashboard`: a view - currently includes both samples and patients (combinations of samples)

## Indices

### `rho_markers`

Marker genes for each cell type, used when running a sample through CellAssign.

```
{
    "celltype": String,
    "marker": String
}
```

### `dashboard_entry`

Metadata for each dashboard loaded into Mira.

```
{
    "dashboard_id": String,
    "type": String -> "sample"|"patient",
    "patient_id": String,
    "sort": String,
    "sample_ids": [String],
    "surgery": [String],
    "treatment": [String],
    "site": [String]
}
```

### `sample_stats`

Specific statistics for each sample loaded into Mira.

NOTE: This was designed to be flexible, but currently only a very small subset of stats are loaded / displayed.

- Number of Reads
- Median UMI Counts
- Estimated Number of Cells
- Mito20
- Number of Genes
- Median Genes per Cell

```
{
    "sample_id": String,
    "stat": String,
    "value": Int
}
```

### `dashboard_cells`

Metadata for each cell in each dashboard.

NOTE: Even though the cells in merged sample dashboards are the same as the sample, there's no guarantee that they have the same cell ID, hence we loaded the cells separately.

```
{
    "dashboard_id": String,
    "sample_id" : String,
    "cell_id" : String,
    "x": Float,
    "y": Float,
    "cell_type" : String (must match with rho),
    "B cell probability" : Float,
    "Plasma cell probability" : Float,
    "CD4 T cell probability" : Float,
    "Cytotoxic T cell probability" : Float,
    "T reg cell probability" : Float,
    "NK cell probability" : Float,
    "Monocyte/Macrophage probability" : Float,
    "pDC probability" : Float,
    "Ovarian cancer cell probability" : Float,
    "Mesothelial cell probability" : Float,
    "Myofibroblast probability" : Float,
    "Vascular SMC probability" : Float,
    "Endothelial cell probability" : Float
}
```

### `dashboard_genes_<dashboard_id>`

Genes and normalized expression for every cell in the dashboard. If a cell does not express that gene, then it is not included in the index.

NOTE: There is one index for every dashboard

```
{
    "cell_id": String,
    "gene": String,
    "log_count": Float,
    "dashboard_id": String
}
```
