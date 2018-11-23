FROM debian:jessie

ENV BR_VERSION 2018.08.2
ENV SNAP_OS_VERSION 0.15.0

RUN apt-get update && apt-get install -y -q \
    bash \
    bc \
    binutils \
    build-essential \
    bzip2 \
    ca-certificates \
    cpio \
    debianutils \
    g++ \
    gcc \
    gzip \
    libncurses5-dev \
    locales \
    make \
    patch \
    perl \
    python \
    rsync \
    sed \
    tar \
    unzip \
    wget \
    ccache \
    git

RUN sed -i "s/^# en_US.UTF-8/en_US.UTF-8/" /etc/locale.gen && locale-gen && update-locale LANG=en_US.UTF-8

WORKDIR /build
COPY Makefile Makefile

CMD ["/usr/bin/make"]