# 3D Protein Structure Modeling using MODELLER

This repository contains the Python scripts and input alignment files I used to build a 3D homology model of an unknown protein structure based on a single template using MODELLER. 

The workflow is based on satisfying spatial restraints and optimizing a molecular probability density function (pdf).

---

## What the Files Do

### Core Python Scripts
- build_profile.py: Takes the target sequence and scans a database of known structures to pick up homologous sequences.
- align2d.py: Aligns the target sequence with the selected template structure to create an optimal sequence-structure alignment.
- model_single.py: Generates the final 3D protein models and assesses their structural energy.

### Alignments and Databases
- sequence.ali: The initial target sequence input file in PIR format.
- pdb_95.pir / pdb_95.bin: The protein database used for screening homologous templates.
- build_profile.ali / build_profile.prf / build_profile.log: The output profiles generated after running the database search.
- align2d.log: The log file verifying that the 2D alignment completed successfully.

---

## Workflow Followed

1. Template Screening
First, I formatted my target sequence into a .ali file. I then used build_profile.py to scan the target against the pdb_95 database. This generated the build_profile.prf file, which lists the best matching structural templates ranked by their e-values and sequence identity percentages.

2. Sequence-Structure Alignment
After identifying a suitable template structure from the profile results, I used align2d.py to create a highly accurate structural alignment between the target sequence and the template's atom files.

3. Model Generation & Evaluation
The final step uses model_single.py to calculate the spatial restraints and build the actual 3D .pdb model files. The script automatically scores the generated models using DOPE and GA341 assessment metrics to ensure high stereochemical quality.

---

## Prerequisites
- MODELLER (v9.21 or compatible)
- Python environment equipped with Modeller library tools
