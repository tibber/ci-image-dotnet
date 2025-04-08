FROM cimg/base:current@sha256:6438d46397dbdff5b4da4a95c29dd469d0c8d7408abc682874c09173249dfaea

# This convenience image by Circle CI (https://github.com/CircleCI-Public/cimg-base) runs Ubuntu 22.04
# in which you can install .NET 9.0 only by using backports ppa.
# See https://learn.microsoft.com/en-us/dotnet/core/install/linux-ubuntu#supported-distributions

# Problem 1: Must use ppa:dotnet/backports to get .NET 9. Remove when cimg/base runs Ubuntu 24.04
#RUN sudo add-apt-repository ppa:dotnet/backports && \
#    sudo apt-get update && \
#    sudo apt-get -y install gettext-base dotnet-sdk-9.0
#RUN dotnet tool install -g trx2junit

# Problem 2: ppa:dotnet/backports only provides .NET 9.0.104
# => install .NET manually using Microsoft maintained packages

RUN set -x && \
    repo_version=$(if command -v lsb_release >/dev/null 2>&1; then lsb_release -r -s; else grep -oP '(?<=^VERSION_ID=).+' /etc/os-release | tr -d '"'; fi) && \
    wget https://packages.microsoft.com/config/ubuntu/$repo_version/packages-microsoft-prod.deb -O packages-microsoft-prod.deb && \
    sudo dpkg -i packages-microsoft-prod.deb && \
    rm packages-microsoft-prod.deb

# Use Microsoft packages instead of Ubuntu so we can later install trx2unit
COPY 99microsoft-dotnet.pref /etc/apt/preferences.d

RUN sudo apt-get update && \
    sudo apt-get -y install gettext-base dotnet-sdk-9.0

# Install trx2junit to be used during build
RUN dotnet tool install -g trx2junit

ENV PATH="${PATH}:/home/circleci/.dotnet/tools"