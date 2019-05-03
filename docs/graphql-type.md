---
id: graphql-type
title: GraphQL: Types
sidebar_label: Types
---

## Patient

- id: String!
- events: [Event!]
- overlappingEvents: [Event!]

## Event

- name: String!
- start: String!
- end: String
- description: String
- colour: String

## EventTree

- name: String!
- id: Int!
- children: [Int!]!
- colour: String

## SubmittedEvent

- event: Int!
- start_time: String!
- end_time: String
- description: String
