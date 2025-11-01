FROM cimg/base:current@sha256:f9e54a98a858e43aaa025a78fe62857d309dce4444f3d346dc281a2593d5d815

RUN sudo add-apt-repository ppa:dotnet/previews && \
   sudo apt-get update && \
   sudo apt-get -y install gettext-base dotnet-sdk-10.0

# Install trx2junit to be used during build
RUN dotnet tool install -g trx2junit

ENV PATH="${PATH}:/home/circleci/.dotnet/tools"