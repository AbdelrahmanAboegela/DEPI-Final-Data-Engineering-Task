
# DEPI-Final-Data-Engineering-Task

DEPI-Final-Data Engineering-Task is an end-to-end project utilizing Azure cloud services to build data pipelines. The project focuses on data ingestion, transformation, and storage, leveraging Azure Data Factory, Databricks, and Synapse Analytics to deliver secure, scalable, and efficient data solutions.

## Table of Contents
- [Overview](#overview)
- [Technologies Used](#technologies-used)
- [Installation](#installation)
- [Usage](#usage)
  - [Data Ingestion](#data-ingestion)
  - [Data Transformation](#data-transformation)
  - [Data Loading and Reporting](#data-loading-and-reporting)
- [Automation and Monitoring](#automation-and-monitoring)
- [Security and Governance](#security-and-governance)
- [Credits](#credits)

## Overview

This project addresses a critical business need by building a comprehensive data pipeline on Azure. The goal is to extract customer and sales data from an on-premises SQL database, transform it in the cloud, and generate actionable insights through a Power BI dashboard. The dashboard will highlight key performance indicators (KPIs) related to gender distribution and product category sales, allowing stakeholders to filter and analyze data by date, product category, and gender.

## Technologies Used

- **Azure Data Factory (ADF)**: For orchestrating data movement and transformation.
- **Azure Data Lake Storage (ADLS)**: For storing raw and processed data.
- **Azure Databricks**: For data transformation and processing.
- **Azure Synapse Analytics**: For data warehousing and SQL-based analytics.
- **Power BI**: For data visualization and reporting.
- **Azure Key Vault**: For securely managing credentials and secrets.
- **SQL Server (On-Premises)**: Source of customer and sales data.

## Installation

To set up this project, follow the steps below:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/AbdelrahmanAboegela/DEPI-Final-Data-Engineering-Task
   cd DEPI-Final-Data-Engineering-Task
   ```
2. **Set up the Azure environment**:
   - Create an Azure Data Factory instance.
   - Set up Azure Data Lake Storage with bronze, silver, and gold containers.
   - Create Azure Databricks and Azure Synapse Analytics workspaces.
   - Configure Azure Key Vault for secret management.

## Usage

### Data Ingestion
   Extract customer and sales data from the on-premises SQL database using ADF. Load the data into the bronze layer in ADLS.
   ```bash
   Execute ADF pipeline for data ingestion
   ```

### Data Transformation
   Clean and aggregate the data in Databricks, progressing it through bronze, silver, and gold layers.
   ```bash
   Use Databricks notebooks for data transformation
   ```

### Data Loading and Reporting
   Load transformed data into Azure Synapse Analytics. Build Power BI dashboards to visualize KPIs based on the transformed data.
   ```bash
   Build Power BI dashboard for insights
   ```

## Automation and Monitoring
- Schedule the pipelines to run daily using Azure Data Factory.
- Monitor the data pipelines with built-in monitoring tools in ADF and Synapse.

## Security and Governance
- Set up role-based access control (RBAC) using Azure Entra ID (formerly Azure Active Directory) to manage data access and security.

## Credits

This project was completed as part of my learning in the Data Engineering track. I would like to acknowledge the following resources and contributors:

- **Microsoft Azure Documentation**: For providing detailed guides on Azure services.
- **Online tutorials and courses**: For knowledge and best practices in setting up the data pipeline.
