ARG ALPINE_VERSION=3.11.5@sha256:b276d875eeed9c7d3f1cfa7edb06b22ed22b14219a7d67c52c56612330348239
FROM alpine:${ALPINE_VERSION}

# Install required packages
RUN apk -v --update add \
  python3 \
  # required for `aws help`
  groff \
  # clean up cache https://docs.docker.com/develop/develop-images/dockerfile_best-practices/#run
  && rm -rf /var/cache/apk/*

# Upgrade PIP
RUN python3 -m pip install --upgrade pip

# Install AWS CLI
RUN pip3 install awscli --upgrade
