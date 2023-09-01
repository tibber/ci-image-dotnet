# Tibber CI image for .NET

> Convenience images for running .NET Circle CI builds

This repository is needed because Circle CI does not have a ready-made image for building .NET (see https://circleci.com/docs/circleci-images).


List of image tags:


| Tag      | Based on                                | Description                                                         |
| :---:    | :---:                                   | :---:                                                               |
| 6        | cimg/base:current                       | Circle CI base image with .NET `dotnet-sdk-6.0` installed. Supports buildx used by `aws-ecr` orb.   |
| 7-alpine | mcr.microsoft.com/dotnet/sdk:7.0-alpine | Microsoft Alpine image with Docker installed. Does not support Docker buildx / Buildkit.                      |
| 7        | cimg/base:current                       | Circle CI base image with .NET `dotnet-sdk-7.0` installed. Supports buildx used by `aws-ecr` orb.   |
