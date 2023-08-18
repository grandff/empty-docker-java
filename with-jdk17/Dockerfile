# Use the official Ubuntu 20.04 image as the base image
FROM ubuntu:20.04

# Set environment variables to prevent interactive prompts during installation
ENV DEBIAN_FRONTEND=noninteractive

# Update the package repositories and install necessary packages
RUN apt-get update \
    && apt-get install -y \
    software-properties-common \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install Docker
RUN apt-get update \
    && apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release \
    && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg \
    && echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null \
    && apt-get update \
    && apt-get install -y \
    docker-ce \
    docker-ce-cli \
    containerd.io \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install OpenJDK 17
RUN apt-get update \
    && apt-get install -y \
    openjdk-17-jdk

# Install git
RUN apt-get update \
    && apt-get install -y \
    git

# Set environment variables
RUN echo "JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64" >> /etc/environment

# Set up the entrypoint to run the Docker daemon
#CMD ["dockerd"]
