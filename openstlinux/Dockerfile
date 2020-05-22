FROM ubuntu:bionic

# This is a recomended list from the official ST wiki.
# See: https://wiki.st.com/stm32mpu/wiki/PC_prerequisites
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    sed wget curl cvs subversion git-core coreutils unzip texi2html texinfo \
    docbook-utils gawk python-pysqlite2 diffstat help2man make gcc build-essential \
    g++ desktop-file-utils chrpath libxml2-utils xmlto docbook bsdmainutils \
    iputils-ping cpio python-wand python-pycryptopp python-crypto libsdl1.2-dev \
    xterm corkscrew nfs-common nfs-kernel-server device-tree-compiler mercurial \
    u-boot-tools libarchive-zip-perl ncurses-dev bc linux-headers-generic \
    gcc-multilib libncurses5-dev libncursesw5-dev lrzsz dos2unix lib32ncurses5 \
    repo libssl-dev \
# Some more tools not in prerequisites
    gdisk vim tree screen\ 
 && rm -rf /var/lib/apt/lists/*

# Set the locale
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y locales \
 && rm -rf /var/lib/apt/lists/* \
 && locale-gen "en_US.UTF-8"
ENV LANG=en_US.UTF-8 \
    LANGUAGE=en_US:en \
    LC_ALL=en_US.UTF-8

# Color terminal
ENV TERM=xterm-256color

COPY README.md /app/

# Build must run in normal user.
RUN useradd -m -s /bin/bash build
RUN mkdir -p /sstate /build
WORKDIR /build

USER build
# Print guide
CMD cat /app/README.md | tail -10
