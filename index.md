---
title: Home
layout: home
nav_order: 0
---

# About HYMET
HYMET (Hybrid Metagenomic Tool) is a pipeline designed for taxonomic identification and analysis of metagenomic sequences. It combines k-mer screening with smart alignment system that dynamically switches between high-precision and efficient tools depending on the genomic characteristics of the sample, followed by taxonomic assignment using exact matches and weighted lowest common ancestor strategies. 

HYMET version 1.0.0 was released under MIT on June xrd, 2025 and can be downloaded [here](https://github.com/inesbmartins02/HYMET2/releases).

---
### **Workflow**

<figure style="text-align: center; margin: 2rem 0;">
  <img src="{{ '/assets/images/hymet.png' | relative_url }}" 
       alt="Diagrama completo do pipeline HYMET"
       style="max-width: 100%; height: auto; width: 600px;">
  <figcaption style="font-style: italic; margin-top: 0.5rem; color: #555;">
    Figura 1: Fluxo de análise metagenômica desde o input até resultados taxonômicos
  </figcaption>
</figure>
---
### **Execution Modes**

HYMET offers two complementary approaches to metagenomic analysis:

**1. Traditional Direct Analysis**  
*For pre-processed data or rapid profiling*  
- Bypasses QC, host removal, and assembly stages  
- Executes HYMET's core hybrid engine directly on input files  
- Ideal when:  
  • Working with already cleaned datasets  
  • Prioritizing speed over comprehensive processing  
  • Using external preprocessing pipelines  

**2. Integrated Pipeline Mode**  
*For complete end-to-end analysis*  
- Modular workflow with three preprocessing stages:  
  1. **Smart Quality Control** - Adaptive trimming and artifact removal  
  2. **Host DNA Depletion** - Customizable reference-based filtering  
  3. **Metagenomic Assembly** - Configurable community reconstruction  
- Seamlessly feeds preprocessed data into HYMET's core analyzer  
- Recommended when:  
  • Processing raw sequencing data 
  • Working with host-contaminated samples  
  • Requiring assembled contigs for downstream analysis  

**Key Advantages**  
- Shared analysis core ensures consistent results across modes  
- All preprocessing steps optimized for metagenomic data characteristics  
- Intermediate quality reports generated at each pipeline stage
  


[Get started with installation →](https://inesbmartins02.github.io/hymet-docs/installation.html)