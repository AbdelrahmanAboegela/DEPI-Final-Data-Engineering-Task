# DEPI-Final-Data-Engineering-Task

This project showcases an end-to-end data engineering pipeline built on Azure cloud services. The project focuses on data ingestion, transformation, and storage, leveraging services such as Azure Data Factory, Azure Databricks, Azure Synapse Analytics, and Power BI for visualization.

## Project Structure

The project is organized into the following components:

- **Azure Key Vault (KV)**: Used to manage secrets, such as credentials for accessing data sources and services.
- **Azure Data Lake Storage (DLG2)**: Scalable storage for raw, cleansed, and transformed data.
- **Azure Data Factory (DF)**: For orchestrating data workflows, including data movement and triggering Databricks notebooks.
- **Azure Databricks (DB)**: Used for data processing and transformation (bronze-to-silver and silver-to-gold transformations).
- **Azure Synapse Analytics (S_PL & S_VP)**: For data warehousing and running queries on the processed data.
- **Power BI**: Used to create interactive reports and dashboards.

## Prerequisites

Before setting up the project, ensure that you have:

- An Azure subscription with appropriate permissions.
- Access to Azure Data Factory, Azure Databricks, Azure Synapse Analytics, and Power BI.
- Basic understanding of Azure services and data engineering concepts.
- SQL Server instance for AdventureWorksLT2017 database.

## Getting Started

### 1. Download and Restore AdventureWorksLT2017 Database

1. **Download the Database**: Obtain the AdventureWorksLT2017 database from [this link](https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver16).
2. **Restore the Database**: Follow the instructions on the download page to restore the database to your SQL Server instance.

### 2. Create Resource Group

1. In the **Azure Portal**, search for **Resource Groups**.
2. Click on **Create**, choose your subscription, and name the resource group (e.g., DEPI-ResourceGroup).
3. Choose a **Region** and click **Review + Create**.

### 3. Azure Data Factory (DF) Setup

Azure Data Factory orchestrates data movement and workflow automation, including running Databricks notebooks for data transformations.

1. **Create a Data Pipeline**:
   - Navigate to **ADF Studio** via **Azure Portal**.
   - Click on **Author & Monitor** and create a **New Pipeline**.
   - Add activities like **Copy Data**, **Data Flow**, and **Lookup** to define data movement and transformations.
   
2. **Configure Linked Services**:
   - Go to **Manage** and create linked services for **SQL Server** and **ADLS**.
   
3. **Trigger Databricks Notebooks**:
   - Add a **Databricks Notebook Activity** to trigger the bronze-to-silver and silver-to-gold transformations.

**DF Pipeline:**
![DF Pipeline](C:/Users/0king/Desktop/Depi Task/DF.png)

**DF Pipeline Run (DF_PLR):**
![DF Pipeline Run](C:/Users/0king/Desktop/Depi Task/DF_PLR.png)

### 4. Azure Databricks (DB) Setup

1. **Create Databricks Workspace**:
   - Create a Databricks workspace in the **Azure Portal** and configure it.

2. **Create and Configure Clusters**:
   - Navigate to **Clusters**, set the VM size, and enable auto-scaling.
   
3. **Create Python Notebooks**:
   - Develop PySpark notebooks for bronze-to-silver and silver-to-gold transformations.
   
4. **Integrate with ADF**:
   - Link these notebooks to your ADF pipeline.

**Databricks Workspace Setup (DB):**
![Databricks Setup](C:/Users/0king/Desktop/Depi Task/DB.png)

### 5. Azure Data Lake (DLG2) Setup

1. **Create Storage Account**:
   - Go to **Storage Accounts** and create a new account (e.g., depidatalake).
   
2. **Create Containers**:
   - Create containers for **bronze**, **silver**, and **gold** layers to store raw, cleansed, and processed data.

**Data Lake Containers (DLG2):**
![Data Lake Containers](C:/Users/0king/Desktop/Depi Task/DLG2.png)

### 6. Azure Synapse Analytics (S_PL & S_VP) Setup

1. **Create Synapse Workspace**:
   - Set up a Synapse workspace and link it to your data lake.
   
2. **Create SQL Pools**:
   - Set up SQL pools to run serverless queries on processed data.

3. **Run Queries**:
   - Execute SQL queries for analytics and create views.

**Synapse Pipeline (S_PL):**
![Synapse Pipeline](C:/Users/0king/Desktop/Depi Task/S_PL.png)

**Synapse View Procedure (S_VP):**
![Synapse View Procedure](C:/Users/0king/Desktop/Depi Task/S_VP.png)

### 7. Azure Key Vault (KV) Setup

1. **Create Key Vault**:
   - In the **Azure Portal**, create a Key Vault to store credentials securely.

2. **Use Key Vault for Secrets**:
   - Store credentials such as SQL Server connection strings, ADLS keys, etc.

**Key Vault Secrets (KV):**
![Key Vault](![KV](https://github.com/user-attachments/assets/75878969-83c3-45db-b3da-23c45c5dd174))

### 8. Power BI Setup

1. **Connect Power BI to Synapse**:
   - Use Power BI Desktop to connect to Azure Synapse for visualization.
   
2. **Create Interactive Reports**:
   - Build dashboards and reports on KPIs such as sales by product category and gender.

3. **Publish Reports**:
   - Publish to **Power BI Service** for sharing and collaboration.


## Conclusion

This repository provides a detailed guide for setting up an end-to-end Azure data engineering pipeline. The project integrates Azure Data Factory, Databricks, Synapse Analytics, and Power BI to deliver a complete data solution.

