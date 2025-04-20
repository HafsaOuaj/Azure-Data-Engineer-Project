# 🏗️ End-to-End Data Engineering Pipeline on Azure with Databricks

This project showcases a full-stack **data engineering pipeline** using **Azure Cloud Services**, **Databricks**, and **Power BI**, built on the **Adventure Works** dataset. It walks through the process from data ingestion to transformation and visualization using modern tools and best practices.

---

## 📊 Project Overview

![Architecture Diagram](./architecture.png)

- **Dataset**: [Adventure Works (Kaggle)](https://www.kaggle.com/datasets)
- **Pipeline**: Data Factory ➝ Data Lake Gen2 ➝ Databricks ➝ Synapse ➝ Power BI
- **Format**: Raw `.csv` ➝ Transformed `.parquet`

---

## ⚙️ Architecture Components

### 🔹 Data Source
- Public GitHub repository containing AdventureWorks `.csv` files.
- Fetched via HTTP using Azure Data Factory.

### 🔹 Ingestion (Bronze Layer)
- **Azure Data Factory**: Automated pipeline that stores raw CSVs into Azure Data Lake Gen2 (`bronze/` folder).

### 🔹 Transformation (Silver Layer)
- **Azure Databricks**: PySpark scripts clean, join, and convert data into optimized Parquet format.
- Transformations include:
  - Adding product names to sales records
  - Removing duplicates
  - Writing with `.write.mode('overwrite')`

### 🔹 Serving
- **Azure Synapse Analytics**: Connects to the transformed data and enables SQL queries.
- Serverless SQL pool used for fast access.

### 🔹 Visualization
- **Power BI**: Dashboards connect to Synapse to display sales and product insights interactively.

---

## 📁 Folder Structure (Local Structure)

```bash

📁 data/
    ├── silver/                # Original CSVs
    ├── bronze/                # Output of the Databricks transformations as Parquet files
    └── transformed/           # Output of Azure Synapse Analytics

📁 notebooks/
    └── 01_silver_layer.ipynb

📁 azureSynapseAnalytics/
    ├── Create_External_Tables.sql    # Create External Table as an Output of Synapse Analytics      
    ├── Create_Schema.sql             # Create Schema     
    └── Create_View_Gold.sql          # Create Views from DataLake Silver data
    
📁 reports/
    └── powerbi_dashboard.pbix

📄 README.md
```
## ☁️ Azure Deployment Info

All ETL scripts, notebooks, and pipelines are stored in Azure:

- **Resource Group**: `AWPROJECT`
- **Services used**:
  - Azure Data Factory (pipelines, linked services, datasets)
  - Azure Databricks (notebooks in workspace)
  - Azure Synapse (SQL pools and data explorer)
  - Azure Data Lake Gen2 (blob containers: `bronze`, `silver`)

### 📤 Sharing Scripts

To share the scripts hosted in Azure:
1. **Databricks notebooks**:  
   - Go to your workspace → right-click notebook → Export → HTML or Source file (`.dbc` or `.ipynb`)
   - Add them to a `/notebooks` folder in this repo

2. **Data Factory Pipelines**:  
   - Use the "Export ARM Template" option from your Data Factory instance
   - Add the `ARMTemplateForFactory.json` file under `/infrastructure/` folder

3. **Synapse SQL Scripts**:  
   - Export your scripts from the Synapse workspace and include them in `/sql-scripts/`

---

## 🧠 Key Concepts

- **Delta Lake** & Parquet optimization
- `.join()` in PySpark
- `.write.mode()` usage: `append`, `overwrite`, `ignore`
- Serverless SQL querying
- End-to-end orchestration with Azure services

---

## 🚀 How to Run

1. Clone the repository:
   ```bash
   git clone [https://github.com/your-username/adventureworks-pipeline.git](https://github.com/HafsaOuaj/Azure-Data-Engineer-Project)
   ```

2. Load raw data into Azure Data Lake (Bronze layer).

3. Trigger ADF pipeline for ingestion.

4. Run Databricks notebooks for transformation.

5. Query data from Synapse or visualize with Power BI.

---

## 🏅 Built By

**Hafsa Ouajdi**

- GitHub: [github.com/HafsaOuajdi](https://github.com/HafsaOuajdi)  
- Portfolio: [hafsaouaj.github.io/Portfolio_Hafsa](https://hafsaouaj.github.io/Portfolio_Hafsa)  
- Email: hafsa.ouajdi.fr@gmail.com  
```

