FROM cimg/base:current@sha256:6438d46397dbdff5b4da4a95c29dd469d0c8d7408abc682874c09173249dfaea

RUN set -x && \
    repo_version=$(if command -v lsb_release >/dev/null 2>&1; then lsb_release -r -s; else grep -oP '(?<=^VERSION_ID=).+' /etc/os-release | tr -d '"'; fi) && \
    wget https://packages.microsoft.com/config/ubuntu/$repo_version/packages-microsoft-prod.deb -O packages-microsoft-prod.deb && \
    sudo dpkg -i packages-microsoft-prod.deb && \
    rm packages-microsoft-prod.deb

# Use Microsoft packages instead of Ubuntu so we can later install trx2unit
COPY 99microsoft-dotnet.pref /etc/apt/preferences.d

RUN sudo apt-get update && \
    sudo apt-get -y install gettext-base dotnet-sdk-7.0

# Install trx2junit to be used during build
RUN dotnet tool install -g trx2junit

ENV PATH="${PATH}:/home/circleci/.dotnet/tools"

RUN curl -Ls https://download.newrelic.com/install/newrelic-cli/scripts/install.sh | bash
