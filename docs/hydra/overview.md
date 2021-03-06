---
title: Hydra - Overview
sidebar_label: Overview
---

Hydra is a cohort-level event timeline dashboard for MSK SPECTRUM.

## Goals

**Functional**

- To show a high level summary of all patients that have been enrolled in MSK SPECTRUM
  - Whether they have been included / excluded in study
  - What events (consent, surgery, blood collection, treatment) have occurred and in what order
  - For each event, what data (scDNA, scRNA, cfDNA, pseudobulk, etc) has been generated
  - Basic demographics of the cohort
- Allow users to easily navigate to other dashboards to see data in depth

## Assumptions

- User access through computer (no mobile support)
- Minimum screen size is 1280 x 800

## Technology

- [React](https://reactjs.org)
  - [React Router](https://reacttraining.com/react-router/)
  - [Material-UI](https://material-ui.com/)
  - [Apollo (Client)](https://www.apollographql.com/)
- [GraphQL](https://graphql.org/)
  - [Apollo](https://www.apollographql.com/)
- [redCAP](https://www.project-redcap.org/)

## Current Features

- Event timeline of all patients
  - Events: Inclusion/Exclusion, Surgery, Blood Collection, Treatment
  - Data: scRNA, scDNA, IMPACT, WGS
  - Link to appropriate Mira dashboard
- Ability to filter based on existence of certain events or data types
- Demographics panel
