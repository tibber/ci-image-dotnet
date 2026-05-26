# Tibber CI image for .NET

> Convenience images for running .NET Circle CI builds

This repository is needed because Circle CI does not have a ready-made image for building .NET (see https://circleci.com/docs/circleci-images).


List of image tags:

| Tag        | Based on                                | Description                                                         |
| :---:      | :---:                                   | :---:                                                               |
| 8          | cimg/base:current                       | Circle CI base image with .NET SDK 8.0 installed via `dotnet-install.sh` w/ signature verification. Supports buildx used by `aws-ecr` orb.   |
| 9          | cimg/base:current                       | Circle CI base image with .NET SDK 9.0 installed via `dotnet-install.sh` w/ signature verification. Supports buildx used by `aws-ecr` orb.   |
| 10         | cimg/base:current                       | Circle CI base image with .NET SDK 10.0 installed via `dotnet-install.sh` w/ signature verification. Supports buildx used by `aws-ecr` orb.   |

# This image is built in Dockerhub
