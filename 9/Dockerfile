FROM cimg/base:current@sha256:c4b738db95b65caeb66429913ce5ef53e203ee30bcf050896c9a6694a335b942

# This convenience image by Circle CI (https://github.com/CircleCI-Public/cimg-base) runs Ubuntu 22.04
# in which you can install .NET 9.0 only by using backports ppa.
# See https://learn.microsoft.com/en-us/dotnet/core/install/linux-ubuntu#supported-distributions

# Remove ppa:dotnet/backports when cimg/base runs Ubuntu 24.04

RUN sudo add-apt-repository ppa:dotnet/backports && \
    sudo apt-get update && \
    sudo apt-get -y install gettext-base dotnet-sdk-9.0
RUN dotnet tool install -g trx2junit

ENV PATH="${PATH}:/home/circleci/.dotnet/tools"
