---
id: sylph-deploy
title: Sylph - Deployment
sidebar_label: Deployment
---

## Software Architecture

Sylph consists of two layers:

- React front-end
- GraphQL and LokiJS back-end

## Deploy: Development

### System Requirements

- [Yarn](https://yarnpkg.com/en/) (or [npm](https://www.npmjs.com/))

### GraphQL + LokiJS

Clone Sylph's graphQL repository:

```
git clone https://github.com/shahcompbio/spectrum-cohort-graphql
```

Go into the directory and install the dependencies:

```
cd spectrum-cohort-graphql
yarn install
```

Then start the development server.

```
yarn start
```

Following the URL `http://localhost:4000` should bring you to the GraphQL playground, where you can enter queries. LokiJS should populate with some initial data.

### React

Clone [Sylph's React](https://github.com/shahcompbio/spectrum-cohort-react) repository:

```
git clone https://github.com/shahcompbio/spectrum-cohort-react.git
```

Go into the directory and install the dependencies:

```
cd spectrum-cohort-react
yarn install
```

Then start the development server.

```
yarn start
```

This should automatically open `http://localhost:3000` on your browser. If not, then navigate to that URL.

## Deploy: Staging

TBD

## Deploy: Production

### System Requirements

- [Docker](https://docker.com)
- [Docker Compose](https://docs.docker.com/compose/)

### Instructions

In the server where you want to host your production instance, clone Sylph's Docker repository:

```
git clone https://github.com/shahcompbio/spectrum-cohort-docker
```

Then run Docker Compose:

```
docker-compose up -d
```

Note that this binds to `localhost:5001` on your local server. For MSK, our main webserver redirects `~/cohort/surgery/` to `localhost:5001`.

### Deploying new version

The instructions above shows how to deploy a production-level instance of Sylph using pre-built images hosted on Docker Hub. There are two images - one for each layer.

To update an image, first set up as you would for development deployment (this is shown for the graphQL layer - the instructions are similar for the React layer):

```
git clone https://github.com/shahcompbio/spectrum-cohort-graphql
cd spectrum-cohort-graphql
yarn install
```

Then run the Dockerfile to build a new image:

```
docker build . -t spectrum-cohort-graphql
```

Then tag and push to Docker Hub

```
docker tag spectrum-cohort-graphql shahcompbio/spectrum-cohort-graphql
docker push shahcompbio/spectrum-cohort-graphql
```

Once that's complete, go to where your production instance, then pull and restart your docker instance.

```
docker-compose pull
docker-compose down

docker-compose up -d
```

## Future Plans

- Complete Staging set up
- Automate deployment of staging / production (TravisCI?)
- Automate rebuilding of images when pushed to repo (Docker Hub already seems to support this)
