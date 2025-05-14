---
title: Running HYMET
layout: home
nav_order: 7
has_children: true
---

## **Execution Modes**

HYMET offers two complementary approaches to metagenomic analysis:

[**1. Traditional Direct Analysis**](https://inesbmartins02.github.io/hymet-docs/hymetsimple.html) 

*For pre-processed data or rapid profiling*  
- Bypasses QC, host removal, and assembly stages  
- Executes HYMET's core hybrid engine directly on input files  
- Ideal when:  
  • Working with already cleaned datasets  
  • Prioritizing speed over comprehensive processing  
  • Using external preprocessing pipelines  

[**2. Integrated Pipeline Mode**](https://inesbmartins02.github.io/hymet-docs/integratedpipeline.md)
  
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
  
