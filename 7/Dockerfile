FROM mcr.microsoft.com/dotnet/sdk:7.0

# Check latest version at https://api.github.com/repos/docker/cli/tags
ENV DOCKER_VERSION 20.10.22

RUN set -x && \
    apt-get update && \
    apt-get -y install unzip jq gettext-base

RUN curl -L -o /tmp/docker-$DOCKER_VERSION.tgz https://download.docker.com/linux/static/stable/x86_64/docker-$DOCKER_VERSION.tgz && \
    tar -xz -C /tmp -f /tmp/docker-$DOCKER_VERSION.tgz && \
    mv /tmp/docker/* /usr/bin
