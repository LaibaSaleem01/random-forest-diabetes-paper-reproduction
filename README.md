# Diabetes Prediction Using Random Forest

This project reproduces a published Random Forest study for diabetes prediction using the BRFSS 2015 dataset.

The dataset contains health-related information collected from 70,692 individuals.

The Random Forest model is used to predict whether a person belongs to the diabetes or prediabetes class based on different health indicators.

The project compares different Random Forest models and studies how tuning and feature selection affect model performance.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LaibaSaleem01/random-forest-diabetes-paper-reproduction/blob/main/diabetes_prediction_random_forest.ipynb)

## Dataset

The dataset contains 21 health-related features.

Some important features include:

General Health  
High Blood Pressure  
Body Mass Index  
Age  
High Cholesterol  
Physical Activity  
Income  
Education  

The target labels are:

0 means No Diabetes  
1 means Prediabetes or Diabetes  

The dataset is balanced, which means both target classes contain approximately the same number of records.

## Technologies Used

Python  
Pandas  
NumPy  
Matplotlib  
Scikit-learn  
KaggleHub  
Google Colab  

## Models Tested

The project tests the following Random Forest models:

Default Random Forest  
Balanced Random Forest  
Tuned Random Forest  
Tuned Random Forest using Top 16 Features  
Tuned Random Forest using Top 12 Features  
Tuned Random Forest using Top 8 Features  
Tuned Random Forest using Top 4 Features  

## Parameters Used

The tuned Random Forest uses the following parameters:

n_estimators = 200  
max_depth = 10  
min_samples_split = 10  

These parameters control the number of trees, the maximum depth of each tree, and the minimum number of samples required to split a node.

## Evaluation

The models are evaluated using:

Training Accuracy  
Testing Accuracy  
Precision  
Recall  
F1 Score  
Confusion Matrix  
ROC Curve  
AUC Score  
Overfitting Gap  

## Results

The Default Random Forest achieved:

Training Accuracy = 99.51%  
Testing Accuracy = 73.71%  
F1 Score = 74.75%  

The large difference between training and testing accuracy showed that the model was overfitting.

The Tuned Random Forest achieved:

Training Accuracy = 77.11%  
Testing Accuracy = 75.22%  
F1 Score = 76.22%  

The tuned model reduced the overfitting gap and performed better on unseen data.

## Feature Selection

Feature importance was used to identify the most useful health indicators.

The four most important features were:

General Health  
High Blood Pressure  
Body Mass Index  
Age  

The model using only these four features achieved:

Testing Accuracy = 74.08%  
F1 Score = 75.14%  

This result showed that most of the predictive performance could still be retained using a much smaller feature set.

## Paper Reproduction

The project reproduces the experiments from the published paper:

Efficient Diabetes Prediction Using Random Forests and Minimal Health Indicators on the BRFSS Dataset

The reproduced results were either identical or very close to the values reported in the original paper.

## Model Used

Random Forest Classifier

## Purpose

The purpose of this project is to understand how Random Forest can be used for diabetes prediction and how model tuning affects overfitting and generalization.

The project also demonstrates how feature importance can be used to reduce the number of input features while keeping most of the model performance.

This project was completed as a research paper reproduction and learning exercise.

## Disclaimer

This project is created for educational and research purposes only.

The model should not be used as a medical diagnosis system.
