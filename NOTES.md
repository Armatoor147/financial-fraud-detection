# Prerequisites

- Python
- Machine Learning
- Docker
- Kubernetes


# Project Plan

1. Data Preparation & Modelling

- Data Collection: Download a fraud detection dataset ("Credit Card Fraud Detection" from Kaggle).


2. Containerisation
3. Kubernetes Deployment
4. Scaling and Monitoring
5. Documentation & Presentation


# Timeline

The first step is to try out different ML models and find the most accurate one by tweaking different model features and comparing the evaluation metrics. In the case of fraud detection, we value the model's accuracy but we also value that no fraud is left undetected (i.e. minimising false positives (false alarms)). We care more about minimising false positives than minimising false negatives.

Once a good model has been found we save it in a pkl file for later use in the deployment phase. Note that if a new and better ML model is found, then it can be redeployed.

Then I created the app (src/app.py) that will load the model and expose it as an API endpoint.

Then I set up the Dockerfile for containerisation (containerising the fraud detetction model with Docker ensures it can be deployed consistently anywhere, especially on Kubernetes). I build the docker image and ran it locally to make sure it works. I then tested the API by running a curl command with a mock transaction.

Then I wrote Kubernetes manifests in YAML files to describe the objects in my cluster. Then I a deployed the manifests to Kubernetes. Then I accessed the API for testing.


# ML model features

Classifier: LogisticRegression, RandomForestClassifier, XGBClassifier, LightGBM


# Evaluation metrics for ML models

- Classification report
- Confusion matrix
- Accuracy score


# Tested ML models

1) SMOTE (before train/test split)
Data leakage -> synthetic samples influenced both train and test.

2) SMOTE (inside pipeline (i.e. for train only))
Realistic seperation between train/test data.

3) Balanced class weight (instead of SMOTE)
Sometimes logistic regression with class weights performs better thatn SMOTE (less overfitting).