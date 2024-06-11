FROM ubuntu:22.04

ARG KIBANA_VERSION=8.5.1

ARG ARCH=x86_64
ARG ARCH_ALIAS=amd64

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    pkg-config ca-certificates apt-transport-https curl

RUN KUBECTL_VERSION=$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt) && \
    curl -s "https://storage.googleapis.com/kubernetes-release/release/${KUBECTL_VERSION}/bin/linux/${ARCH_ALIAS}/kubectl" -o /usr/local/bin/kubectl && \
    chmod a+x /usr/local/bin/kubectl

RUN curl -O https://artifacts.elastic.co/downloads/kibana/kibana-${KIBANA_VERSION}-linux-${ARCH}.tar.gz && \
    curl https://artifacts.elastic.co/downloads/kibana/kibana-${KIBANA_VERSION}-linux-${ARCH}.tar.gz.sha512 | shasum -a 512 -c - && \
    tar -xzf kibana-${KIBANA_VERSION}-linux-${ARCH}.tar.gz

RUN kubectl version

WORKDIR /kibana-${KIBANA_VERSION}
