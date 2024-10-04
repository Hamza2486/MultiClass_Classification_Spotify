


# Multi-Class Music Genre Classification using Spotify Data

## Project Overview

This project explores the use of various machine learning models to classify songs into different genres based on audio features provided by Spotify. The dataset contains 50,000 randomly selected songs and includes features like *tempo*, *energy*, *danceability*, and more.

## Dataset Overview

The dataset, `musicData.csv`, contains the following columns for each of the 50,000 songs:

1. **Spotify ID**: Unique identifier for each song
2. **Artist Name**: Name of the song's artist
3. **Song Name**: Name of the song
4. **Popularity**: The popularity score of the song, ranging from 0 to 99%
5. **Acousticness**: Measure of the acoustic elements in the song, ranging from 0 to 1
6. **Danceability**: Measure of how suitable a track is for dancing, ranging from 0 to 1
7. **Duration**: Length of the song in milliseconds
8. **Energy**: Measure of intensity and activity, ranging from 0 to 1
9. **Instrumentality**: Amount of instrumentals in the song, ranging from 0 to 1
10. **Key**: Musical key of the song (encoded from 1 to 12)
11. **Liveness**: Probability of the track being performed live, ranging from 0 to 1
12. **Loudness**: The loudness of the track in decibels
13. **Mode**: Major or minor scale (binary format)
14. **Speechiness**: Measure of spoken words in the track, ranging from 0 to 1
15. **Tempo**: Speed of the track in beats per minute
16. **Obtained Date**: Date when the song's data was retrieved from Spotify
17. **Valence**: Positivity conveyed by a track, ranging from 0 to 1
18. **Genre**: The genre of the song (10 possible genres, encoded numerically)

## Pre-processing and Exploratory Data Analysis (EDA)

The dataset required several pre-processing steps to ensure its suitability for classification:

- **Data Cleaning**: Removed unnecessary columns (e.g., artist name, track name) and handled missing or erroneous values. Rows with NaN values and illogical values in the `tempo` and `duration` columns were either dropped or imputed with the median value of the genre to preserve uniform distribution across genres.
- **Categorical Features**: Transformed categorical columns such as `mode` and `key` into numerical format, and encoded genres numerically from 1 (Alternative) to 10 (Rock).
- **Standardization**: All features except binary and ordinal features were standardized for consistency.

## Dimensionality Reduction: Linear Discriminant Analysis (LDA)

Given the supervised nature of the task, **Linear Discriminant Analysis (LDA)** was used to reduce the dimensionality of the data while maximizing class separability.

## Clustering: K-Means

Using the LDA-transformed data, **K-Means clustering** was applied with 10 clusters (corresponding to the 10 genres).

## Classification Models

### 1. Support Vector Machines (SVM)

An **SVM** model was trained on the LDA-transformed data using cross-validation to optimize the regularization parameter.
### 2. Random Forest

A **Random Forest** model was trained on both the original and LDA-transformed data.

### 3. AdaBoost

An **AdaBoost** model was implemented with 100 estimators and tuned hyperparameters.
## Summary of Model Performance

| Model                  | Training Accuracy | Test Accuracy | Avg. ROC | Avg. Precision | Avg. Recall |
|------------------------|-------------------|---------------|----------|----------------|-------------|
| SVM                    | 0.445             | 0.446         | 0.83     | 0.43           | 0.43        |
| Random Forest           | 0.705             | 0.586         | 0.93     | 0.59           | 0.59        |
| Random Forest + LDA     | 0.535             | 0.502         | 0.90     | 0.50           | 0.50        |
| AdaBoost               | 0.632             | 0.525         | 0.91     | 0.53           | 0.52        |

## Report and Code

- **Report**: A detailed analysis of the models and methods used, including performance metrics and visualizations, can be found in `MultiClass_Classification_Spotify.pdf`.
- **Code**: The full code for the project is available in `MultiClass_Classification_Spotify.ipynb`.
