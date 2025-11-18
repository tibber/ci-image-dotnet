# Tibber CI image for .NET

> Convenience images for running .NET Circle CI builds

This repository is needed because Circle CI does not have a ready-made image for building .NET (see https://circleci.com/docs/circleci-images).


List of image tags:

| Tag        | Based on                                | Description                                                         |
| :---:      | :---:                                   | :---:                                                               |
| 6          | cimg/base:current                       | Circle CI base image with .NET `dotnet-sdk-6.0` installed from Microsofts's package repository. Supports buildx used by `aws-ecr` orb.   |
| 7-alpine   | mcr.microsoft.com/dotnet/sdk:7.0-alpine | Microsoft Alpine image with Docker installed. Does not support Docker buildx / Buildkit.                      |
| 7          | cimg/base:current                       | Circle CI base image with .NET `dotnet-sdk-7.0` installed from Microsofts's package repository. Supports buildx used by `aws-ecr` orb.   |
| 8          | cimg/base:current                       | Circle CI base image with .NET `dotnet-sdk-8.0` installed from Microsofts's package repository. Supports buildx used by `aws-ecr` orb.   |
| 9          | cimg/base:current                       | Circle CI base image with .NET `dotnet-sdk-9.0` installed from Ubuntu's package repository (backport ppa needed for 22.04). Supports buildx used by `aws-ecr` orb.   |
| 10         | cimg/base:current                       | Circle CI base image with .NET SDK 10.0 installed via `dotnet-install.sh` w/ signature verification. Supports buildx used by `aws-ecr` orb.   |

# This image is built in Dockerhub
