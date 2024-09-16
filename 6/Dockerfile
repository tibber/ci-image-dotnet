FROM cimg/base:current@sha256:161944153a72083104b19d44575faf5fc838b904fafa57e241002eefd8b3ed55

RUN set -x && \
    repo_version=$(if command -v lsb_release >/dev/null 2>&1; then lsb_release -r -s; else grep -oP '(?<=^VERSION_ID=).+' /etc/os-release | tr -d '"'; fi) && \
    wget https://packages.microsoft.com/config/ubuntu/$repo_version/packages-microsoft-prod.deb -O packages-microsoft-prod.deb && \
    sudo dpkg -i packages-microsoft-prod.deb && \
    rm packages-microsoft-prod.deb

# Use Microsoft packages instead of Ubuntu so we can later install trx2unit
COPY 99microsoft-dotnet.pref /etc/apt/preferences.d

RUN sudo apt-get update && \
    sudo apt-get -y install gettext-base dotnet-sdk-6.0

# Install trx2junit to be used during build
RUN dotnet tool install -g trx2junit

ENV PATH="${PATH}:/home/circleci/.dotnet/tools"
