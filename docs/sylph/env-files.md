---
title: Sylph - Env Files
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
REACT_APP_BASENAME="/sylph"
PUBLIC_URL="http://40.87.0.178/sylph"
```

To build:

```
docker build . -t sylph-react:staging --build-arg ENV_PATH=".spectrum.staging.env"
```

### Production

`.spectrum.prod.env` file

```
REACT_APP_BASENAME="/cohort/surgery"
PUBLIC_URL="http://spectrum.mskcc.org/cohort/surgery"
```

To build:

```
docker build . -t sylph-react --build-arg ENV_PATH=".spectrum.prod.env"
```
