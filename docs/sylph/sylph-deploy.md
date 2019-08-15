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

Clone [Sylph's graphQL](https://github.com/shahcompbio/sylph-graphql) repository:

```
git clone https://github.com/shahcompbio/sylph-graphql
```

Go into the directory and install the dependencies:

```
cd sylph-graphql
yarn install
```

Then start the development server.

```
yarn start
```

Following the URL `http://localhost:4000` should bring you to the GraphQL playground, where you can enter queries. LokiJS should populate with some initial data.

### React

Clone [Sylph's React](https://github.com/shahcompbio/sylph-react) repository:

```
git clone https://github.com/shahcompbio/sylph-react.git
```

Go into the directory and install the dependencies:

```
cd sylph-react
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
git clone https://github.com/shahcompbio/sylph-docker
```

The input form is password protected, and is linked to a file that contains the username and encrpyted password pairs.

```
cd sylph-docker

touch .users
```
Each password should be encrypted:

```
openssl passwd -apr1
```


Then run Docker Compose:

```
docker-compose up -d
```

Note that this binds to `localhost:5001` on your local server. For MSK, our main webserver redirects `~/cohort/surgery/` to `localhost:5001`.

### Alternative

If you would prefer to run the images without Docker Compose, they can be run as separate containers:

```
docker pull shahcompbio/sylph-graphql

docker pull shahcompbio/sylph-react

docker run -d -p 4000:4000 --name graphql sylph-graphql

docker run -d -p 80:80 --link graphql:graphql sylph-react
```

### Deploying new version

The instructions above shows how to deploy a production-level instance of Sylph using pre-built images hosted on Docker Hub. There are two images - one for each layer.

To update an image, first set up as you would for development deployment (this is shown for the graphQL layer - the instructions are similar for the React layer):

```
git clone https://github.com/shahcompbio/sylph-graphql
cd sylph-graphql
yarn install
```

Then run the Dockerfile to build a new image:

```
docker build . -t sylph-graphql
```

Then tag and push to Docker Hub

```
docker tag sylph-graphql shahcompbio/sylph-graphql
docker push shahcompbio/sylph-graphql
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
