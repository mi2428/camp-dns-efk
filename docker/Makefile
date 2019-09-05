BUILDKIT_BUILD = DOCKER_BUILDKIT=1 docker build
IMAGE_TAG      = latest
REGISTRY       = 203.178.158.5:30500

build:
	$(BUILDKIT_BUILD) unbound -t $(REGISTRY)/wide-camp-1909/camp-dns-unbound:$(IMAGE_TAG)
	$(BUILDKIT_BUILD) fluentd -t $(REGISTRY)/wide-camp-1909/camp-dns-fluentd:$(IMAGE_TAG)
