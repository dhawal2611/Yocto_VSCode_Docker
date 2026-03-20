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


# Create the 'yocto' user
RUN groupadd -g 1000 yocto \
    && useradd -u 1000 -g yocto -m -s /bin/bash yocto \
    && apt-get update && apt-get install -y sudo \
    && echo "yocto ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Set the active user
USER yocto
ENV HOME=/home/yocto

ENV LANG=en_US.UTF-8
ENV LANGUAGE=en_US:en
ENV LC_ALL=en_US.UTF-8

# # Create a user named 'vscode' (UID 1000 is standard for Dev Containers)
# ARG USERNAME=vscode
# ARG USER_UID=1000
# ARG USER_GID=$USER_UID

# RUN groupadd --gid $USER_GID $USERNAME \
#     && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
#     # Add sudo support so you can still install things if needed
#     && apt-get update \
#     && apt-get install -y sudo \
#     && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
#     && chmod 0440 /etc/sudoers.d/$USERNAME

# # Set the default user for the container
# USER $USERNAME

#EXPOSE 1883
#EXPOSE 8883

