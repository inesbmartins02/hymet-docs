---
title: Traditional Direct Analysis
layout: home
nav_order: 8
parent: Running HYMET
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
```

Where:

* `$num_sequences`: The total number of input sequences in the directory.
* `3.25`: The default multiplier for candidate selection.
* A minimum of 5 candidates is enforced, even for small datasets.

### Adjusting the Threshold

You can adjust the threshold based on the type and size of your input data:

* **Large genomes (e.g., vertebrates) or limited resources**:
  Use a lower multiplier like `1.25–2.25` to reduce load.

* **Small genomes (e.g., prokaryotes) or high accuracy desired**:
  Use a higher multiplier like `4.25–5.25` for better precision.

* **Very large datasets (>1000 query sequences)**:
  Use a multiplier of `1.25–2.0` to maintain performance.

By tuning the threshold appropriately, you can optimize both computational efficiency and classification accuracy.


