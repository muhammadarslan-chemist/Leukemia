# Integrated Machine Learning and CADD Approach for Discovery of Novel FLT3 Tyrosine Kinase Inhibitors in Leukemia Treatment

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Scikit--learn-orange)
![CADD](https://img.shields.io/badge/CADD-Molecular%20Docking%20%7C%20MD%20Simulation%20%7C%20DFT-green)
![Status](https://img.shields.io/badge/Status-Research-brightgreen)

## 📋 Overview

This repository presents an integrated Machine Learning (ML) and Computer-Aided Drug Design (CADD) approach for the discovery of novel FLT3 (FMS-like tyrosine kinase 3) inhibitors as potential therapeutic agents for leukemia treatment. FLT3 is a validated drug target in acute myeloid leukemia (AML). Our workflow combines ML-based virtual screening with molecular docking, molecular dynamics (MD) simulations, density functional theory (DFT) calculations, and ADMET profiling to identify promising hit compounds.

## 🔬 Research Methodology

### Workflow Summary
1. **Data Curation**: Active and inactive compounds with known IC50 values from ChEMBL database
2. **Feature Engineering**: Generation of six molecular descriptor/fingerprint types
3. **ML Model Development**: Training and evaluation of models for each feature type
4. **Virtual Screening**: Screening 100,000 compounds from ZINC-22 database
5. **Hit Selection**: Identification of compounds predicted to be active by all six models
6. **ADMET Profiling**: Filtering compounds with favorable pharmacokinetic properties
7. **Molecular Docking**: Docking with FLT3 receptor (PDB: 6JQR)
8. **MD Simulations & DFT**: Validation of top candidates through dynamics and quantum mechanics


## 🎯 Key Findings

- **Initial Screening**: 100,000 compounds from ZINC-22 database
- **ML Consensus**: 532 compounds predicted active by all six models
- **ADMET Filtering**: 20 compounds with favorable pharmacokinetic profiles
- **Docking Results**: 4 compounds with binding energies comparable to reference drug (gilteritinib)
- **Final Candidates**: 4 novel scaffolds identified as potential FLT3 inhibitors

## 📊 Dataset and Feature Engineering

### Data Source
- **Database**: ChEMBL (www.ebi.ac.uk/chembl/)
- **Target**: FLT3 kinase (UniProt ID: P36888)
- **Activity Data**: IC50 values for active and inactive compounds
- **Data Curation**: Standardization, duplicate removal, activity classification

### Six Molecular Representations

| Feature Type | Description | Dimension |
|-------------|-------------|-----------|
| **RDKit Descriptors** | Physicochemical properties (MW, LogP, TPSA, etc.) | 12 |
| **MACCS Fingerprints** | 166-bit structural keys | 166 |
| **Morgan Fingerprints** | Circular fingerprints (ECFP4) | 2048 |
| **Atom-Pairs Fingerprints** | 2D atom pair descriptors | 2048 |
| **PubChem Fingerprints** | 881-bit structural fingerprints | 881 |
| **RDKit Topological Fingerprints** | Topological torsions | 2048 |

## 🤖 Machine Learning Workflow

### Model Development
- Trained separate ML models for each of the six feature types
- Selected best-performing model based on AUC-ROC scores
- Algorithms evaluated: Random Forest, XGBoost, SVM, Neural Networks

### Consensus Screening Strategy
- Compounds predicted as "active" by ALL six best-performing models
- Rationale: Reducing false positives through ensemble consensus
- Result: 532 consensus-active compounds from 100,000 screened

## 💻 Computational Methods

### 1. Machine Learning
- **Packages**: Scikit-learn, XGBoost, RDKit, Pandas, NumPy
- **Validation**: 5-fold cross-validation, external test set
- **Metrics**: AUC-ROC, Accuracy, Precision, Recall, F1-score

### 2. ADMET Profiling
- **Absorption**: Caco-2 permeability, intestinal absorption
- **Distribution**: Plasma protein binding, BBB penetration
- **Metabolism**: CYP450 inhibition profiles
- **Excretion**: Half-life, clearance
- **Toxicity**: Ames test, hepatotoxicity, hERG inhibition

### 3. Molecular Docking
- **Software**: AutoDock Vina / Glide
- **Receptor**: FLT3 kinase domain (PDB: 6JQR)
- **Reference Drug**: Gilteritinib
- **Analysis**: Binding energy scores, interaction fingerprints

### 4. Molecular Dynamics Simulations
- **Software**: GROMACS / AMBER
- **Timescale**: 100 ns simulations
- **Analysis**: RMSD, RMSF, hydrogen bonding, binding free energy (MM-PBSA)

### 5. DFT Calculations
- **Software**: Gaussian / ORCA
- **Level of Theory**: B3LYP/6-31G**
- **Properties**: HOMO-LUMO gap, electrostatic potential, optimization energy
