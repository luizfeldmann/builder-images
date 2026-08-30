FROM alpine:3.23

WORKDIR /workspace

# Install build tools
RUN apk add --no-cache \
    git \
    bash \
    nasm \
    build-base \
    linux-headers \
    jq \
    zip \
    unzip \
    curl \
    ninja \
    cmake \
    python3 \
    py3-pip

# Prepare python venv
RUN python3 -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"

# Install conan
RUN pip install --upgrade pip && \
    pip install "conan==2.30.0" && \
    conan profile detect
