---
id: graphql-mutation
title: GraphQL: Mutations
sidebar_label: Mutations
---

## Patients and Events

### createEvents

_createEvents(patient_id: String!, events: [SubmittedEvent]!): Patient!_

- Inputs:
	- patient_id
  - events: all created events associated with the specified patient_id
- Output: currently just patient_id, as the other fields in the Patient query are not mandatory (click [here](https://github.com/shahcompbio/spectrum-cohort-graphql/blob/master/src/patients.js) for more details)
