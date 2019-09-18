---
title: Hydra - Deployment
sidebar_label: Deployment
---

## Software Architecture

Hydra consists of two layers:

- React front-end
- GraphQL back-end (connected to REDCap)

## Deploy: Development

### System Requirements

- [Yarn](https://yarnpkg.com/en/) (or [npm](https://www.npmjs.com/))

### GraphQL + LokiJS

Clone [Hydra's graphQL](https://github.com/shahcompbio/hydra-graphql) repository:

```
git clone https://github.com/shahcompbio/hydra-graphql
```

Go into the directory and install the dependencies:

```
cd hydra-graphql

yarn install
```

Create an `.env` file and copy in the API token and URL from the REDCap connection.

```
cd hydra-graphql

vi .env
```

Here is an example structure of the `.env` file:

```
API_TOKEN=<API Token here>
URI=<Link to REDCap API here>
```

Then start the development server.

```
yarn start
```

Following the URL `http://localhost:4000` should bring you to the GraphQL playground, where you can enter queries.

### React

Clone [Hydra's React](https://github.com/shahcompbio/hydra-react) repository:

```
git clone https://github.com/shahcompbio/hydra-react.git
```

Go into the directory and install the dependencies:

```
cd hydra-react
yarn install
```

Then start the development server.

```
yarn start
```

This should automatically open `http://localhost:3000` on your browser. If not, then navigate to that URL.
