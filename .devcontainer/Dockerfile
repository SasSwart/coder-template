# Use Ubuntu as the base image
FROM ubuntu

# Update package list and install required packages
RUN apt-get update && \
    apt-get install -y vim sudo curl git python3 python3-pip zsh && \
    rm -rf /var/lib/apt/lists/*

# Set the Go version
ARG GO_VERSION=1.22.5

# Download and install Go manually to control the version
RUN curl --silent --show-error --location \
    "https://go.dev/dl/go${GO_VERSION}.linux-amd64.tar.gz" \
    -o /usr/local/go.tar.gz && \
    tar -C /usr/local -xzf /usr/local/go.tar.gz && \
    rm /usr/local/go.tar.gz

# Add Go to PATH
ENV PATH="/usr/local/go/bin:${PATH}"

# Create a new user and add it to the sudo group
ARG USER=sas
RUN useradd -m -s /bin/zsh -G sudo ${USER}

# Install Oh My Zsh for the user
RUN curl -Lo install.sh https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh && \
    chmod +x install.sh && \
    RUNZSH=no CHSH=no /bin/zsh install.sh && \
    rm install.sh
