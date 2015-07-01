Build tools for the SDMX-ML v2.0 release package
================================================

This folder contains tools for maintaining the SDMX-ML v2.0 release package.
Main tool is a makefile with some supporting files. Run the makefile with the
standard make command:

    make

Makefile checks and validates all sample XML instance files and sample XML
schema files. It also validates SDMX-ML schema files for general use. Please
inspect the output carefully before committing any changes.

Supporting files are:

- `joint-schema-for-xmllint.xsd` is a XML schema file that imports SDMX-ML schemas
(both sample and generated). Makefile uses the standard `xmllint` command for
validation and xmllint accepts only a single schema file as an argument (see
makefile for details).

- `XMLSchema.xsd` is the standard XML Schema schema. It is used for validating
other XML Schema files in the package.

- `xml.xsd` is the standard base XML schema.

