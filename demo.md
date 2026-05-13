# Training Workbook – What You Will Learn

This Jupyter notebook acts as a **hands-on ETL workshop**, guiding you step-by-step through building a simple data pipeline using Python and PostgreSQL.

***

## Connect & Go to Work

To begin working with the training environment, open the example notebook:
once you get the environment up run:

```text
http://127.0.0.1:18890/lab?token=mytoken123
```

click on the left folder and select example.ipynb

## Overview

The workbook simulates a real-world data engineering workflow where you will:

- Connect to a database running in Docker  
- Extract data using SQL queries  
- Transform that data using pandas  
- Visualise insights using Python libraries  
- Export processed data for downstream use  

***

## Learning Outcomes

By completing this workbook, you will be able to:

- Establish a connection from Python to PostgreSQL using SQLAlchemy  
- Execute SQL queries and retrieve structured data  
- Load query results into pandas DataFrames  
- Perform basic data transformations and aggregations  
- Create visualisations to explore trends in the data  
- Export cleaned and transformed datasets to CSV  
- Understand how databases, Python, and Docker interact in an ETL pipeline  

***

## End-to-End Workflow

The notebook follows a structured pipeline:

### 1. Extract

- Connect to PostgreSQL using environment variables  
- Query database tables using SQL  
- Load results into pandas  

### 2. Transform

- Clean and structure the data  
- Perform aggregations and grouping  
- Prepare datasets for analysis  

### 3. Analyse & Visualise

- Generate charts using matplotlib and seaborn  
- Identify patterns such as pricing trends  

### 4. Load / Export

- Save processed data to CSV  
- Prepare outputs for further analysis or reporting  

***

## Real-World Relevance

This workbook mirrors common data engineering tasks:

- Working with containerised databases (Docker)  
- Building reproducible data pipelines  
- Performing exploratory data analysis (EDA)  
- Moving data between systems  

It provides a foundation for more advanced topics such as:

- Automated pipelines  
- Data warehousing  
- Streaming and real-time processing  

***

## Who This Is For

This training is ideal for:

- Beginners learning Python for data engineering  
- Analysts transitioning into engineering workflows  
- Developers looking to understand ETL fundamentals  

***

## Expected Outcome

By the end of the workshop, you will have:

- Built a working Python-to-PostgreSQL pipeline  
- Queried and transformed relational data  
- Produced visual insights from real datasets  
- Exported a final dataset ready for reuse  
