# Tibber CI image for .NET

> Convenience images for running .NET Circle CI builds

This repository is needed because Circle CI does not have a ready-made image for building .NET (see https://circleci.com/docs/circleci-images).


List of image tags:

| Tag        | Based on                                           | Description                                                         |
| :---:      | :---:                                              | :---:                                                               |
| 8.0        | `cimg/base` (version pinned in `8/Dockerfile`)     | Circle CI base image with .NET SDK 8.0 installed via `dotnet-install.sh` w/ signature verification. Supports buildx used by `aws-ecr` orb.   |
| 9.0        | `cimg/base` (version pinned in `9/Dockerfile`)     | Circle CI base image with .NET SDK 9.0 installed via `dotnet-install.sh` w/ signature verification. Supports buildx used by `aws-ecr` orb.   |
| 10.0       | `cimg/base` (version pinned in `10/Dockerfile`)    | Circle CI base image with .NET SDK 10.0 installed via `dotnet-install.sh` w/ signature verification. Supports buildx used by `aws-ecr` orb.   |

The tags are moving tags: each one always points to the latest build of that .NET line.

## Versions

The exact .NET SDK version and the `cimg/base` version are pinned in each folder's `Dockerfile` (`8/`, `9/`, `10/`) and updated by Renovate (see `.github/renovate.json`).

### Which SDK is in an image?

```bash
docker run --rm --platform linux/amd64 tibber/ci-image-dotnet:10.0 ls /usr/share/dotnet/sdk
```

Prints the installed SDK version, for example `10.0.402`. The images are `linux/amd64` only, so on Apple Silicon keep the `--platform` flag.

## Build and publish

The images are built and published by Docker Hub's automated build from `main` (folder `8/`, `9/`, `10/` to tag `8.0`, `9.0`, `10.0`). Every merge to `main` rebuilds all three tags.

Renovate automerges docker digest, patch and minor bumps and .NET SDK bumps (SDK bumps wait 7 days), see `.github/renovate.json`.
