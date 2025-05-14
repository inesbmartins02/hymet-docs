---
title: Installation
nav_order: 1
---

# Installation

To begin using HYMET, you must first install and configure the tool. We provide options for installation using Docker (recommended for ease and reproducibility) or Conda.

### 1. Installation with Conda (Recommended)

The easiest way to install HYMET is through Bioconda:

```bash
conda install -c bioconda hymet
```

### 2. Clone the Repository

Alternatively, you can clone the repository to your local environment:

```bash
git clone https://github.com/inesbmartins02/HYMET.git
cd HYMET
```

### 3. Installation with Docker

If you prefer using Docker, follow these steps:

1. **Build the Docker Image**:
   ```bash
   docker build -t hymet .
   ```

2. **Run the Container**:
   ```bash
   docker run -it hymet
   ```

3. **Inside the Container**:
   - The environment will already be set up with all dependencies installed.
   - Run the tool as needed.

### 4. Installation with Conda Environment File

If you cloned the repository, you can create a Conda environment from the included file:

1. **Create the Conda Environment**:
   ```bash
   conda env create -f environment.yml
   ```

2. **Activate the Environment**:
   ```bash
   conda activate hymet_env
   ```
