# Spotify Genre Classification (2022)

This project was developed as a group assignment for the **Data Science and Machine Learning 1** course at the **University of Crete, Department of Physics**.

## Project Overview
The goal of this project is to build a multi-class genre classifier using Spotify audio features. By analyzing track-level descriptors (such as danceability, energy, and acousticness), we compare the performance of three model families to determine the most effective approach for music genre prediction.

## Dataset
The dataset is sourced from the [Ultimate Spotify Tracks Database on Kaggle](https://www.kaggle.com/datasets/zaheenhamidani/ultimate-spotify-tracks-db). It contains metadata and audio features for over 232k tracks.

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

## Repository Structure
This repository contains two versions of the analysis to demonstrate the progression from initial development to computational optimization:

*   **`Spotify-Genre-Classification-Original.ipynb`**: Our initial submission. It utilizes exhaustive `GridSearchCV` and a higher number of Cross-Validation folds. While highly thorough, it has a significant computational runtime (e.g., SVM tuning exceeding 1.5 hours).
*   **`spotify-genre-classification-Revised.ipynb`**: An optimized version of the project. It streamlines the pipeline using `RandomizedSearchCV` and more efficient data processing. It achieves equivalent (and in some cases superior) accuracy while running in a fraction of the time.

## Methodology
- **Data Cleaning:** Missing value validation, duplicate removal based on `track_id`, and label normalization.
- **Preprocessing:** Categorical encoding for variables like `key` and `mode`, and feature scaling where required (StandardScaler/MinMaxScaler).
- **Dimensionality Reduction:** Filtering overlapping genres to improve class separability.
- **Models Compared:** 
    - Support Vector Machine (SVM)
    - Random Forest (Ensemble Learning)
    - Multi-layer Perceptron (Neural Network)

## Key Findings
- **Best Performer:** The **Random Forest** model consistently outperformed other families, achieving a top accuracy of **~81.9%**.
- **Feature Importance:** Analysis revealed that **Acousticness** and **Instrumentalness** are the most discriminative audio features for genre separation.
- **Efficiency:** The revised version demonstrates that strategic hyperparameter selection and search methods can maintain high accuracy while drastically reducing hardware strain.
