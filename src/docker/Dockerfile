FROM ubuntu:22.04

ARG ARCH_ALIAS=amd64

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    pkg-config ca-certificates apt-transport-https curl

RUN KUBECTL_VERSION=$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt) && \
    curl -s "https://storage.googleapis.com/kubernetes-release/release/${KUBECTL_VERSION}/bin/linux/${ARCH_ALIAS}/kubectl" -o /usr/local/bin/kubectl && \
    chmod a+x /usr/local/bin/kubectl
