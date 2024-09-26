# Phase 2 Drug Discovery: Bioactivity Prediction

## Introduction
In this project, the goal was to develop a machine learning model to predict compounds' bioactivity against a therapeutic target. We focused on Methionine Aminopeptidase 2, a cancer-related protein. Bioactivity data were retrieved from the ChEMBL database, specifically compounds with IC50 values, which indicate the concentration required to inhibit 50% of the target protein's activity.

## Dataset and Preprocessing
The dataset from ChEMBL (version 34) included IC50 values, assay information, and molecular descriptors calculated using RDKit and Mordred. **Data preprocessing** involved:
- Cleaning and filtering missing or invalid IC50 values.
- Generating molecular descriptors to capture chemical and structural properties.
- Feature engineering with Principal Component Analysis (PCA) to reduce dimensionality.

![Molecular descriptors PCA](image1.png)
*Figure 1: PCA applied to molecular descriptors showing variance explained by each principal component.*

## Model Development and Training
A **Random Forest Regressor** was selected for predicting pIC50 (log-transformed IC50). The dataset was split into 80% training and 20% testing sets. The training phase captured non-linear relationships between molecular descriptors and pIC50. Evaluation metrics used were:
- **Mean Squared Error (MSE)**: 0.0504
- **Mean Absolute Error (MAE)**: 0.0952
- **R-squared**: 0.9647

Cross-validation was performed to ensure generalizability across different data folds.

![Model performance metrics](image2.png)
*Figure 2: Model performance across cross-validation folds, highlighting R-squared values.*

## Results and Feature Importance
Key molecular descriptors influencing bioactivity include:
- **Molecular Weight (MW)**: Heavier compounds showed varied bioactivity, indicating the importance of size.
- **LogP**: Lipophilicity affected compounds’ ability to permeate membranes.
- **Hydrogen Bond Acceptors/Donors**: Essential for compound-target interactions.

The scatter plot below demonstrates the relationship between binding affinity and pIC50, with a clear positive correlation between the two.

![Binding Affinity vs. pIC50](image3.png)
*Figure 3: Positive correlation between binding affinity and pIC50 values.*

## Conclusion
This study successfully built a Random Forest model for predicting pIC50 values, demonstrating robust predictive power. Future work should focus on refining molecular descriptors and validating results experimentally to discover more potent cancer therapy compounds.

