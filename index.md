---
title: Home
layout: home
nav_order: 0
---

# About HYMET
HYMET (Hybrid Metagenomic Tool) is a pipeline designed for taxonomic identification and analysis of metagenomic sequences. It combines k-mer screening with smart alignment system that dynamically switches between high-precision and efficient tools depending on the genomic characteristics of the sample, followed by taxonomic assignment using exact matches and weighted lowest common ancestor strategies. 

HYMET version 1.0.0 was released under MIT on June xrd, 2025 and can be downloaded [here](https://github.com/inesbmartins02/HYMET2/releases).

---
### **Workflow overview**

<figure style="text-align: center; margin: 2rem 0;">
  <img src="{{ '/assets/images/hymet.png' | relative_url }}" 
       alt="Diagrama completo do pipeline HYMET"
       style="max-width: 100%; height: auto; width: 600px;">
  <figcaption style="font-style: italic; margin-top: 0.5rem; color: #555;">
  </figcaption>
</figure>
---
```mermaid
graph LR
    %% Optional Preprocessing
    A[Raw FASTQ] --> B{QC?}
    B -->|Yes| C[Trimmomatic]
    B -->|No| D{Preprocessing<br>Required?}
    C --> D
    D -->|Yes| E[Host Removal]
    D -->|No| F{Assembly?}
    E --> F
    F -->|Yes| G[SPAdes]
    F -->|No| H[Convert to FASTA]
    G --> H
    
    %% Core HYMET Pipeline
    H --> I[k-mer Screening<br>(Mash Screen)]
    I --> J{Dynamic Reference<br>Database Construction}
    J --> K{Genome Size<br>Analysis}
    K -->|Large Genomes| L[Mashmap2]
    K -->|Small Genomes| M[Minimap2]
    L --> N[Taxonomic Assignment]
    M --> N
    N --> O[Weighted LCA]
    O --> P[Confidence Scoring]
    P --> Q[(Final Report)]
    
    %% Style Definitions
    style A stroke:#3498db
    style B stroke:#f39c12
    style D stroke:#f39c12
    style I stroke:#e74c3c,stroke-width:2px
    style J stroke:#2ecc71,stroke-width:2px
    style O stroke:#9b59b6,stroke-width:2px
    
    classDef optional fill:#f8f9fa,stroke:#bdc3c7,stroke-dasharray:5
    class B,D,F optional
´´´

[Get started with installation →](https://inesbmartins02.github.io/hymet-docs/installation.html)