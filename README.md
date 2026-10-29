IT Help Desk — Data Engineering Pipeline
Databricks · PySpark · Python · SQL · Delta Lake · Unity Catalog · Lakeflow Jobs

I built this project to practise data engineering with Databricks, using a dataset of 100,000 synthetic IT support tickets. I explored the data, created Bronze, Silver and Gold tables, and connected the processing notebooks in a Databricks Job.
Project overview

The image is an illustration of the architecture, not a screenshot of actual results. The notebooks contain the real analysis and transformations.
Architecture
IT support tickets (CSV)
          |
          v
    Bronze (Delta)
          |
          v
    Silver (Delta)
          |
          v
     Gold (Delta)
          |
          v
 Reporting-ready tables
I use Unity Catalog to organize the source file and Delta tables. A Lakeflow Job runs the Bronze, Silver and Gold notebooks in order.
What I did
1. Exploratory Data Analysis (EDA)
I started by checking the dataset's structure, missing values, ticket categories and trends. I also checked duplicate ticket IDs and reviewed how resolution times and customer satisfaction scores are recorded.
2. Bronze — Load the raw data
I read the original CSV from a Unity Catalog Volume, added an ingestion timestamp and saved the data as a Delta table.
3. Silver — Clean the data
I removed duplicate ticket IDs, standardized fields such as priority and status, and prepared useful columns for reporting. I kept NA as the valid region code for North America, and excluded CSAT scores of 0 from averages because they represent no survey response.
4. Gold — Prepare reporting tables
I created aggregated Delta tables for overall ticket KPIs, monthly trends, priority performance and regional performance. These tables are ready to be used by a reporting tool.
5. Orchestration
I configured a Databricks Lakeflow Job with three dependent tasks:

Bronze → Silver → Gold

This ensures each notebook runs after the previous one succeeds.
Repository structure
IT-HelpDesk-Data-Engineering/
├── README.md
├── notebooks/
│   ├── 01_EDA.ipynb
│   ├── 02_Bronze.ipynb
│   ├── 03_Silver.ipynb
│   └── 04_Gold.ipynb
└── images/
    ├── project_overview.png
    ├── databricks_job.png       # Add your screenshot
    └── eda_charts.png           # Add your charts
Databricks Job
After uploading your screenshot to images/databricks_job.png, uncomment this line:
<!-- ![Databricks Bronze → Silver → Gold Job](images/databricks_job.png) -->

Dataset
Synthetic IT Support Tickets — Kaggle

The data is synthetic and used for learning and portfolio purposes.
Next steps
I plan to keep improving this project by adding more data quality checks and exploring incremental data loading.
