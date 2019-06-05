---
id: alhena-overview
title: Alhena - Overview
sidebar_label: Overview
---

Alhena is a single cell DNA (scDNA) dashboard for MSK SPECTRUM. It takes the CSV output from the [single cell pipeline](https://github.com/shahcompbio/single_cell_pipeline).

## Goals

- Allow users to browse through the processed data for QC / low level analysis purposes
- Allow users to access the data for further analysis

## Technology

- [React](https://reactjs.org)
  - [d3](https://d3js.org/)
  - [React Router](https://reacttraining.com/react-router/)
  - [Material-UI](https://material-ui.com/)
  - [Apollo (Client)](https://www.apollographql.com/)
- [GraphQL](https://graphql.org/)
  - [Apollo](https://www.apollographql.com/)
- [Elasticsearch](https://www.elastic.co/products/elasticsearch)

## Planned Features

- View data on per library and meta-library (multiple libraries in one) basis
- Cellscape (copy number heatmap)
- Accompanying QC plots: scatterplot, GC bias, violin plot, chip heatmap(s), metadata table
- Apply filters on entire data, and facades (selection in one plot to update the others)
- Users can download underlying data for further analysis
