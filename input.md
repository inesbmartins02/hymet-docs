---
title: HYMET input data
layout: home
nav_order: 3
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
Each file (`sample1.fna`, `sample2.fna`, etc.) should follow the FASTA format described above.
