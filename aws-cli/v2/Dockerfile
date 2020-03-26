# Ubuntu is the smallest supported distribution
# - https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html#cliv2-linux-prereq
# - https://github.com/aws/aws-cli/issues/4685#issuecomment-556436861
ARG UBUNTU_VERSION=18.04@sha256:bec5a2727be7fff3d308193cfde3491f8fba1a2ba392b7546b43a051853a341d
FROM ubuntu:${UBUNTU_VERSION}

# Copy AWS public key
# https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html#v2-install-linux-validate
COPY aws.pub .

# Install required packages
RUN apt-get update && apt-get install -y --no-install-recommends \
  ca-certificates \
  curl \
  gnupg \
  # required for `aws help`
  groff \
  unzip \
  # clean up cache https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#run
  && rm -rf /var/lib/apt/lists/*

# Download, verify, and install
RUN curl https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip -o awscliv2.zip \
  && gpg --import aws.pub \
  && curl https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip.sig -o awscliv2.sig \
  && gpg --verify awscliv2.sig awscliv2.zip \
  && unzip awscliv2.zip \
  && ./aws/install
