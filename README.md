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

### ELT Pipeline
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

## Repository
- https://github.com/mlnotes2718/hdb-resale-price-e2e-elt
- https://github.com/mlnotes2718/hdb-resale-price-e2e-ml


## Latest Release
- 11 Jul 2025: ELT pipeline v1.0 is release Release Notes: (https://github.com/mlnotes2718/hdb-resale-price-e2e-elt/releases/tag/v1.0)


Reference:
- https://medium.com/@hargobind/not-your-average-hdb-resale-price-predictor-a0ea0c1fa6c2
- https://wongcheefah.pythonanywhere.com/data_project/