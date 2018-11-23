#!/usr/bin/make -f

SNAPOS_VERSION=raspi0w
BR_VERSION=2018.08.2
BR_TARGET=snapos_rpi0w_defconfig

BR_NAME=buildroot-${BR_VERSION}
SNAPOS_NAME=snapos-${SNAPOS_VERSION}

all: conf build

build: conf
	$(MAKE) -C ${BR_NAME}

menuconf: conf
	$(MAKE) -C ${BR_NAME} menuconfig

conf: ${BR_NAME} ${BR_NAME}/${SNAPOS_NAME}
	$(MAKE) -C ${BR_NAME} BR2_EXTERNAL=${SNAPOS_NAME}/buildroot-external ${BR_TARGET}

${BR_NAME}/${SNAPOS_NAME}/: ${BR_NAME}/
	cd ${BR_NAME} && git clone --depth 1 --branch ${SNAPOS_VERSION}  git@github.com:thaussma/snapos.git ${SNAPOS_NAME}

${BR_NAME}/:
	wget -qO- http://buildroot.org/downloads/${BR_NAME}.tar.gz | tar xz