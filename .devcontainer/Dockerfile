# Use a base image
FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

# Install required dependencies
RUN apt-get update && \
    apt-get install -y wget && \
    apt-get install -y git \ 
    build-essential \
    xsltproc \
    cmake libssl-dev \
    libwebsockets-dev \
    docbook-xsl \
    vim \
    mosquitto \
    mosquitto-clients \
    openssl \
    libmosquitto-dev \
    net-tools \
    python \
    python3 \
    python3-pip \ 
    gawk diffstat unzip texinfo gcc-multilib \
    chrpath socat cpio \
    python3-pexpect xz-utils debianutils iputils-ping \
    python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev \
    pylint python3-subunit mesa-common-dev zstd liblz4-tool


#RUN mosquitto -c /workspaces/test/conf/mosquitto_c.conf  -v


RUN git clone https://github.com/DaveGamble/cJSON.git

RUN cd cJSON && \
    mkdir build && \
    cd build && \
    cmake .. && \
    cmake --build . && \
    make install

#EXPOSE 1883
#EXPOSE 8883

