
SAMPLE_DIR          := ../../samples
SCHEMA_DIR          := ../../schemas

SAMPLE_SUB_DIRS     := $(wildcard $(SAMPLE_DIR)/*/)

SAMPLES_XML         := $(wildcard $(addsuffix *.xml,$(SAMPLE_SUB_DIRS)))
SAMPLES_XSD         := $(wildcard $(addsuffix *.xsd,$(SAMPLE_SUB_DIRS)))
SCHEMAS_XSD         := $(wildcard $(SCHEMA_DIR)/*.xsd)

JOINT_SDMX_SCHEMA   := joint-schema-for-xmllint.xsd
XML_SCHEMA_SCHEMA   := XMLSchema.xsd

.PHONY: default samples schemas

default: samples sample_schemas schemas end

samples:
	@echo ------------------------------------------------------------------------
	@echo -- Starting to check file types of sample SDMX-ML instances
	@echo -- Check that character set is us-ascii or utf-8
	@echo ------------------------------------------------------------------------

	@$(foreach file, $(SAMPLES_XML), file -I $(file);)

	@echo ------------------------------------------------------------------------
	@echo -- Starting to validate sample SDMX-ML instances
	@echo -- Check that all instances are valid
	@echo ------------------------------------------------------------------------

	@$(foreach file, $(SAMPLES_XML), xmllint --noout --schema $(JOINT_SDMX_SCHEMA) $(file);)

sample_schemas:
	@echo ------------------------------------------------------------------------
	@echo -- Starting to check file types of sample SDMX-ML schemas
	@echo -- Check that character set is us-ascii
	@echo ------------------------------------------------------------------------

	@$(foreach file, $(SAMPLES_XSD), file -I $(file);)

	@echo ------------------------------------------------------------------------
	@echo -- Starting to validate sample SDMX-ML schemas
	@echo -- Check that all schemas are valid
	@echo ------------------------------------------------------------------------

	@$(foreach file, $(SAMPLES_XSD), xmllint --noout --schema $(XML_SCHEMA_SCHEMA) $(file);)

schemas:
	@echo ------------------------------------------------------------------------
	@echo -- Starting to check file types of general SDMX-ML schemas
	@echo -- Check that character set is us-ascii
	@echo ------------------------------------------------------------------------

	@$(foreach file, $(SCHEMAS_XSD), file -I $(file);)

	@echo ------------------------------------------------------------------------
	@echo -- Starting to validate general SDMX-ML schemas
	@echo -- Check that all schemas are valid
	@echo ------------------------------------------------------------------------

	@$(foreach file, $(SCHEMAS_XSD), xmllint --noout --schema $(XML_SCHEMA_SCHEMA) $(file);)

end:
	@echo ------------------------------------------------------------------------
	@echo -- Finished
	@echo ------------------------------------------------------------------------

