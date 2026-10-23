PLANTUML ?= plantuml
SOURCES := $(wildcard source/*.puml)
OUTPUT_DIR := $(CURDIR)/exports

.PHONY: export
export:
	@mkdir -p $(OUTPUT_DIR)
	@set -e; for src in $(SOURCES); do $(PLANTUML) -tpng -o $(OUTPUT_DIR) "$$src" && $(PLANTUML) -tsvg -o $(OUTPUT_DIR) "$$src"; done
