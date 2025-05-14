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

### Key Principles  
- **Flexible Processing**: Convert between formats using built-in utilities  
- **Scalable Design**: Handles single files to multi-sample projects  
- **Quality-Aware**: Automatically detects and reports input issues  

> **Getting Started Tip**: New users should begin with our [Test Dataset](.https://inesbmartins02.github.io/hymet-docs/testdataset.html) to verify pipeline installation before analyzing experimental data.  

[Proceed to Basic Requirements →](https://inesbmartins02.github.io/hymet-docs/basicinput.html){: .btn .btn-purple }  
[Download Test Data →](https://inesbmartins02.github.io/hymet-docs/testdataset.html){: .btn .btn-blue }  
