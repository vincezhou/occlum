SGX_MODE ?= HW
BUILD_DIR := build

.PHONY: all format format-check clean

all:
	@mkdir -p ../$(BUILD_DIR)/bin/
	@ln -s -f ../../tools/occlum_build.mk ../$(BUILD_DIR)/bin/occlum_build.mk
	@ln -s -f ../../tools/occlum ../$(BUILD_DIR)/bin/occlum
	@ln -s -f ../../tools/occlum-gen-default-occlum-json ../$(BUILD_DIR)/bin/occlum-gen-default-occlum-json
	@$(MAKE) --no-print-directory -C protect-integrity
	@$(MAKE) --no-print-directory -C gen_enclave_conf

format:
	@$(MAKE) --no-print-directory -C protect-integrity format

format-check:
	@$(MAKE) --no-print-directory -C protect-integrity format-check

clean:
	@$(MAKE) --no-print-directory -C protect-integrity clean
	@$(MAKE) --no-print-directory -C gen_enclave_conf clean
