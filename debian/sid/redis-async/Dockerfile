FROM fooinha/suricata-experimental:debian-sid-build
MAINTAINER fooinha <fooinha@gmail.com>
ARG MAINTANER_NAME=fooinha
ARG MAINTANER_EMAIL=fooinha@gmail.com

# Build arguments
ARG SURICATA_FEATURE=redis-async
ARG SURICATA_DEBIAN_SID_VERSION=3.1.2-2
ARG SURICATA_DEBIAN_EXPERIMENTAL_VERSION=3.2.0-1+beta1~${SURICATA_FEATURE}
ARG SURICATA_GIT_REPO=https://github.com/fooinha/suricata.git
ARG SURICATA_GIT_BRANCH=dev-eve-output-redis-async-v4
ARG SURICATA_DEBIAN_CHANGELOG_ENTRY="Experimental version of suricata 3.2.0beta with async redis"
ARG EXTRA_DEV_PACKAGES="libevent-dev"

# Update
RUN DEBIAN_FRONTEND=noninteractive apt-get update

# Install build dependencies
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y --fix-missing \
    ${EXTRA_DEV_PACKAGES}

WORKDIR /root

# Clone source from git repository
RUN git clone -v -b ${SURICATA_GIT_BRANCH} --single-branch ${SURICATA_GIT_REPO}
RUN cd suricata ; git checkout ${SURICATA_GIT_BRANCH}
RUN mv suricata suricata-${SURICATA_DEBIAN_EXPERIMENTAL_VERSION}
RUN tar cf suricata-${SURICATA_DEBIAN_EXPERIMENTAL_VERSION}.tar suricata-${SURICATA_DEBIAN_EXPERIMENTAL_VERSION}/
RUN gzip suricata-${SURICATA_DEBIAN_EXPERIMENTAL_VERSION}.tar

# Get debian package source
RUN DEBIAN_FRONTEND=noninteractive apt-get source suricata=$SURICATA_DEBIAN_SID_VERSION
RUN xz -d suricata_${SURICATA_DEBIAN_SID_VERSION}.debian.tar.xz ; tar xvf suricata_${SURICATA_DEBIAN_SID_VERSION}.debian.tar

# Copy debian directory to build dir
RUN mv debian suricata-${SURICATA_DEBIAN_EXPERIMENTAL_VERSION}/

WORKDIR /root/suricata-${SURICATA_DEBIAN_EXPERIMENTAL_VERSION}/

# Get libhtp from git
RUN git clone -v https://github.com/OISF/libhtp

# Changelog
RUN DEBFULLNAME=${MAINTANER_NAME} DEBEMAIL=${MAINTANER_EMAIL} dch  -v ${SURICATA_DEBIAN_EXPERIMENTAL_VERSION} -D unstable "${SURICATA_DEBIAN_CHANGELOG_ENTRY}"

# Build package
RUN ./debian/rules binary

# Get package information
RUN dpkg -I ../suricata_${SURICATA_DEBIAN_EXPERIMENTAL_VERSION}_amd64.deb

CMD ["/bin/bash"]
