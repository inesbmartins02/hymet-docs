---
title: Use our test dataset
layout: home
nav_order: 6
parent: HYMET input data
---


# Test Dataset
- This folder includes scripts to install and prepare all necessary data to replicate the work using our dataset.
  - **Prerequisites**:
    - Before running the scripts in this folder, users need to download the assembly files (`assembly_files.txt`) for each domain from the NCBI FTP site.
  - **Scripts**:
    - **`create_database.py`**: Downloads 10% of the content from each downloaded assembly file and organizes the datasets by domain.
    - **`extractNC.py`**: Maps the content of each Genome Collection File (GCF) with its respective sequence identifiers. It generates a CSV file containing       this mapping, with one column for the GCF and another column for the sequence identifiers (such as NC, NZ, etc.) present in each GCF.
    - **`extractTaxonomy.py`**: Creates a CSV file containing the GCF and its respective taxonomy, among other information.
    - Additional scripts modify the data format and organization, including:
      - Implementing mutations
      - Converting formats (e.g., FASTA to FASTQ)
      - Formatting into paired-end reads
    - **`GCFtocombinedfasta.py`**: Combines all GCFs from each domain into a single FASTA file, separating sequences by identifier. This script is used as input for most of the tools.
