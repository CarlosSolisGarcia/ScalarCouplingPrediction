# Scalar Coupling Prediction with Deep Learning

This repository contains the official implementation of my Master's Thesis (**TFM**) for the **Master in Data Science at UOC (Universitat Oberta de Catalunya)**, completed in January 2025. 

The project focuses on predicting scalar coupling constants (J-coupling) in organic molecules, a key parameter in Nuclear Magnetic Resonance (NMR), using high-performance Machine Learning and Deep Learning architectures.

## 🧪 Project Overview
Predicting molecular properties traditionally requires Density Functional Theory (DFT) calculations, which are extremely resource-intensive. This project demonstrates how **Graph Neural Networks (GNN)** and **Gradient Boosting** can approximate these values with high precision in a fraction of the time, using the CHAMPS dataset.

## 🚀 Key Features & Methodology

### 1. Data Engineering & Chemical Descriptors
The project leverages a multi-source approach to feature engineering:
* **External Chemical Data:** Integration of atomic properties (electronegativity, atomic radius, ionization energy) via **PubChem** API and **RDKit**.
* **Geometric Engineering:** Calculation of Euclidean distances, bond angles (3 atoms), and dihedral angles (4 atoms) to define the spatial chemical environment.
* **Graph Representation:** Molecules are modeled as **heterogeneous graphs**, where atoms are nodes and different types of couplings (1JHC, 2JHH, etc.) are treated as distinct edge types.

### 2. Modeling & Optimization
* **Deep Learning:** Implementation of GNNs using **DGL (Deep Graph Library)** and PyTorch. Tested architectures include `HeteroGraphConv`, `GraphSAGE`, and `GAT` (Graph Attention Networks).
* **Gradient Boosting (LightGBM):** A highly optimized baseline using **Optuna** for automated hyperparameter tuning, which achieved the best overall accuracy-to-latency ratio.
* **Multi-Target Strategy:** The model treats each coupling type specifically, acknowledging the unique physical nature of each bond interaction.

## 🛠️ Tech Stack
* **Core:** Python 3.10.14, PyTorch 2.2.2
* **Graph Processing:** DGL (Deep Graph Library) 2.0.0
* **Cheminformatics:** RDKit, Pybel (OpenBabel)
* **Optimization:** Optuna (Bayesian Optimization)

## 📓 Notebooks Structure

The project is organized into sequential notebooks to ensure reproducibility, following the data science pipeline from raw structures to optimized models:

### 1. Data Cleaning & Feature Engineering
* `01_Data_Exploration_and_Engineering.ipynb`: 
    * Initial EDA of the CHAMPS dataset.
    * Integration with **PubChem API** to fetch atomic properties.
    * Implementation of geometric calculations for bond angles and dihedrals using **RDKit**.
    * Generation of the final enriched dataset (`train_extended.csv`).

### 2. Graph Neural Networks (GNN)
* `Línia 1_HeteroGraphCN_Dataset.ipynb`:
    * Molecule conformation discarding non-stable molecules.
    * Construction of **Heterogeneous Graphs** using the Deep Graph Library (DGL).
        * Atomic bonding represented as one type of edge
        * Atomic coupling interaction represented as another type of edge.
    * Training loops and evaluation of node-edge interaction models.
* `Línia 2_GraphSAGE i GraphGAT.ipynb`:
    * Molecule conformation simplified to consider only coupled atoms as graph nodes and edges.
    * Implementation of `HeteroGraphConv`, `GraphSAGE`, and `GAT` architectures.
    * Training loops and evaluation of node-edge interaction models.

### 3. Gradient Boosting
* `Línia 3_LightGBM.ipynb`: 
    * Training of the initial Gradient Boosting Decision Tree (GBDT) models.
    * Automated hyperparameter tuning using **Bayesian Optimization** via Optuna.
    * Fine-tuning of learning rates, leaf sizes, and regularization to reach the final Global MAE of 0.95.

## 📊 Performance Summary
According to the final thesis results, the **Optimized LightGBM** model outperformed the initial GNN implementations in accuracy and computational efficiency.

| Model | Global MAE | Training Time |
| :--- | :---: | :---: |
| GNN (HeteroGraph) | 1.42 | ~4 hours |
| **LightGBM (Optimized)** | **0.95** | **~15 minutes** |

## 💡 Thesis Conclusions
* **GNN vs. Boosting:** While GNNs are theoretically ideal for molecular topology, LightGBM with robust feature engineering proved more effective for this specific scale of J-coupling prediction. LightGBM offered better accuracy with significantly lower training times (minutes vs. hours).
* **Feature Criticality:** Geometric features (bond angles and dihedrals) and external atomic properties (PubChem) were essential for reducing error in complex coupling types.

## 📂 Repository Structure
* `notebooks/`: Includes the full pipeline from EDA and Feature Engineering to Model Training.
* `src/`: Core logic for geometry calculations and data extraction from PubChem.
* `models/`: Configuration files and saved weights for the best-performing models.

---

## ✒️ Author
**Carlos Solís García** *Master's Thesis in Data Science | Universitat Oberta de Catalunya (UOC)* *January 2025*
