---
title: Sylph - Deployment
sidebar_label: Deployment
---

## Software Architecture

Sylph consists of two layers:

- React front-end
- GraphQL and LokiJS back-end

## Deploy in Development

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

Add an `.env` file in the root directory with the following content:

```
REACT_APP_BASENAME="."
```

Then start the development server.

```
yarn start
```

This should automatically open `http://localhost:3000` on your browser. If not, then navigate to that URL.

## Deploy onto server

Deployment onto a server (for staging or production) is done through Docker images -- one for each layer.

### System Requirements

- [Docker](https://docker.com)
- [Docker Compose](https://docs.docker.com/compose/)

### Building Docker image: GraphQL

Set up as you would for development deployment:

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

### Building Docker image: React

Set up as you would for development deployment:

```
git clone https://github.com/shahcompbio/sylph-react
cd sylph-react
yarn install
```

Add an `.env` file with the appropriate content (see [env files](sylph/env-files) for specific files) and then build:

```
REACT_APP_BASENAME="<SUBDOMAIN_HERE>"
PUBLIC_URL="<URL_HERE>"
```

```
docker build . -t sylph-react --build-arg BUILD_ENV="staging"

docker build . -t sylph-react --build-arg BUILD_ENV="prod"
```

Then tag and push to Docker Hub

```
docker tag sylph-react shahcompbio/sylph-react
docker push shahcompbio/sylph-react
```

### Deploy

In the server where you want to host your instance, clone Sylph's Docker repository:

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

## Future Plans

- Automate deployment of staging / production (TravisCI?)
- Automate rebuilding of images when pushed to repo (Docker Hub already seems to support this)
