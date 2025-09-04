FROM cimg/base:current@sha256:6438d46397dbdff5b4da4a95c29dd469d0c8d7408abc682874c09173249dfaea

RUN sudo add-apt-repository ppa:dotnet/previews && \
   sudo apt-get update && \
   sudo apt-get -y install gettext-base dotnet-sdk-10.0

# Install trx2junit to be used during build
RUN dotnet tool install -g trx2junit

ENV PATH="${PATH}:/home/circleci/.dotnet/tools"