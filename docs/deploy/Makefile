.PHONY: clean verify init plan publish check check-fmt check-types

BUILDDIR ?= ../../build
export TF_VAR_det_version := $(shell cat ../../VERSION)
export TF_VAR_build_dir := $(BUILDDIR)

clean:
	-rm -r .terraform
	-rm state/terraform.tfstate.backup

verify:
	terraform --version

init:
	terraform init

plan: init
	terraform plan

publish: init
	terraform apply -auto-approve

check: check-fmt check-types

check-fmt:
	terraform fmt -check=true -diff=true

check-types: init
	terraform validate -check-variables=false
