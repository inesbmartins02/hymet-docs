---
title: Installation
layout: home
nav_order: 1
---

# Installation

To begin using HYMET, you must first install and configure the tool. We provide options for installation using Docker (recommended for ease and reproducibility) or Conda.

## Installation with Conda (Recommended)

The easiest way to install HYMET is through Bioconda:

```
conda install -c bioconda hymet
```

## Clone the Repository

Alternatively, you can clone the repository to your local environment:

```
git clone [https://github.com/inesbmartins02/HYMET.git](https://github.com/inesbmartins02/HYMET.git)
cd HYMET
```

## Installation with Docker

If you prefer using Docker, follow these steps:

### Build the Docker Image

```
docker build -t hymet .
```

### Run the Container

```
docker run -it hymet
```

**Inside the Container:** The environment will already be set up with all dependencies installed. Run the tool as needed.

## Installation with Conda Environment File

If you cloned the repository, you can create a Conda environment from the included file:

### Create the Conda Environment

```
conda env create -f environment.yml
```

### Activate the Environment

```
conda activate hymet_env
```
[Next Step: Configuration →](https://inesbmartins02.github.io/hymet-docs/configuration.html)