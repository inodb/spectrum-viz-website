---
title: Mira - Overview
sidebar_label: Overview
---

Mira is a single cell RNA (scRNA) dashboard for MSK SPECTRUM. It takes the JSON output from the [scRNA pipeline](https://github.com/shahcompbio/SCRNApipeline).

## Goals

**Functional**

- Allow users to browse through the processed data for QC / low level analysis purposes
- Allow users to access the data for further analysis

**Non Functional**

- Maintain fast interactivity after initial load

## Assumptions

- User access through computer (no mobile support)
- Minimum screen size is 1280 x 800

## Repositories

- [React front-end](https://github.com/shahcompbio/mira-react)
- [GraphQL middleware](https://github.com/shahcompbio/mira-graphql)
- [Elasticsearch database](https://github.com/shahcompbio/mira-db)

- [Docker Compose build](https://github.com/shahcompbio/mira-docker)

## Technology

- [React](https://reactjs.org)
  - [Semiotic](http://semiotic.nteract.io)
  - [React Router](https://reacttraining.com/react-router/)
  - [Material-UI](https://material-ui.com/)
  - [Apollo (Client)](https://www.apollographql.com/)
- [GraphQL](https://graphql.org/)
  - [Apollo](https://www.apollographql.com/)
- [Elasticsearch](https://www.elastic.co/products/elasticsearch)

## Major Features

- Viewing of data on a per sample, merged sample (pre-caluclated) basis
- Interactive tSNE plot with ability to colour by cell type or gene expression
- QC table with various metrics
