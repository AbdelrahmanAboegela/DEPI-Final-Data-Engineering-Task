# DEPI-Final-Data-Engineering-Task

This project demonstrates an end-to-end data engineering pipeline built on Azure cloud services. It focuses on data ingestion, transformation, and storage using services such as Azure Data Factory, Azure Databricks, Azure Synapse Analytics, and Power BI for visualization.

## Table of Contents

1. [Project Structure](#project-structure)
2. [Prerequisites](#prerequisites)
3. [Getting Started](#getting-started)
   - [Download and Restore AdventureWorksLT2017 Database](#1-download-and-restore-adventureworksl2017-database)
   - [Create Resource Group](#2-create-resource-group)
   - [Azure Data Factory Setup](#3-azure-data-factory-df-setup)
   - [Azure Databricks Setup](#4-azure-databricks-db-setup)
   - [Azure Data Lake Setup](#5-azure-data-lake-dlg2-setup)
   - [Azure Synapse Analytics Setup](#6-azure-synapse-analytics-s_pl-s_vp-setup)
   - [Azure Key Vault Setup](#7-azure-key-vault-kv-setup)
   - [Power BI Setup](#8-power-bi-setup)
4. [Conclusion](#conclusion)

---

## Project Structure

The project is organized into the following components:

- **[Azure Key Vault (KV)](https://azure.microsoft.com/en-us/services/key-vault/)**: Used to manage secrets, such as credentials for accessing data sources and services.
- **[Azure Data Lake Storage (DLG2)](https://azure.microsoft.com/en-us/services/storage/data-lake-storage/)**: Scalable storage for raw, cleansed, and transformed data.
- **[Azure Data Factory (DF)](https://azure.microsoft.com/en-us/services/data-factory/)**: For orchestrating data workflows, including data movement and triggering Databricks notebooks.
- **[Azure Databricks (DB)](https://azure.microsoft.com/en-us/services/databricks/)**: Used for data processing and transformation (bronze-to-silver and silver-to-gold transformations).
- **[Azure Synapse Analytics (S_PL & S_VP)](https://azure.microsoft.com/en-us/services/synapse-analytics/)**: For data warehousing and running queries on the processed data.
- **[Power BI](https://powerbi.microsoft.com/)**: Used to create interactive reports and dashboards.

---

## Prerequisites

Ensure that you have:

- An **[Azure subscription](https://azure.microsoft.com/en-us/free/)** with appropriate permissions.
- Access to **Azure Data Factory**, **Azure Databricks**, **Azure Synapse Analytics**, and **Power BI**.
- Basic understanding of **Azure services** and **data engineering concepts**.
- A **SQL Server instance** for the AdventureWorksLT2017 database.

---

## Getting Started

### 1. Download and Restore AdventureWorksLT2017 Database

1. **Download the Database**: Obtain the AdventureWorksLT2017 database from [this link](https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver16).
2. **Restore the Database**: Follow the instructions on the download page to restore the database to your SQL Server instance.

---

### 2. Create Resource Group

1. In the **[Azure Portal](https://portal.azure.com/)**, search for **Resource Groups**.
2. Click on **Create**, choose your subscription, and name the resource group (e.g., DEPI-ResourceGroup).
3. Choose a **Region** and click **Review + Create**.

---

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

![DF Pipeline](https://github.com/user-attachments/assets/859aa806-e925-4e98-8b7e-39b07cb0b100)

**DF Pipeline Run (DF_PLR):**

![DF Pipeline Run](https://github.com/user-attachments/assets/be8409ee-5795-4e23-8e4f-78efd2d660a0)

---

### 4. Azure Databricks (DB) Setup

1. **Create Databricks Workspace**:
   - Create a **Databricks workspace** in the **Azure Portal** and configure it.

2. **Create and Configure Clusters**:
   - Navigate to **Clusters**, set the VM size, and enable auto-scaling.
  
**Databricks Workspace Setup (DB):**

![Databricks Workspace Setup](https://github.com/user-attachments/assets/e9779ee9-32b8-4d69-ad13-710a122252d4)

3. **Create Python Notebooks**:
   - Develop PySpark notebooks for bronze-to-silver and silver-to-gold transformations.
   
4. **Integrate with ADF**:
   - Link these notebooks to your ADF pipeline.

---

### 5. Azure Data Lake (DLG2) Setup

1. **Create Storage Account**:
   - Go to **[Storage Accounts](https://azure.microsoft.com/en-us/services/storage/)** and create a new account (e.g., depidatalake).
   
2. **Create Containers**:
   - Create containers for **bronze**, **silver**, and **gold** layers to store raw, cleansed, and processed data.

**Data Lake Containers (DLG2):**

![Data Lake Containers](https://github.com/user-attachments/assets/a14a279a-2c8e-459d-8600-37f4db0791ac)

---

### 6. Azure Synapse Analytics (S_PL & S_VP) Setup

1. **Create Synapse Workspace**:
   - Set up a **[Synapse workspace](https://docs.microsoft.com/en-us/azure/synapse-analytics/quickstart-create-workspace)** and link it to your data lake.
   
2. **Create SQL Pools**:
   - Set up SQL pools to run serverless queries on processed data.

**Synapse Pipeline (S_PL):**

![Synapse Pipeline](https://github.com/user-attachments/assets/e01f737b-a5a9-45a7-9f86-970a5f497d91)

3. **Run Queries**:
   - Execute SQL queries for analytics and create views.

**Synapse View Procedure (S_VP):**

![Synapse View Procedure](https://github.com/user-attachments/assets/13f17009-817c-4cf4-a48d-85697166dddb)

---

### 7. Azure Key Vault (KV) Setup

1. **Create Key Vault**:
   - In the **Azure Portal**, create a **[Key Vault](https://azure.microsoft.com/en-us/services/key-vault/)** to store credentials securely.

2. **Use Key Vault for Secrets**:
   - Store credentials such as SQL Server connection strings, ADLS keys, etc.

**Key Vault Secrets (KV):**

![Key Vault](https://github.com/user-attachments/assets/74579a4d-10b3-4a3a-9532-2f0e5085f29c)

---

### 8. Power BI Setup

1. **Connect Power BI to Synapse**:
   - Use **[Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/)** to connect to **Azure Synapse** for visualization.
   
2. **Create Interactive Reports**:
   - Build dashboards and reports on KPIs such as sales by product category and gender.

3. **Publish Reports**:
   - Publish to **Power BI Service** for sharing and collaboration.

---

## Conclusion

This repository provides a comprehensive guide for setting up an end-to-end Azure data engineering pipeline. The project integrates Azure Data Factory, Databricks, Synapse Analytics, and Power BI to deliver a complete data solution.

By following these steps, you can replicate this setup in your environment and customize it to meet your business requirements.
