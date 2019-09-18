---
title: Alhena - Overview
sidebar_label: Overview
---

Alhena is a single cell DNA (scDNA) QC dashboard for MSK SPECTRUM.

It takes the CSV output from the [single cell pipeline](https://github.com/shahcompbio/single_cell_pipeline).

This is intended on being a complete rewrite of Montage to eliminate code debt and to update the technologies used in its implementation.

## Goals

**Functional**

- Users can easily what libraries are available to view via the dashboard
- Users can browse through the processed data of individual libraries for QC / low level analysis purposes
- Enables users to access the data for further analysis on their own

**Non Functional**

- Maintain fast interactivity after initial load

## Assumptions

- User access through computer (no mobile support)
- Minimum screen size is 1280 x 800

## Technology

- [React](https://reactjs.org)
  - [d3](https://d3js.org/)
  - [React Router](https://reacttraining.com/react-router/)
  - [Material-UI](https://material-ui.com/)
  - [Apollo (Client)](https://www.apollographql.com/)
- [GraphQL](https://graphql.org/)
  - [Apollo](https://www.apollographql.com/)
- [Elasticsearch](https://www.elastic.co/products/elasticsearch)
