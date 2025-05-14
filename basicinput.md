---
title: Basic input
layout: home
nav_order: 4
parent: HYMET input data
---

# Input Requirements

### Input File Format
The tool expects input files in **FASTA format** (`.fna` or `.fasta`). Each file should contain metagenomic sequences with headers in the following format:
```
>sequence_id additional_info
SEQUENCE_DATA
```
- **sequence_id**: A unique identifier for the sequence.
- **additional_info**: Optional metadata (e.g., source organism, length).
- **SEQUENCE_DATA**: The nucleotide sequence.

### Input Directory
Place your input files in the directory specified by the `$input_dir` variable in the `main.pl` script. 

For example, if your input directory contains the following files:
```
input_dir/
├── sample1.fna
├── sample2.fna
└── sample3.fna
```
Each file should follow the FASTA format described above.

The pipeline automatically processes all valid input files through its taxonomic classification workflow, generating structured results in the output directory. Input files must follow standard \ac{FASTA} format requirements, where each sequence is preceded by a header line beginning with '>' followed by a unique identifier (e.g., >1, >sequence\_001, >contig\_1, >read\_1 etc.). These identifiers are preserved throughout the analysis and serve as the primary keys for matching sequences to their final taxonomic classifications in the output files. For optimal taxonomic resolution, \ac{HYMET} requires inputs partitioned into multiple sequence files (minimum 10 recommended). This design fundamentally enhances the pipeline's candidate selection mechanism, where reference genome retrieval scales proportionally with the number of query sequences. Since metagenomes inherently contain mixed genomic material from diverse organisms, splitting a composite sample into discrete segments presents no biological limitations while conferring significant computational advantages.

