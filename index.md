---
title: Home
layout: home
nav_order: 0
---

# About HYMET
HYMET (Hybrid Metagenomic Tool) is a comprehensive metagenomic analysis pipeline that performs taxonomic identification through a dual-phase approach. The system first optionally processes raw sequencing data through an automated preprocessing cascade including quality control (Trimmomatic with Illumina adapter removal and sliding-window trimming), host DNA depletion (Bowtie2 alignment against customizable reference genomes), metagenomic assembly (SPAdes with microbial community-optimized parameters), and binning (with MetaBAT2). For the core analysis, HYMET employs a sophisticated hybrid strategy that begins with rapid k-mer screening using Mash Screen to identify candidate reference genomes, followed by dynamic alignment routing - using Mashmap2 for efficient processing of large genomes and Minimap2 for precise alignment of smaller sequences. Taxonomic assignments are then generated through a combination of exact matches and weighted lowest common ancestor algorithms, incorporating confidence scoring to produce finalized, reliability-annotated taxonomic profiles. This integrated workflow supports both direct analysis of preprocessed FASTA files and complete end-to-end processing from raw FASTQ inputs, adapting automatically to the specific characteristics of each metagenomic dataset.

HYMET version 1.0.0 was released under MIT on June xrd, 2025 and can be downloaded [here](https://github.com/inesbmartins02/HYMET2/releases).

---
### **Workflow overview**

<figure style="text-align: center; margin: 2rem 0;">
  <img src="{{ '/assets/images/hymet1.png' | relative_url }}" 
       alt="Diagrama completo do pipeline HYMET"
       style="max-width: 100%; height: auto; width: 600px;">
  <figcaption style="font-style: italic; margin-top: 0.5rem; color: #555;">
  </figcaption>
</figure>
---

[Get started with installation →](https://inesbmartins02.github.io/hymet-docs/installation.html)