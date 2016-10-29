REPO := fooinha

NAME := suricata-experimental

TAG := debian-sid-kafka-package

all: build

build:
	docker build --rm -t ${REPO}/${NAME}:${TAG} .
