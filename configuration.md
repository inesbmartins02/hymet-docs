---
title: Configuration
layout: home
nav_order: 3
parent: Home
---

## Reference Sketched Databases

The databases required to run the tool are available for download on Google Drive:
- **sketch1.msh.gz**: [Download](https://drive.google.com/drive/folders/1YC0N77UUGinFHNbLpbsucu1iXoLAM6lm?usp=share_link)
- **sketch2.msh.gz**: [Download](https://drive.google.com/drive/folders/1YC0N77UUGinFHNbLpbsucu1iXoLAM6lm?usp=share_link)
- **sketch3.msh.gz**: [Download](https://drive.google.com/drive/folders/1YC0N77UUGinFHNbLpbsucu1iXoLAM6lm?usp=share_link)

### Steps to Use the Databases

1. **Download the Files**:
   - Click on the links above to download the `.gz` files.

2. **Place the Files in the `data/` Directory**:
   - Move the downloaded files to the `data/` directory of the project.

3. **Unzip the Files**:
   - Use the following command to unzip the `.gz` files:
     ```bash
     gunzip data/sketch1.msh.gz
     gunzip data/sketch2.msh.gz
     gunzip data/sketch3.msh.gz
     ```
   - This will extract the files `sketch1.msh`, `sketch2.msh`, and `sketch3.msh` in the `data/` directory.

4. **Verify the Files**:
   - After unzipping, ensure the files are in the correct format and location:
     ```bash
     ls data/
     ```
   - You should see the files `sketch1.msh`, `sketch2.msh`, and `sketch3.msh`.


## Initial setup
Ensure all scripts have execution permissions:
   ```bash
   chmod +x config.pl
   chmod +x main.pl
   chmod +x scripts/*.sh
   chmod +x scripts/*.py
   ```

After installation and configuration, first you should run the configuration script to download and prepare the taxonomy files, and define the main paths.

```bash
./config.pl
```

Then, you can run the main tool to perform taxonomic identification:

```bash
./main.pl
```

If installed via Conda, you can use:
```bash
hymet-config
hymet
```