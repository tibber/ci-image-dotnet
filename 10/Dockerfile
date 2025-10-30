FROM cimg/base:current@sha256:914f8f3896bc4033634a446552a8c256f19fdb56aa4e999cf493961d0681bc48

RUN sudo add-apt-repository ppa:dotnet/previews && \
   sudo apt-get update && \
   sudo apt-get -y install gettext-base dotnet-sdk-10.0

# Install trx2junit to be used during build
RUN dotnet tool install -g trx2junit

ENV PATH="${PATH}:/home/circleci/.dotnet/tools"