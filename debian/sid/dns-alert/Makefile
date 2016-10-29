REPO := fooinha

NAME := suricata-experimental

TAG := debian-sid-dns-alert-package

all: build

build:
	docker build --rm -t ${REPO}/${NAME}:${TAG} .
