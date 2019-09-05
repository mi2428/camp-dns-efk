BUILDKIT_BUILD = DOCKER_BUILDKIT=1 docker build
IMAGE_TAG      = latest

build:
	$(BUILDKIT_BUILD) unbound -t wide-camp-1909/camp-dns-unbound:$(IMAGE_TAG)
	$(BUILDKIT_BUILD) fluentd -t wide-camp-1909/camp-dns-fluentd:$(IMAGE_TAG)
