---
title: Complete Pipeline Execution 
layout: home
nav_order: 9
parent: Running HYMET
---

# HYMET Pipeline Technical Documentation

## 1. Main Pipeline Controller (`run_pipeline.sh`)

### Core Functionality
- Orchestrates the entire preprocessing workflow
- Provides modular execution via command-line flags
- Handles intermediate file passing between stages

### Execution Flow
<div class="mermaid">
graph TD
    A[Input FASTQ] --> B{QC Step?}
    B -->|Yes| C[Trimmomatic]
    B -->|No| D{Host Removal?}
    C --> D
    D -->|Yes| E[Bowtie2]
    D -->|No| F{Assembly?}
    E --> F
    F -->|Yes| G[SPAdes]
    F -->|No| H[HYMET Analysis]
    G --> H
</div>

### Key Features
- **Dependency Checking**: Verifies all required tools are installed
- **Parameter Validation**: Ensures correct input/output paths
- **Error Handling**: Stops pipeline on any subprocess failure

### Usage Examples
```bash
# Full pipeline
./run_pipeline.sh -i input.fastq -all

# Custom workflow
./run_pipeline.sh -i input.fastq -qc -hostremoval
```

---

## 2. Quality Control Module (`1_trimming/run.sh`)

### Processing Steps
1. **Adapter Handling**:
   - Automatically downloads Illumina TruSeq3 adapters if missing
   - Uses Trimmomatic's ILLUMINACLIP with conservative settings (2:30:10)

2. **Quality Trimming**:
   - Sliding window of 4bp with Q≥20 threshold
   - Discards reads <50bp after trimming

3. **Output**:
   - Generates cleaned FASTQ with naming convention: `[prefix].fastq`

### Technical Parameters
```bash
trimmomatic SE \
  -threads 4 \
  $INPUT \
  $OUTPUT_PREFIX.fastq \
  ILLUMINACLIP:adapters.fa:2:30:10 \
  SLIDINGWINDOW:4:20 \
  MINLEN:50
```

---

## 3. Host DNA Removal Module (`2_host_removal/run.sh`)

### Key Components
- **Bowtie2 Alignment**:
  - Uses uncompressed FASTQ input
  - Ultra-sensitive preset (default parameters)
  - 4 threads for parallel processing

- **Index Requirements**:
  - Pre-built host genome index required
  - Expected files: `human_bowtie2_index.[1-4].bt2`

- **Output**:
  - Host-free reads in `[output].fastq`
  - Automatically discards aligned reads

### Critical Checks
```bash
if [ ! -f "${HOST_INDEX}.1.bt2" ]; then
    echo "Error: Missing Bowtie2 index"
    exit 1
fi
```

---

## 4. Metagenomic Assembly Module (`3_assembly/run.sh`)

### SPAdes Configuration
- **Metagenome Mode**: `--only-assembler` flag
- **Resource Allocation**:
  - 4 CPU threads
  - Automatic memory detection

### Output Structure
```
output/
└── assembly/
    ├── contigs.fasta
    ├── scaffolds.fasta
    └── assembly_graph/
```

### Error Handling
- Creates output directory if missing
- Fails immediately on SPAdes errors

---

## Integration Points

### File Passing Convention
- Each stage expects FASTQ input
- Output naming follows:
  - QC: `clean.fastq`
  - Host removal: `host_removed.fastq`
  - Assembly: `contigs.fasta`

### Environment Requirements
All scripts verify:
1. Conda environment activation
2. Tool availability (via `command -v`)
3. Write permissions in output directory


[Back to Traditional Mode](https://inesbmartins02.github.io/hymet-docs/hymetsimple.html)