#Scalar Coupling Prediction

This repository contains the implementation and workflow for predicting scalar coupling constants (J-coupling) between pairs of atoms in organic molecules. The project is based on the Kaggle challenge organized by CHAMPS (CHemistry And Mathematics in Phase Space).

🧪 Problem Description
Nuclear Magnetic Resonance (NMR) is a crucial technique for understanding the structure and dynamics of molecules. A key parameter is the scalar coupling constant, which measures the magnetic interaction between the nuclei of two atoms.

While these values can be calculated using quantum mechanics (such as DFT), these calculations are extremely computationally expensive. The goal of this project is to develop fast and accurate Machine Learning models to predict these properties directly from the 3D structure of the molecule.

🚀 Key Features
Exploratory Data Analysis (EDA): Visualization of molecular structures and distribution of coupling constants across different bond types.

Feature Engineering: Generation of chemical descriptors, including Euclidean distances, bond angles, atom types, and molecular geometry features.

Modeling: Implementation of high-performance models based on Gradient Boosting (LightGBM/XGBoost) or Neural Networks.

Optimization: Hyperparameter tuning focused on minimizing the logarithmic Mean Absolute Error (MAE).

📂 Repository Structure
notebooks/: Jupyter Notebooks containing step-by-step analysis, feature engineering, and model training.

src/: Python scripts for data preprocessing and utility functions.

data/: (Not included due to size) Placeholder for Kaggle datasets (train.csv, test.csv, structures.csv).

models/: Serialized trained models and evaluation logs.

🛠️ Installation & Setup
To run this project, ensure you have Python 3.8+ installed along with the following dependencies:

Bash

pip install pandas numpy matplotlib seaborn scikit-learn lightgbm
Clone the repository:

Bash

git clone https://github.com/CarlosSolisGarcia/ScalarCouplingPrediction.git
cd ScalarCouplingPrediction
Dataset: Download the data from the Kaggle Predicting Molecular Properties Competition and place the CSV files in the data/ directory.

📊 Evaluation Metric
The performance is evaluated using the Group MAE, which is the average of the log of the Mean Absolute Error calculated for each coupling type (e.g., 1JHC, 2JHH, 3JHI).
