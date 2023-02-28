FROM mcr.microsoft.com/dotnet/sdk:7.0-alpine

# Check latest version at https://api.github.com/repos/docker/cli/tags
ENV DOCKER_VERSION 23.0.1

RUN set -x && \
    apk update && apk add aws-cli jq gettext bash  && \
    curl -L -o /tmp/docker-$DOCKER_VERSION.tgz https://download.docker.com/linux/static/stable/x86_64/docker-$DOCKER_VERSION.tgz && \
    tar -xz -C /tmp -f /tmp/docker-$DOCKER_VERSION.tgz && \
    mv /tmp/docker/* /usr/bin && \
    dotnet tool install -g trx2junit

ENV PATH="${PATH}:/root/.dotnet/tools"
    
