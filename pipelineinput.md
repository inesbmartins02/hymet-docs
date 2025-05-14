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

| Parameter        | Recommended | Minimum |
|------------------|-------------|---------|
| Read Length      | ≥100bp      | 50bp    |
| Q-score (Phred) | ≥30         | ≥20     |
| Adapter Content | <5%         | -       |

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

## Next Step: Choose Your Analysis Path

[**I just want to classify my reads: Convert FASTQ to FASTA**   
→ Proceed to Traditional Direct Analysis](https://inesbmartins02.github.io/hymet-docs/hymetsimple.html){: .btn .btn-purple }

[**Run full pipeline: QC or/and Host Removal or/and Assembly**   
→ Proceed to Pipeline Requirements](https://inesbmartins02.github.io/hymet-docs/integratedpipeline.html){: .btn .btn-green }

