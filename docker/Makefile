#!/usr/bin/make -f

SNAPOS_VERSION=raspi0w
BR_VERSION=2018.08.2
BR_TARGET=snapos_rpi0w_defconfig

BR2_EXTERNAL=/build/snapos/buildroot-external
BR2_DL_DIR=/build/download
BR2_CCACHE_DIR=/build/cache
O=/build/output


BR_NAME=buildroot-${BR_VERSION}

export BR2_EXTERNAL
export BR2_DL_DIR
export BR2_CCACHE_DIR
export O

all: conf build

build: conf
	$(MAKE) -C buildroot

menuconf: conf
	$(MAKE) -C buildroot menuconfig

conf: snapos/buildroot-external
	$(MAKE) -C buildroot ${BR_TARGET}

snapos/buildroot-external: buildroot/Makefile
	-git clone --depth 1 --branch ${SNAPOS_VERSION}  https://github.com/thaussma/snapos snapos
	cd snapos && git pull

buildroot/Makefile:
	wget -qO- http://buildroot.org/downloads/${BR_NAME}.tar.gz | tar xz
	mkdir -p buildroot
	mv ${BR_NAME}/* buildroot/
	rm -rf ${BR_NAME}