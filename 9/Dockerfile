FROM cimg/base:current@sha256:03c91d4730297b5af3718e1e81d43e210eae02be271ed7d370ccb3b994dad2bd

# This convenience image by Circle CI (https://github.com/CircleCI-Public/cimg-base) runs Ubuntu 22.04
# in which you can install .NET 9.0 only by using backports ppa.
# See https://learn.microsoft.com/en-us/dotnet/core/install/linux-ubuntu#supported-distributions

# Remove ppa:dotnet/backports when cimg/base runs Ubuntu 24.04

RUN sudo add-apt-repository ppa:dotnet/backports && \
    sudo apt-get update && \
    sudo apt-get -y install gettext-base dotnet-sdk-9.0
RUN dotnet tool install -g trx2junit

ENV PATH="${PATH}:/home/circleci/.dotnet/tools"
