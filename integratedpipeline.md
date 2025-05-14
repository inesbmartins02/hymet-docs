---
title: Complete Pipeline Execution 
layout: home
nav_order: 9
parent: Running HYMET
---

# Complete HYMET Pipeline  

The integrated pipeline mode processes raw metagenomic data through three optimized stages before taxonomic analysis:  

## Workflow Overview  
1. **Quality Control**  
   - Adaptive trimming (Trimmomatic)  
   - Quality filtering (Q≥20, min length 50bp)  
   - Automatic adapter detection  

2. **Host DNA Removal**  
   - Bowtie2 alignment against user-selectable host genomes  
   - Generates contamination statistics report  

3. **Metagenomic Assembly**  
   - SPAdes-based assembly with optimized parameters for metagenomes  
   - Automatic quality-based contig filtering  

4. **Core HYMET Analysis**  
   - Executes automatically on processed data  
   - Same hybrid engine as traditional mode  

## Execution Instructions  

### 1. Basic Pipeline Run  
```bash  
./pipeline/run_pipeline.sh -i /path/to/raw_data.fastq -all  
```  

### 2. Customized Execution  
Select specific modules using flags:  
```bash  
./pipeline/run_pipeline.sh -i input.fastq -qc -hostremoval  
```  
*(Skips assembly, proceeds directly to analysis with cleaned reads)*  

[Back to Traditional Mode](https://inesbmartins02.github.io/hymet-docs/hymetsimple.html)