# Spotify Genre Classification (2022)

This project was developed as a group assignment for the **Data Science and Machine Learning 1** course at the **University of Crete, Department of Physics**.

## Project Overview
The goal of this project is to build a multi-class genre classifier using Spotify audio features. By analyzing track-level descriptors (such as danceability, energy, and acousticness), the project compares the performance of three common machine learning model families to determine the most effective approach for music genre prediction.

## Dataset
The dataset is sourced from the [Ultimate Spotify Tracks Database on Kaggle](https://www.kaggle.com/datasets/zaheenhamidani/ultimate-spotify-tracks-db). It contains metadata and audio features for over 232k tracks across various genres.

## Getting Started

To run this project locally, follow these steps to set up your environment:

```powershell
# Create a virtual environment
python -m venv .venv

# Activate the virtual environment (Windows)
.\.venv\Scripts\activate

# Install required dependencies
pip install -r requirements.txt
```

## Implementation & Optimization
This repository contains the evolution of the project across three iterations:
1.  **Original Implementation:** The initial model development which focused on exhaustive Grid Search for hyperparameter tuning.
2.  **Refined Versions:** Two subsequent versions focused on **computational efficiency**. Optimized the training pipeline by implementing `RandomizedSearchCV`, adjusting class balance for better stability, and reducing redundant processing.

The final optimized version achieves comparable accuracy to the exhaustive original while running significantly faster, demonstrating a more professional and efficient machine learning pipeline.

## Methodology
- **Data Cleaning:** Missing value validation, duplicate removal based on `track_id`, and label normalization.
- **Preprocessing:** Categorical encoding for variables like `key` and `mode`, and feature scaling (StandardScaler/MinMaxScaler) where required for specific model families.
- **Dimensionality Reduction:** Filtering overlapping or underrepresented genres to improve class separability.
- **Model Comparison:** 
    - **Support Vector Machine (SVM)**
    - **Random Forest (Ensemble Learning)**
    - **Multi-layer Perceptron (Neural Network)**

## Key Findings
- **Best Performer:** The **Random Forest** model consistently outperformed other families, achieving a top accuracy of **~81.9%**.
- **Feature Importance:** Feature analysis revealed that **Acousticness** and **Instrumentalness** are the most discriminative features for genre classification.
- **Optimization:** Found that the Random Forest baseline settings are highly effective for this dataset; exhaustive tuning provided only marginal gains compared to the computational cost.

## Results Summary
| Model | Baseline Accuracy | Tuned Accuracy |
| :--- | :--- | :--- |
| **Random Forest** | **0.8189** | 0.8172 |
| **SVM** | 0.8003 | 0.8044 |
| **MLP (Neural Net)** | 0.8034 | 0.8039 |
