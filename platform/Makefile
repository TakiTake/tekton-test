TEKTON_PIPELINE_VERSION = v0.3.1
TENANT_NAME = default

.PHONY: install
install:
	kubectl apply -f https://github.com/tektoncd/pipeline/releases/download/$(TEKTON_PIPELINE_VERSION)/release.yaml

.PHONY: create-tenant
create-tenant:
	mkdir ../tenants/$(TENANT_NAME)
	kubectl create namespace $(TENANT_NAME)
