
# IT Help Desk — Data Engineering Pipeline

**Databricks · PySpark · Python · SQL · Delta Lake · Unity Catalog · Lakeflow Jobs**

## Project Overview

I built this project to practise Data Engineering using a dataset of 100,000 synthetic IT support tickets.

The project follows the **Medallion Architecture**, with three layers:

- **Bronze:** Raw data ingestion
- **Silver:** Data cleaning and validation
- **Gold:** Aggregated tables for reporting

## Pipeline Architecture

![Medallion Architecture](images/project_overview.png)

## Data Processing

### 1. Exploratory Data Analysis (EDA)

I started by exploring the dataset, checking missing values, duplicate ticket IDs and ticket categories.

### 2. Bronze Layer

I loaded the CSV file into Databricks and saved it as a Delta table.

### 3. Silver Layer

I cleaned the data, standardized categories and added columns for reporting.

### 4. Gold Layer

I created reporting tables for ticket KPIs, monthly trends, priority performance and regional performance.

## Pipeline Orchestration

I configured a Databricks Lakeflow Job to run the notebooks in order:

**Bronze → Silver → Gold**

## Dataset

[Synthetic IT Support Tickets — Kaggle](https://www.kaggle.com/datasets/ahsanneural/synthetic-it-support-tickets)
