---
title: Home
layout: home
nav_order: 0
---
<figure style="text-align: center; margin: 2rem 0;">
  <img src="{{ '/assets/images/logo.png' | relative_url }}" 
       alt="logo"
       style="max-width: 100%; height: auto; width: 600px;">
  <figcaption style="font-style: italic; margin-top: 0.5rem; color: #555;">
  </figcaption>
</figure>
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

[Get started with installation →](https://inesbmartins02.github.io/hymet-docs/installation.html)