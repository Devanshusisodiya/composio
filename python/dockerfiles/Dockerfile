FROM python:slim

# Install dependencies
RUN apt update \
    && apt install  -y \
    git \
    curl \
    sudo \
    python3-dev \
    python3-pip \
    python3-venv \
    uuid-runtime \
    openssh-server

# Create Venv
RUN /bin/python3 -m venv .composio/venv

# Setup path
RUN export PATH=$PATH:$(pwd)/.composio/venv/bin

# Install composio
RUN python -m pip install composio-core[all]==0.3.27 fastapi

# Setup user
RUN useradd -rm -d /home/user -s /bin/bash -g root -G sudo -u 1000 user

# Define entry point
COPY entrypoint.sh /root/entrypoint.sh

# Run entrypoint.sh
ENTRYPOINT [ "/root/entrypoint.sh" ]
