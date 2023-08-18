# Use the official Ubuntu 20.04 image as base
FROM ubuntu:20.04

# Update packages and install necessary tools
RUN apt-get update && apt-get upgrade -y && \
    apt-get install -y software-properties-common

# Add deadsnakes PPA for installing different Python versions
RUN add-apt-repository ppa:deadsnakes/ppa

# Update packages again after adding PPA
RUN apt-get update

# Install Python 3.10 and pip for Python 3.10
RUN apt-get install -y python3.10 python3.10-distutils curl && \
    curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py && \
    python3.10 get-pip.py && \
    rm get-pip.py

# Update alternatives to set python3.10 as the default python3 version
RUN update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.10 1 && \
    update-alternatives --install /usr/bin/python python /usr/bin/python3.10 1

# install package
RUN pip install "fastapi[all]"

RUN pip install selenium

RUN pip install bs4