# HDB Resale Price Machine Learning End to End Pipeline Project Documentation

This is the master repository that contain the project master plan and consolidation of project documentation to implement an end to end machine learning pipeline on HDB resale Price Prediction.

## Objective:
The objective of this project is to showcase an end-to-end machine learning flow from teh data source to the presentation end. We use HDB Resale prediction as our project.

## Implementation Strategy
We will be using CI/CD approach to develop and improve this project over time.

## Data
- **Data Source**: data.gov.sg
- **Dataset Name**:  HDB Resale Flat Price based on registration from Jan 2017 onwards
- **Filename**: `ResaleflatpricesbasedonregistrationdatefromJan2017onwards.csv`

## Pipeline
![alt text](assets/e2e_p1.png)

## ELT Pipeline
- https://github.com/mlnotes2718/hdb-resale-price-e2e-elt
- We use a script file `run.sh` to execute the entire ELT flow.
- The script will execute the following process:
    - Run the python script `main.py`
    - This script will perform the following tasks:
        1. Load data from data.gov.sg (`data_download.py`)
        2. Clean the data and save the cleaned data into the dbt seeds folder. (`clean_hdb_resale_from_2017.py`)
    - Enter the dbt folder for HDB Resales Project
    - Run `dbt clean` to start new and install all dbt related dependencies first.
    - Run `dbt seed --target raw`
    - Run `dbt run`
    - Run `dbt test`
- The whole process is configure with Github Actions for a quick automation.
- Since this is a PoC prototype, there is no scheduling for Github Actions, only manual trigger.

## Machine Learning (ML) Pipeline
- https://github.com/mlnotes2718/hdb-resale-price-e2e-ml
- We use a python file `main.py` to execute the entire ML flow.
- The script will execute the following process:
    - Load configuration
    - Read the data file
    - Initialize and setup the data preparation class
    - Perform data cleaning by invoking the data cleaning method
    - Initialize the model training class and setup the preprocessor
    - Perform baseline training by invoking the baseline training method
    - Perform hyperparameters fine tuning by invoking the fine tune model method.
- This is a PoC prototype, model development and selection is not ready, we will use Linear Regression base line.
- The whole process is configure with Github Actions for a quick automation.
- Since this is a PoC prototype, there is no scheduling for Github Actions, only manual trigger.

## ML Deployment on Flask API
- https://github.com/mlnotes2718/hdb-resale-price-e2e-web-flask
- This is a static website deployed on render.com
- The website is at https://hdb-resale-price-e2e-web-flask.onrender.com
- Website allows user to enter the housing details and our ML model will make prediction.
- Model is copied from ML repository

## Repository
- https://github.com/mlnotes2718/hdb-resale-price-end-to-end-ml-project-docs (Current Repository)
- https://github.com/mlnotes2718/hdb-resale-price-e2e-elt (ELT Pipeline)
- https://github.com/mlnotes2718/hdb-resale-price-e2e-ml (Machine Learning Pipeline)
- https://github.com/mlnotes2718/hdb-resale-price-e2e-web-flask (Flask Static Website Deployment)


## Latest Release



Reference:
- https://medium.com/@hargobind/not-your-average-hdb-resale-price-predictor-a0ea0c1fa6c2
- https://wongcheefah.pythonanywhere.com/data_project/