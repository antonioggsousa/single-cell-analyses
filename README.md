# Docker images for reproducible single-cell data analyses

**Maintainer**: António Sousa (aggode@utu.fi)

<br>

---

<br>

## Contents

* [Build image](#build-image)

* [Run container](#run-container)


<br>

---

<br>

## Build image 

1. Main: Build & push the image to personal docker hub (aggode) - compatible only with `amd64`:

`docker login -u aggode` # type password

`docker build -f Dockerfile-amd64 -t sctoolkit .`

`docker image tag sctoolkit aggode/sctoolkit:latest`

`docker image push aggode/sctoolkit:latest`

<br>

2. Alternative: Build & push the image to personal docker hub (aggode) - compatible `amd64` & `arm64`: 

>ongoing: can't install system library `llvm-10` in w/ base image `rocker/rstudio:latest-daily`):

`docker run --rm --privileged tonistiigi/binfmt`

`docker buildx create --name mybuilder`

`docker buildx use mybuilder`

`docker buildx inspect --bootstrap`

`docker buildx build --no-cache --push --platform linux/amd64,linux/arm64 -t aggode/sctoolkit:latest -f Dockerfile-cross-platform .`

<br>

---

<br>

## Run container

>Singularity

`singularity pull docker://aggode/sctoolkit:latest`

