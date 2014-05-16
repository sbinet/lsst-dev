## binet/lsst-qserv

.PHONY: all build

REPO := binet/lsst-qserv
TAG := 6.0.0

all: build
	@echo "done"

build: Dockerfile
	docker build --rm --tag=$(REPO):$(TAG) .
	docker tag --force $(REPO):$(TAG) $(REPO):latest

upload: build
	docker push $(REPO):$(TAG)
