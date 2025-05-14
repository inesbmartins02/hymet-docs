---
title: HYMET input data
layout: home
nav_order: 3
has_children: true
---

# Data Requirements for HYMET Analysis  

HYMET accepts multiple input types across different processing modes, each optimized for specific research scenarios. This section guides you through:  

1. **[Basic Input](https://inesbmartins02.github.io/hymet-docs/basicinput.html)**: Standard FASTA requirements for direct analysis  
2. **[Pipeline Input](https://inesbmartins02.github.io/hymet-docs/pipelineinput.html)**: Raw FASTQ specifications for complete preprocessing  
3. **[Test Dataset](https://inesbmartins02.github.io/hymet-docs/testdataset.html)**: Verified example files for pipeline validation  

## Choosing Your Input Type  

| Analysis Stage          | Recommended Format | Use Case |  
|-------------------------|--------------------|----------|  
| **Direct Classification** | Processed FASTA    | Re-analysis of assembled contigs |  
| **Full Metagenomics**    | Raw FASTQ          | End-to-end analysis from sequencing reads |  
| **Method Validation**    | Test Dataset       | Protocol testing and benchmarking |  


## Which Scenario Describes Your Needs?  

<div class="input-options">
  <div class="option-card">
    <h3>1. I have processed FASTA files</h3>
    <p>Already have assembled contigs or quality-filtered sequences?</p>
    <ul>
      <li>Direct taxonomic classification</li>
      <li>No preprocessing needed</li>
      <li>Fastest analysis path</li>
    </ul>
    <a href="https://inesbmartins02.github.io/hymet-docs/basicinput.html" class="btn btn-purple">Use Basic Input Mode →</a>
  </div>

  <div class="option-card">
    <h3>2. I have raw FASTQ files</h3>
    <p>Starting with raw sequencing data?</p>
    <ul>
      <li>Full QC + host removal</li>
      <li>Optional assembly</li>
      <li>End-to-end processing</li>
    </ul>
    <a href="https://inesbmartins02.github.io/hymet-docs/pipelineinput.html" class="btn btn-purple">Use Pipeline Mode →</a>
  </div>

  <div class="option-card">
    <h3>3. I need test data</h3>
    <p>Want to try HYMET first?</p>
    <ul>
      <li>Pre-verified datasets</li>
      <li>Includes expected results</li>
      <li>Training and validation</li>
    </ul>
    <a href="https://inesbmartins02.github.io/hymet-docs/testdataset.html" class="btn btn-blue">Download Test Data →</a>
  </div>
</div>

<!-- 
[Proceed to Basic Requirements →](https://inesbmartins02.github.io/hymet-docs/basicinput.html){: .btn .btn-purple }  
[Download Test Data →](https://inesbmartins02.github.io/hymet-docs/testdataset.html){: .btn .btn-blue }   -->
