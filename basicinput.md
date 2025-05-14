---
title: Basic input
layout: home
nav_order: 4
parent: HYMET input data
---
# Input Requirements  

## File Format  
**HYMET** requires input files in **FASTA format** (`.fna` or `.fasta`). Each file must adhere to the following structure:  

```
>sequence_id [additional_info]  
SEQUENCE_DATA  
```  

- **`sequence_id`**: A unique identifier (e.g., `>1`, `>contig_001`, `>read_42`).  
- **`additional_info`**: Optional metadata (e.g., sample origin, length).  
- **`SEQUENCE_DATA`**: Raw nucleotide sequence (case-insensitive).  

## How to Provide Input Files  
When you execute `main.pl`, the script will prompt you to enter the **input directory path** containing your FASTA files.  

Example:  
1. Run the pipeline:  
   ```bash
   perl main.pl
   ```  
2. When prompted, provide the full path to your input directory:  
   ```
    Please enter the path to the input directory (containing .fna files):  /path/to/your/input_files/
   ```  

## Key Recommendations  
1. **Multiple Files Preferred**: For optimal performance, the input should consist of multiple read files or contigs. This allows for more efficient screening in the initial stage of the pipeline, as it evaluates candidates for each read separately. Thus, split large metagenomes into **≥10 smaller files**. This improves:  
   - Taxonomic resolution via enhanced reference genome retrieval.  
   - Computational efficiency in candidate selection.  

2. **Header Preservation**: Sequence IDs are used to track classifications—avoid duplicates or special characters.  

3. **No Biological Constraints**: Metagenomic fragmentation has no impact on results, as HYMET processes mixed genomic material natively.  

The pipeline automatically processes all valid FASTA files, generating structured outputs with preserved identifiers.  

---  
*Note: For troubleshooting, ensure headers start with `>` and sequences contain only standard nucleotides (A/T/C/G/N).*

## Preparing Input Files  

### 1. Splitting Large FASTA Files  
For optimal performance, split large files into **≥10 smaller chunks** using Linux commands:  

```bash
split -n l/10 sample1.fna read_
```  
This creates 10 files named:  
- `read_aa`  
- `read_ab`  
- `read_ac`  
...etc.  

### 2. Adding FASTA Headers  
The split files need proper headers. Use this script:  

```bash
#!/bin/bash
for file in read_*; do
    suffix=${file#read_}
    sed -i "1i >read_$suffix" "$file"  # Adds header
    mv "$file" "${file}.fna"           # Adds .fna extension
done
```

**To execute:**  
1. Save as `add_headers.sh`  
2. Make executable:  
   ```bash
   chmod +x add_headers.sh
   ```  
3. Run in the directory containing split files:  
   ```bash
   ./add_headers.sh
   ```  

**Result:**  
Properly formatted FASTA files (`read_aa.fna`, `read_ab.fna`, etc.) ready for analysis.  

## Next Step: Choose Your Analysis Path

[**I just want to classify my reads/contigs**  
→ Proceed to Traditional Direct Analysis](https://inesbmartins02.github.io/hymet-docs/hymetsimple.html){: .btn .btn-purple .mr-2 }

[**I want to apply host removal and/or assembly**  
→ Proceed to Pipeline Requirements](https://inesbmartins02.github.io/hymet-docs/integratedpipeline.html){: .btn .btn-green }