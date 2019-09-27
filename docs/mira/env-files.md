---
title: Mira - Env Files
sidebar_label: Env Files
---

## React Layer

### Development

`.env` file

```
REACT_APP_BASENAME="."
```

### Staging

`.spectrum.staging.env` file

```
REACT_APP_BASENAME="/mira"
PUBLIC_URL="http://40.87.0.178/mira"
```

To build:

```
docker build . -t mira-react:staging --build-arg ENV_PATH=".spectrum.staging.env"
```

### Production

`.spectrum.prod.env` file

```
REACT_APP_BASENAME="/scrna"
PUBLIC_URL="http://spectrum.mskcc.org/scrna"
```

To build:

```
docker build . -t mira-react --build-arg ENV_PATH=".spectrum.prod.env"
```
