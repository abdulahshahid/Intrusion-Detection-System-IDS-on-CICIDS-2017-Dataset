# Intrusion Detection System (IDS) on CICIDS 2017 Dataset

This project focuses on implementing an Intrusion Detection System (IDS) using the CICIDS 2017 dataset. The notebook provided contains step-by-step procedures for loading, preprocessing, analyzing, and modeling data to detect intrusions effectively.

## Table of Contents
1. [Overview](#overview)
2. [Dataset Information](#dataset-information)
3. [Project Workflow](#project-workflow)
4. [Dependencies](#dependencies)
5. [Results and Evaluation](#results-and-evaluation)

---

## Overview
The CICIDS 2017 dataset contains labeled network traffic data simulating real-world intrusion scenarios. This project leverages the dataset to train machine learning models for identifying normal and anomalous network behavior.

The key objectives of this project include:
- Data preprocessing and feature engineering.
- Exploratory data analysis (EDA) for feature selection and visualization.
- Training and evaluating classification models to detect intrusions.

---

## Dataset Information
The CICIDS 2017 dataset simulates various types of network attacks, including DoS, DDoS, brute force, and phishing attempts, alongside normal traffic. Each record includes multiple network features such as:
- Packet length statistics
- Flow duration
- Protocol type
- Source and destination IPs
- Flags and other network-specific metrics

### Attack Classes:
- BENIGN
- Bot
- DDoS
- DoS GoldenEye
- DoS Hulk
- DoS Slowhttptest
- DoS slowloris
- FTP-Patator
- Heartbleed
- Infiltration
- PortScan
- SSH-Patator
- Web Attack – Brute Force
- Web Attack – Sql Injection
- Web Attack – XSS

#### Original Class Distribution:
```
Counter({
    0: 439683, 4: 230124, 10: 158804, 2: 128025, 3: 10293,
    7: 7935, 11: 5897, 6: 5796, 5: 5499, 1: 1956, 12: 1507,
    14: 652, 9: 36, 13: 21, 8: 11
})
```

#### Resampled Class Distribution:
```
Counter({
    0: 439683, 2: 439683, 10: 439683, 1: 439683, 9: 439683,
    7: 439683, 11: 439683, 3: 439683, 4: 439683, 5: 439683,
    6: 439683, 8: 439683, 12: 439683, 13: 439683, 14: 439683
})
```

For more information, visit the [CICIDS 2017 dataset website](https://www.unb.ca/cic/datasets/ids-2017.html).

---

## Project Workflow

1. **Data Loading:**
   - The dataset is loaded into a Pandas DataFrame.
   - Data includes both benign and attack labels.

2. **Preprocessing:**
   - Handling missing values and duplicates.
   - Converting categorical features to numerical format (e.g., one-hot encoding).
   - Feature scaling and normalization.

3. **Exploratory Data Analysis (EDA):**
   - Visualizing class distributions.
   - Correlation heatmaps for feature importance.

4. **Feature Engineering:**
   - Dropping irrelevant or highly correlated features.
   - Feature selection based on domain knowledge and statistical methods.
   - Selected Features (using Chi-squared test):
     ```
     [' Flow Duration', 'Total Length of Fwd Packets', ' Fwd Packet Length Max',
      'Flow Bytes/s', ' Flow Packets/s', ' Flow IAT Mean', ' Flow IAT Std',
      ' Flow IAT Max', 'Fwd IAT Total', ' Fwd IAT Mean', ' Fwd IAT Std',
      ' Fwd IAT Max', ' Fwd IAT Min', ' Bwd Packets/s', ' Packet Length Mean',
      ' Packet Length Std', ' Packet Length Variance', ' Average Packet Size',
      ' Subflow Fwd Bytes', ' Active Min']
     ```

5. **Model Training:**
   - Training multiple machine learning models, including:
     - Logistic Regression
     - Decision Trees
     - Random Forests
     - Support Vector Machines (SVM)
     - Neural Networks
   - Hyperparameter tuning using grid search or cross-validation.

6. **Evaluation:**
   - Metrics include accuracy, precision, recall, F1-score, and ROC-AUC.
   - Generating confusion matrices to analyze model performance.

---

## Dependencies

The following Python libraries are required:
- `numpy`
- `pandas`
- `matplotlib`
- `seaborn`
- `scikit-learn`
- `tensorflow`


---

## Usage Instructions

1. Clone the repository and navigate to the project directory.
2. Open the Jupyter notebook file `ids-on-cicids2017.ipynb`.
3. Execute the cells step by step to reproduce the analysis and results.
4. Modify the hyperparameters or dataset path as needed.

---

## Results and Evaluation

### Model Accuracies:
- **Random Forest:** 96.27%
- **Deep Neural Network (DNN):** 87.35%
