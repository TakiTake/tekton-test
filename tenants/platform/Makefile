TEKTON_PIPELINE_VERSION = v0.4.0
TENANT_NAME = default

.PHONY: install-tekton
install-tekton:
	kubectl apply -f https://github.com/tektoncd/pipeline/releases/download/$(TEKTON_PIPELINE_VERSION)/release.yaml

.PHONY: delete-tekton
delete-tekton:
	kubectl delete -f https://github.com/tektoncd/pipeline/releases/download/$(TEKTON_PIPELINE_VERSION)/release.yaml

.PHONY: create-common-pipeliens
create-common-pipelines:
	find common -name '*.task.yaml' -exec kubectl apply -f {} \;
	find common -name '*.pipeline.yaml' -exec kubectl apply -f {} \;

.PHONY: create-tenant
create-tenant:
	mkfile_path := $(abspath $(lastword $(MAKEFILE_LIST)))
	current_dir := $(notdir $(patsubst %/,%,$(dir $(mkfile_path))))
	mkdir -p $(current_dir)/../tenants/$(TENANT_NAME)
	kubectl create namespace $(TENANT_NAME)
