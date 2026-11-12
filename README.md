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

## Versions

The exact .NET SDK version and the `cimg/base` version are pinned in each folder's `Dockerfile` (`8/`, `9/`, `10/`, `11/`) and updated by Renovate (see `.github/renovate.json`).

## Build and publish

The images are built and published by Docker Hub's automated build from `main` (folder `8/`, `9/`, `10/`, `11/` to tag `8.0`, `9.0`, `10.0`, `11.0`). Every merge to `main` rebuilds all four tags.

### Adding a new .NET version

Adding a folder is not enough on its own. The folder-to-tag mapping lives in Docker Hub, not in this repo, so Docker Hub ignores a new folder until it has a build rule. Without one, the merge builds the existing tags, nothing fails, and the new tag never appears.

1. Add the folder, its Renovate rules and its row in the tag table above.
2. Before merging, add a build rule in Docker Hub under `tibber/ci-image-dotnet` → Builds → Configure Automated Builds: source type `Branch`, source `main`, Docker tag `<major>.0`, Dockerfile location `Dockerfile`, build context `/<major>`. This needs admin access to the `tibber` organisation on Docker Hub.
3. After merging, check the merge commit's statuses on GitHub. There should be a `ci/dockercloud-stage (/<major>)` status for each folder.

Renovate automerges docker digest, patch and minor bumps and .NET SDK bumps (SDK bumps wait 7 days), see `.github/renovate.json`.
