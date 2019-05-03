---
id: graphql-mutation
title: GraphQL: Mutations
sidebar_label: Mutations
---

## Patients and Events

### createEvents

_createEvents(patient_id: String!, events: [SubmittedEvent]!): Patient!_

- Input:
	- patient_id
  - events: all created events associated with specified patient
- Output: currently outputs just patient_id (as the other fields in the Patient query are not mandatory)
