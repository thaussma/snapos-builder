#!/usr/bin/make -f

SNAPOS_VERSION=raspi0w
BR_VERSION=2018.08.2
BR_TARGET=snapos_rpi0w_defconfig

BR2_EXTERNAL=/build/snapos/buildroot-external
BR2_DL_DIR=/build/download
BR2_CCACHE_DIR=/build/cache
BR2_OUPUT=/build/output
BR2_FOLDER=/build/buildroot


BR_NAME=buildroot-${BR_VERSION}

export BR2_EXTERNAL
export BR2_DL_DIR
export BR2_CCACHE_DIR
export O

all: conf build

build: conf
	$(MAKE) O=${BR2_OUPUT} -C ${BR2_FOLDER}

menuconf: conf
	$(MAKE) O=${BR2_OUPUT} -C ${BR2_FOLDER} menuconfig

conf: /build/snapos/buildroot-external
	$(MAKE) O=${BR2_OUPUT} -C ${BR2_FOLDER} ${BR_TARGET}

/build/snapos/buildroot-external: ${BR2_FOLDER}/Makefile
	-git clone --depth 1 --branch ${SNAPOS_VERSION}  https://github.com/thaussma/snapos snapos
	cd snapos && git pull

${BR2_FOLDER}/Makefile:
	wget -qO- http://buildroot.org/downloads/${BR_NAME}.tar.gz | tar xz
	mkdir -p buildroot
	mv ${BR_NAME}/* ${BR2_FOLDER}
	rm -rf ${BR_NAME}