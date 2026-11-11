# Tibber CI image for .NET

> Convenience images for running .NET Circle CI builds

This repository is needed because Circle CI does not have a ready-made image for building .NET (see https://circleci.com/docs/circleci-images).


List of image tags:

| Tag        | Based on                                           | Description                                                         |
| :---:      | :---:                                              | :---:                                                               |
| 8.0        | `cimg/base` (version pinned in `8/Dockerfile`)     | Circle CI base image with .NET SDK 8.0 installed via `dotnet-install.sh` w/ signature verification. Supports buildx used by `aws-ecr` orb.   |
| 9.0        | `cimg/base` (version pinned in `9/Dockerfile`)     | Circle CI base image with .NET SDK 9.0 installed via `dotnet-install.sh` w/ signature verification. Supports buildx used by `aws-ecr` orb.   |
| 10.0       | `cimg/base` (version pinned in `10/Dockerfile`)    | Circle CI base image with .NET SDK 10.0 installed via `dotnet-install.sh` w/ signature verification. Supports buildx used by `aws-ecr` orb.   |
| 11.0       | `cimg/base` (version pinned in `11/Dockerfile`)    | Circle CI base image with .NET SDK 11.0 installed via `dotnet-install.sh` w/ signature verification. Supports buildx used by `aws-ecr` orb.   |

The tags are moving tags: each one always points to the latest build of that .NET line.

`8.0`, `9.0` and `10.0` ship `trx2junit` as a global tool; `11.0` does not. On `11.0`, declare it in the repo's `.config/dotnet-tools.json` and call it as `dotnet trx2junit` after `dotnet tool restore`, or let xunit write JUnit directly with `--report-xunit-junit`.

## Versions

The exact .NET SDK version and the `cimg/base` version are pinned in each folder's `Dockerfile` (`8/`, `9/`, `10/`, `11/`) and updated by Renovate (see `.github/renovate.json`).

## Build and publish

The images are built and published by Docker Hub's automated build from `main` (folder `8/`, `9/`, `10/`, `11/` to tag `8.0`, `9.0`, `10.0`, `11.0`). Every merge to `main` rebuilds all four tags.

Renovate automerges docker digest, patch and minor bumps and .NET SDK bumps (SDK bumps wait 7 days), see `.github/renovate.json`.
