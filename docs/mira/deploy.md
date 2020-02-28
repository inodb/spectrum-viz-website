---
title: Mira - Deployment
sidebar_label: Deployment
---

## Deploy: Development

### System Requirements

- [Yarn](https://yarnpkg.com/en/) (or [npm](https://www.npmjs.com/))
- [Docker](https://docker.com)

### Elasticsearch

Pull the docker image for Elasticsesarch (v.7.1.1) and then run the container:

```
docker pull docker.elastic.co/elasticsearch/elasticsearch:7.1.1

docker run -d -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.1.1
```

To load data, follow [these instructions](mira/loading-data.md).

### GraphQL

Clone Mira's graphQL repository:

```
git clone https://github.com/shahcompbio/mira-graphql
```

Go into the directory and install the dependencies:

```
cd mira-graphql
yarn install
```

Then start the development server.

```
yarn start
```

Following the URL `http://localhost:4000` should bring you to the GraphQL playground, where you can enter queries.

### React

Clone [Mira's React](https://github.com/shahcompbio/mira-react) repository:

```
git clone https://github.com/shahcompbio/mira-react.git
```

Go into the directory, add an `.npmrc` file with the fontawesome token (provided by Samantha).

```
cd mira-react
touch .npmrc
```

Install the dependencies:

```
yarn install
```

Then start the development server.

```
yarn start
```

This should automatically open `http://localhost:3000` on your browser. If not, then navigate to that URL.

## Deploy

### System Requirements

- [Docker](https://docker.com)
- [Docker Compose](https://docs.docker.com/compose/)

### Environment

TODO: Flesh out more...

1. Create VM for ES nodes
2. Pull down docker repo for Mira, pull down docker images for db
3. Start docker-compose
4. Create VM for ws (install nginx?)
5. Pull down docker images for app (make sure to also change host name for graphql)
6. Start docker-compose
7. Here is the right nginx config

### Instructions

In the server where you want to host your production instance, clone Mira's Docker repository:

```
git clone https://github.com/shahcompbio/mira-docker
```

Then run Docker Compose:

```
docker-compose up -d
```

Note that this binds to `localhost` on your local server. You'll need to setup a proxy server to redirect it

### Deploying new version

The instructions above shows how to deploy a production-level instance of Mira using pre-built images hosted on Docker Hub. There are two images - one for the graphQL layer and one for the React layer

To update an image, first set up as you would for development deployment:

```

git clone https://github.com/shahcompbio/mira-graphql

cd mira-graphql

yarn install

```

Then run the Dockerfile to build a new image:

```

docker build . -t mira-graphql

```

Then tag and push to Docker Hub

```

docker tag mira-graphql shahcompbio/mira-graphql

docker push shahcompbio/mira-graphql

```

For the `react` layer, the instructions are similar but you'll need to ensure that you have the right environment file. For staging, the file name is `.spectrum.staging.env`, and for production it is `.spectrum.prod.env`

```
REACT_APP_BASENAME=""
PUBLIC_URL=""
WIKI_URL=""
MIRA_URL=""
SYLPH_URL=""
HYDRA_URL=""
```

Then to build:

```
docker build . -t mira-react:staging --build-arg BUILD_ENV="staging"
OR
docker build . -t mira-react --build-arg BUILD_ENV="prod"
```

Then tag and push to Docker Hub

```
docker tag mira-react shahcompbio/mira-react

docker push shahcompbio/mira-react
```

Once that's complete, go to where your production instance, then pull and restart your docker instance.

```

docker-compose pull

docker-compose down

docker-compose up -d

```
