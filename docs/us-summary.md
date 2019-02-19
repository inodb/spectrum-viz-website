---
id: us-cohort
title: User Stories: Cohort
sidebar_label: Cohort
---

## Patient Enrollment

As a user, I want to see how many patients are enrolled in the study over time.

- [[VIZ-203](https://shahcompbio.atlassian.net/browse/VIZ-203)] Get API token for REDCap test database
- [[VIZ-204](https://shahcompbio.atlassian.net/browse/VIZ-204)] GraphQL layer to pull patient count (only those included in study) from REDCap
  - [[VIZ-205](https://shahcompbio.atlassian.net/browse/VIZ-205)] Write schema documentation
  - [[VIZ-206](https://shahcompbio.atlassian.net/browse/VIZ-206)] Write tests for graphQL layer
- [[VIZ-207](https://shahcompbio.atlassian.net/browse/VIZ-207)] UI layer to render cumulative count over time

## Cohort Events Summary

As a user, I want to see a summarized timeline of medical events (enrollment, surgery, blood collection, etc) for all patients in the study.

- [[VIZ-208](https://shahcompbio.atlassian.net/browse/VIZ-208)] GraphQL layer to pull medical events per patient from REDCap
  - [[VIZ-209](https://shahcompbio.atlassian.net/browse/VIZ-209)] Write schema documentation
  - [[VIZ-210](https://shahcompbio.atlassian.net/browse/VIZ-210)] Write tests for graphQL layer
- [[VIZ-211](https://shahcompbio.atlassian.net/browse/VIZ-211)] UI layer to render table of patients with event timeline

As a user, I want to see more information about a given medical event for a patient (how many samples, what kinds of data is available, when it was collected, etc)

- [[VIZ-212](https://shahcompbio.atlassian.net/browse/VIZ-212)] GraphQL layer to pull metadata, given event and patient
  - [[VIZ-213](https://shahcompbio.atlassian.net/browse/VIZ-213)] Write schema documentation
  - [[VIZ-214](https://shahcompbio.atlassian.net/browse/VIZ-214)] Write tests for graphQL layer
- [[VIZ-215](https://shahcompbio.atlassian.net/browse/VIZ-215)] UI layer to render table of metadata after some interaction with an event on the timeline

## Sending it to production

- [[VIZ-216](https://shahcompbio.atlassian.net/browse/VIZ-216)] Get API token for REDCap production database
- [[VIZ-217](https://shahcompbio.atlassian.net/browse/VIZ-217)] Write Docker build
- [[VIZ-218](https://shahcompbio.atlassian.net/browse/VIZ-218)] Get access to server
- [[VIZ-219](https://shahcompbio.atlassian.net/browse/VIZ-219)] Deploy app to server
- [[VIZ-220](https://shahcompbio.atlassian.net/browse/VIZ-220)] Set up authentication layer
- [[VIZ-221](https://shahcompbio.atlassian.net/browse/VIZ-221)] Set up continuous integration
