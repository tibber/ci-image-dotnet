FROM cimg/base:current@sha256:6438d46397dbdff5b4da4a95c29dd469d0c8d7408abc682874c09173249dfaea

# This convenience image by Circle CI (https://github.com/CircleCI-Public/cimg-base) runs Ubuntu 22.04
# in which you can install .NET 10.0 only by using backports ppa.
# See https://learn.microsoft.com/en-us/dotnet/core/install/linux-ubuntu#supported-distributions

RUN sudo add-apt-repository ppa:dotnet/previews && \
   sudo apt-get update && \
   sudo apt-get -y install gettext-base dotnet-sdk-10.0

# Install trx2junit to be used during build
RUN dotnet tool install -g trx2junit

ENV PATH="${PATH}:/home/circleci/.dotnet/tools"