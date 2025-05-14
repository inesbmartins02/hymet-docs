---
title: Pipeline input
layout: home
nav_order: 5
parent: HYMET input data
---

# Pipeline-Specific Input Requirements  

## Supported Formats  
HYMET's preprocessing pipeline accepts:  
- **Raw reads**: `.fastq` or `.fastq.gz` (Single-End or Paired-End)  
- **Pre-trimmed data**: `.fna`/`.fasta` (skip QC with `-noqc` flag)  

## FASTQ Requirements  
```bash
# Example Illumina headers (v1.5+)  
@Instrument:RunID:Flowcell:Lane:Tile:X:Y  
ATCGATCGATCG...  
+  
BBFFBFFBFFB...  
```

### Quality Considerations  
| Parameter          | Recommended | Minimum |  
|--------------------|-------------|---------|  
| Read Length        | ≥100bp      | 50bp    |  
| Q-score (Phred)   | ≥30         | ≥20     |  
| Adapter Content   | <5%         | -       |  

## Execution Modes  

### 1. Full Pipeline (FASTQ → Results)  
```bash  
./pipeline/run_pipeline.sh -i raw_data.fastq -all  
```  
*Processes:*  
1. QC → 2. Host Removal → 3. Assembly → 4. HYMET Analysis  

### 2. Partial Processing  
```bash  
# Only QC + Host removal  
./pipeline/run_pipeline.sh -i input.fastq -qc -hostremoval  

# Start from intermediate files  
./pipeline/run_pipeline.sh -i cleaned.fna -assembly  
```  

## File Structure Examples  

### Paired-End Input  
```  
/path/to/input/  
├── sample1_R1.fastq.gz  
├── sample1_R2.fastq.gz  
└── sample2_R1.fastq.gz  
```  

### Single-End with Metadata  
```  
/path/to/input/  
├── clinical_1.fq.gz    # Auto-detected  
├── clinical_2.fq.gz  
└── metadata.txt        # Optional  
```  

## Conversion Tools  

### FASTQ → FASTA (if needed)  
```bash  
seqtk seq -A input.fastq > output.fna  
```  

### Compress/Decompress  
```bash  
gzip -d file.fastq.gz    # Decompress  
pigz -9 file.fastq      # Parallel compression  
```  
---

[**Run full pipeline: QC or/and Host Removal or/and Assembly**  
*(Recommended for host-contaminated samples)*  
→ Pipeline Requirements](https://inesbmartins02.github.io/hymet-docs/integratedpipeline.html){: .btn .btn-green }

[Back to Basic Input](https://inesbmartins02.github.io/hymet-docs/basicinput.html)
