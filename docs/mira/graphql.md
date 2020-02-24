---
title: Mira - GraphQL
sidebar_label: GraphQL
---

## DashboardAttributeInput

Dashboard attributes are options that a user can select to color the UMAP plot by.

```
{
    "type": "CELL"||"SAMPLE"||"GENE"
    "label": String
}
```

### Possible labels

"CELL"

- celltype
- celltype probabilities

"SAMPLE"

- site
- surgery
- treatment

"GENE"

- all gene names
