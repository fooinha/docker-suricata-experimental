REPO := fooinha

NAME := suricata-experimental

TAG := debian-sid-yara-package

all: build

build:
	docker build --rm -t ${REPO}/${NAME}:${TAG} .
