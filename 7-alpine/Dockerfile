FROM mcr.microsoft.com/dotnet/sdk:7.0-alpine@sha256:1478c99b4bed8d297ccd000e0fdaf060cdfb281779f8c8aa47f031a09503c0d4

# Check latest version at https://api.github.com/repos/docker/cli/tags
ENV DOCKER_VERSION 23.0.1

RUN set -x && \
    apk update && apk add aws-cli jq gettext bash build-base  && \
    curl -L -o /tmp/docker-$DOCKER_VERSION.tgz https://download.docker.com/linux/static/stable/x86_64/docker-$DOCKER_VERSION.tgz && \
    tar -xz -C /tmp -f /tmp/docker-$DOCKER_VERSION.tgz && \
    mv /tmp/docker/* /usr/bin && \
    dotnet tool install -g trx2junit

ENV PATH="${PATH}:/root/.dotnet/tools"

