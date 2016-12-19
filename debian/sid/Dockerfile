FROM debian:sid
MAINTAINER fooinha <fooinha@gmail.com>
ARG MAINTANER_NAME=fooinha
ARG MAINTANER_EMAIL=fooinha@gmail.com

# Build arguments
ARG DEBIAN_REPO_HOST=httpredir.debian.org

# Mirror to my location
RUN echo "deb http://${DEBIAN_REPO_HOST}/debian sid main" > /etc/apt/sources.list
RUN echo "deb-src http://${DEBIAN_REPO_HOST}/debian sid main" >> /etc/apt/sources.list

# Update
RUN DEBIAN_FRONTEND=noninteractive apt-get update || true

# Install build dependencies
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y --fix-missing \
    apt-utils \
    git-core \
    build-essential \
    devscripts \
    make \
    valgrind \
    autoconf \
    automake \
    dh-autoreconf \
    libtool \
    libpcap-dev \
    libnet1-dev \
    libyaml-0-2 \
    libyaml-dev \
    zlib1g \
    zlib1g-dev \
    libcap-ng-dev \
    libcap-ng0 \
    libpcre3 \
    libpcre3-dbg \
    libpcre3-dev \
    libmagic-dev \
    libnetfilter-queue-dev \
    libnetfilter-queue1 \
    libnfnetlink-dev \
    libnetfilter-log-dev \
    libprelude-dev \
    libnfnetlink0 \
    libjansson-dev \
    libnss3-dev \
    libnspr4-dev \
    libgeoip1 \
    libgeoip-dev \
    libluajit-5.1-common \
    libluajit-5.1-dev \
    libhiredis-dev \
    python \
    wget \
    jq \
    vim \
    tcpdump \
    ngrep \
    bind9-host


CMD ["/bin/bash"]
