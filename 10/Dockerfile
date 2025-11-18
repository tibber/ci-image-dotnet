FROM cimg/base:current@sha256:914f8f3896bc4033634a446552a8c256f19fdb56aa4e999cf493961d0681bc48

# Install GPG and import Microsoft's public key for dotnet-install script verification
RUN sudo apt-get update && \
    sudo apt-get -y install gpg && \
    sudo rm -rf /var/lib/apt/lists/* && \
    # Download and import Microsoft's public key
    wget https://dot.net/v1/dotnet-install.asc && \
    gpg --import dotnet-install.asc && \
    rm dotnet-install.asc

# Download, verify, and install .NET SDK 10.0
RUN wget https://dot.net/v1/dotnet-install.sh && \
    wget https://dot.net/v1/dotnet-install.sig && \
    # Verify the GPG signature
    gpg --verify dotnet-install.sig dotnet-install.sh && \
    # Make script executable and run installation
    chmod +x dotnet-install.sh && \
    sudo ./dotnet-install.sh --channel 10.0 --install-dir /usr/share/dotnet && \
    # Cleanup
    rm dotnet-install.sh dotnet-install.sig && \
    sudo ln -s /usr/share/dotnet/dotnet /usr/local/bin/dotnet

RUN sudo apt-get update && \
    sudo apt-get -y install gettext-base && \
    sudo rm -rf /var/lib/apt/lists/*

ENV DOTNET_CLI_TELEMETRY_OPTOUT=1 \
    DOTNET_ROOT=/usr/share/dotnet \
    PATH="${PATH}:/home/circleci/.dotnet/tools"

# Install trx2junit to be used during build
RUN dotnet tool install -g trx2junit