include ../sgxenv.mk

EXEC_PROTO := occlum_exec.proto
SRC_FILES := $(shell find . -type f -name '*.rs') Cargo.toml $(EXEC_PROTO)
RUST_TARGET_DIR := $(OBJ_DIR)/exec/cargo-target
RUST_OUT_DIR := $(BUILD_DIR)/bin
EXEC_TARGET := $(RUST_OUT_DIR)/*occlum_exec*

.PHONY: all clean

all: $(SRC_FILES)
ifeq ($(OCCLUM_RELEASE_BUILD), 1)
	@RUSTC_BOOTSTRAP=1 cargo build --release --target-dir=$(RUST_TARGET_DIR) -Z unstable-options --out-dir=$(RUST_OUT_DIR)
	@echo "CARGO (release) => exec"
else
	@RUSTC_BOOTSTRAP=1 cargo build --target-dir=$(RUST_TARGET_DIR) -Z unstable-options --out-dir=$(RUST_OUT_DIR)
	@echo "CARGO (debug) => exec"
endif

clean:
	@cargo clean --target-dir=$(RUST_TARGET_DIR)
	@-$(RM) -f $(EXEC_TARGET)
