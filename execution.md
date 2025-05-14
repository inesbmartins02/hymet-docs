---
title: Running HYMET
layout: home
nav_order: 4
---

# Running HYMET

After completing the initial setup and configuration, you can run the HYMET tool using the main script. Follow these steps:

1. **Execute the main script**:

    ```bash
    ./main.pl
    ```

2. **When prompted, enter the path to the input directory containing your `.fna` files**:

    ```bash
    Please enter the path to the input directory (containing .fna files): 
    ```

3. **Type or paste the full path to your input directory and press Enter**.

The tool will then process the input files and perform the taxonomic identification based on the configured databases and taxonomy files.

> **Note**: Ensure that your input directory contains properly formatted `.fna` files before running the tool.

---

## Mash Threshold and Candidate Selection

The `mash` tool is used in the pipeline to screen input sequences and select candidate genomes for further analysis. The threshold parameter plays a crucial role in balancing the number of candidates selected and the computational load of subsequent steps.

### Default Threshold and Candidate Calculation

In this pipeline, the default threshold is set to `3.25`, meaning that for each input sequence, approximately 3.25 candidate genomes are selected. This ensures a balance between sensitivity and computational efficiency. The number of candidates is calculated as:

```bash
min_candidates=$(echo "$num_sequences * 3.25" | bc | awk '{printf("%d\n",$1 + 0.5)}')
min_candidates=$(( min_candidates < 5 ? 5 : min_candidates ))