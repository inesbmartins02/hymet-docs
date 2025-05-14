---
title: Use our test dataset
layout: home
nav_order: 6
parent: HYMET input data
---

# Test Dataset  

## Overview  
This package includes pre-configured scripts and datasets for quick validation of HYMET. The test dataset allows users to:  
1. Download reference genomes from NCBI  
2. Process them into analysis-ready formats  
3. Optionally modify data for testing purposes  

## Quick Start  

```bash
# Navigate to test dataset directory
cd testdataset
```

## Step-by-Step Guide  

### 1. Download Assembly Files  
Download summary files for each taxonomic domain:  

```bash
# Archaea
wget "https://ftp.ncbi.nlm.nih.gov/genomes/refseq/archaea/assembly_summary.txt"
# Bacteria
wget "https://ftp.ncbi.nlm.nih.gov/genomes/refseq/bacteria/assembly_summary.txt"
# Fungi
wget "https://ftp.ncbi.nlm.nih.gov/genomes/refseq/fungi/assembly_summary.txt"
# Invertebrate
wget "https://ftp.ncbi.nlm.nih.gov/genomes/refseq/invertebrate/assembly_summary.txt" 
# Plant
wget "https://ftp.ncbi.nlm.nih.gov/genomes/refseq/plant/assembly_summary.txt" 
# Protozoa
wget "https://ftp.ncbi.nlm.nih.gov/genomes/refseq/protozoa/assembly_summary.txt" 
# Vertebrate Mammalian
wget "https://ftp.ncbi.nlm.nih.gov/genomes/refseq/vertebrate_mammalian/assembly_summary.txt" 
# Vertebrate Other
wget "https://ftp.ncbi.nlm.nih.gov/genomes/refseq/vertebrate_other/assembly_summary.txt" 
# Viral
wget "https://ftp.ncbi.nlm.nih.gov/genomes/refseq/viral/assembly_summary.txt" 
```

### 2. Create Reference Database  
```bash
python3 createDatabase.py
```
**Prompts:**  
- Path to assembly summaries directory  
- Destination directory for sequences  
- Taxonomic domain to process (e.g., "bacteria")  

### 3. Filter Genomes (10% Subset)  
```bash
python3 filterGCF.py
```
**Prompts:**  
- Input directory containing GCF files  
- Output directory for filtered sequences  

### Optional Processing Steps  

#### Extract Taxonomy Information  
```bash
python3 extractTaxonomy.py
```
**Requires:**  
- NCBI-registered email  
- Path to domain-specific .fna files  
- Assembly summary file  

#### Map Sequence IDs to Genomes  
```bash
python3 extractNC.py
```
**Output:** CSV mapping GCF accessions to sequence IDs (NC_, NZ_, etc.)  

#### Simulate Genetic Variation  
```bash
python3 mutationGCF.py
```
**Parameters:**  
- Input/output paths  
- Mutation rate (0-1, e.g., 0.2 for 20% mutation)  

---  
*Note: Process taxonomic groups separately to avoid system overload *