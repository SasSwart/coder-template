FROM ubuntu

RUN apt-get update
RUN apt-get install vim sudo curl -y

# Install Go manually, so that we can control the version
ARG GO_VERSION=1.22.5

# Boring Go is needed to build FIPS-compliant binaries.
RUN apt-get update && \
	apt-get install --yes curl && \
	curl --silent --show-error --location \
	"https://go.dev/dl/go${GO_VERSION}.linux-amd64.tar.gz" \
	-o /usr/local/go.tar.gz && \
	rm -rf /var/lib/apt/lists/*

ARG USER sas
RUN useradd -m -s /bin/bash -G sudo ${USER}
USER ${USER}