---
title: HYMET output
layout: home
nav_order: 10
---

# HYMET Output

After running HYMET, the tool generates an output file with taxonomic classifications. The output is formatted as follows:

```
| Query | Lineage | Taxonomic Level | Confidence |
|-------|---------|-----------------|------------|
| seq1  | superkingdom:Bacteria;phylum:Firmicutes;genus:Staphylococcus | genus | 0.9500 |
| seq2  | superkingdom:Bacteria;phylum:Proteobacteria;species:Escherichia coli | species | 0.8700 |
| seq3  | Unknown | root | 0.0000 |
```

Each line in the output represents a classification result:

- **Query**: The identifier of the input sequence (e.g., `seq1`, `seq2`). These correspond to the sequence IDs in your input files (e.g., `NC_...`).
- **Lineage**: The taxonomic lineage assigned to the query sequence.
- **Taxonomic Level**: The most specific taxonomic level confidently assigned.
- **Confidence**: A score between 0 and 1 indicating the confidence of the classification.

### Interpreting the Results

- High confidence scores (close to 1) indicate more reliable classifications.
- `"Unknown"` in the Lineage column and `"root"` as Taxonomic Level indicate that the tool couldn't confidently classify the sequence.
- The **Taxonomic Level** shows the most specific classification the tool could make with confidence.

> **Note:** The Query column (`seq1`, `seq2`, etc.) corresponds to the sequence IDs in your input files (e.g., `NC_...`). You can cross-reference these IDs with your original input to identify which sequences received which classifications.