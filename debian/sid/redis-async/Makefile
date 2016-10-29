REPO := fooinha

NAME := suricata-experimental

TAG := debian-sid-redis-async-package

all: build

build:
	docker build --rm -t ${REPO}/${NAME}:${TAG} .
