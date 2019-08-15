---
id: mira-deploy
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

docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.1.1 -d
```

To load data, follow [these instructions](mira-loading-data).

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

Go into the directory and install the dependencies:

```
cd mira-react
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

In the server where you want to host your production instance, clone Mira's Docker repository:

```
git clone https://github.com/shahcompbio/mira-docker
```

Then run Docker Compose:

```
docker-compose up -d
```

Note that this binds to `localhost` on your local server. For MSK, our main webserver redirects `~/scrna/` to the IP of the server we host Mira on.

### Deploying new version

The instructions above shows how to deploy a production-level instance of Mira using pre-built images hosted on Docker Hub. There are two images - one for the graphQL layer and one for the React layer

To update an image, first set up as you would for development deployment (this is shown for the graphQL layer - the instructions are similar for the React layer):

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

Once that's complete, go to where your production instance, then pull and restart your docker instance.

```

docker-compose pull

docker-compose down

docker-compose up -d

```

## Future Plans

- Complete Staging set up
- Provide example data for them to load
- Automate deployment of staging / production (TravisCI?)
- Automate rebuilding of images when pushed to repo (Docker Hub already seems to support this)

```

```
