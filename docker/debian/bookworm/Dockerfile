FROM debian:bookworm

# Avoid prompts
ENV DEBIAN_FRONTEND=noninteractive

# Install build dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    build-essential \
    cmake \
    git \
    python3 \
    python3-pip \
    ninja-build \
    jq \
    curl \
    zip \
    unzip \
    && rm -rf /var/lib/apt/lists/*

# Install Conan
RUN python3 -m pip install --break-system-packages --no-cache-dir \
        "conan==2.30.0"

# Configure Conan profile
RUN conan profile detect --force

# Point to toolchain
ENV CC=gcc
ENV CXX=g++

WORKDIR /workspace
CMD ["/bin/bash"]
