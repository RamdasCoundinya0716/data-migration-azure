# Azure Cloud Data Migration Project

## 📌 Introduction
A cloud-based data migration project leveraging Azure Data Factory, Azure Databricks, Azure Synapse Analytics, and ADLS Gen2 to migrate, transform, and analyze data from on-prem MSSQL Server to Azure Cloud.

---

## 🛠️ Tech Stack Used
- **Azure Data Factory (ADF)**
- **Azure Databricks (PySpark)**
- **Azure Synapse Analytics (SQL Data Warehouse)**
- **Azure Data Lake Storage Gen2 (ADLS Gen2)**
- **MSSQL Server (Docker)**
- **SQL Server Management Studio (SSMS)**
- **Python**

---

## 📊 Architecture Diagram
               +----------------------+
               |   On-Prem MSSQL       |
               |   Server (Docker)     |
               |   AdventureWorks      |
               +----------+-----------+
                          |
                          | 
               +----------v-----------+
               |  SQL Server           |
               |  Management Studio    |
               +----------+-----------+
                          |
                          |
             +------------v------------+
             |  Azure Data Factory      |
             |  Integration Runtime     |
             +------------+------------+
                          |
               (8-9 Tables Ingested)   
                          |
             +------------v------------+
             | Azure Data Lake Storage  |
             |       Gen2 (Bronze)      |
             +------------+------------+
                          |
           (Mounted in Azure Databricks)
                          |
             +------------v------------+
             |  Azure Databricks        |
             |  (Data Transformation)   |
             |  - Timestamp Conversion  |
             |  - Column Standardization|
             +------------+------------+
                          |
             +------------v------------+
             | Azure Data Lake Storage  |
             |       Gen2 (Gold)        |
             +------------+------------+
                          |
                          |
             +------------v------------+
             | Azure Synapse Analytics  |
             | (SQL Data Warehouse)     |
             +-------------------------+

             
---

## 📑 Steps Involved
1. **Setup Docker Image of MSSQL Server** and load AdventureWorks sample data.
2. **Configure Azure Data Factory (ADF)** to ingest data from on-prem server to ADLS Gen2 (Bronze Layer).
3. **Mount ADLS Gen2 in Azure Databricks** and perform transformations:
   - Convert timestamp columns to `DATE`.
   - Standardize column names by removing spaces.
4. **Store transformed data in ADLS Gen2 (Gold Layer)** for further analysis.
5. **Set up Azure Synapse Analytics Warehouse** for querying transformed data.
6. Demonstrate familiarity with **Azure Functions, Azure Logic Apps, and Azure Data Explorer** for optimized querying.

---

## 💡 Challenges Faced & Solutions
- **Data Transformation Challenges in Azure Databricks:** Resolved by optimizing PySpark operations and using proper data formats.
- **Query Optimization in Azure Synapse Analytics:** Improved query efficiency by utilizing indexes and partitioning.
