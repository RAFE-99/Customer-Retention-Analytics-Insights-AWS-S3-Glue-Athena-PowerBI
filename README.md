# 📊 Customer Retention Automated Pipeline (AWS S3 + AWS Glue + Athena + Power BI)

Welcome to the Customer Retention Automated Pipeline Project!  
This project is designed to analyze and understand customer churn patterns using modern cloud-based technologies. By leveraging AWS S3, AWS Glue, Amazon Athena, and Power BI, the pipeline provides an end-to-end solution for storing, processing, querying, and visualizing customer data.

![S3-Glue-Athena-PowerBi](https://github.com/user-attachments/assets/070c6d18-fa8c-4b5b-a0f2-c75652779cf9)

---


## 🚀 Project Overview
This project builds a data pipeline for analyzing customer churn using AWS services with Power BI as the visualization layer. The dataset contains customer demographics, subscription details, and churn indicators, helping identify why customers leave and which groups are most at risk.  
The solution leverages Amazon S3 as a central data lake, AWS Glue for schema inference and metadata management, and Amazon Athena for serverless SQL queries. Power BI connects to Athena through an ODBC driver, enabling business-ready dashboards and interactive churn insights.

---

## ✨ Features
- **Centralized Data Lake**: Amazon S3 stores raw and curated customer churn datasets for scalable and secure access. 🗂️  
- **Automated Schema Detection**: AWS Glue Crawlers dynamically infer schema and update the Glue Data Catalog. 🤖  
- **Serverless Querying**: Amazon Athena enables SQL-based churn analysis without managing infrastructure. ⚡  
- **Secure Access Control**: IAM Roles and Athena Workgroups ensure least-privilege access and cost governance. 🔐  
- **Interactive Dashboards**: Power BI delivers real-time churn insights, customer segmentation, and revenue analysis. 📊  
- **Future-Ready Extension**: Pipeline can be extended with AWS SageMaker for predictive churn modeling. 🔮  

---

## 🏛️ Architecture 
- 📥 **Data Ingestion** → Customer churn dataset uploaded into Amazon S3 (/raw/ and /curated/).  
- 📂 **Data Cataloging** → AWS Glue Crawler scans curated bucket and registers schema in Glue Data Catalog.  
- 🔎 **Query Layer** → Amazon Athena connects to the Glue Catalog to run SQL queries on S3 data.  
- 🔐 **Access Control** → IAM Roles & Workgroups manage security, query results, and permissions.  
- 📊 **Visualization** → Power BI connects to Athena (via ODBC) to build churn analytics dashboards.  

---

## 🔎 Components Description

### Amazon S3 - 🗄️
- **Function**: Amazon S3 is a scalable storage service that holds both raw and curated datasets. It ensures durability, security, and easy integration with other AWS services.  
- **Role in Pipeline**: It acts as the data lake, with `/raw/` storing the original Telco churn CSVs and `/curated/` holding cleaned data ready for analysis.  

### AWS Glue Crawler - 🤖
- **Function**: AWS Glue Crawler automatically scans datasets in S3 and detects their schema. It identifies data types, partitions, and column structures without manual effort.  
- **Role in Pipeline**: It keeps the metadata updated in the Glue Data Catalog so Athena always has the latest schema for querying curated datasets.  

### AWS Glue Data Catalog - 📚
- **Function**: The Glue Data Catalog is a centralized metadata repository that stores table structures, partitions, and schema definitions. It eliminates the need for repeated schema creation.  
- **Role in Pipeline**: It provides Athena with the schema layer needed to interpret S3 data, making queries seamless and consistent across datasets.  

### Amazon Athena - 🔎
- **Function**: Amazon Athena is a serverless SQL query engine that enables direct querying of S3 data without data movement. It allows analysts to create reusable views for reporting and analysis.  
- **Role in Pipeline**: It performs the actual churn analysis by querying datasets from S3 (via the Glue Catalog) and preparing views such as churn rate, tenure segmentation, and revenue impact.  

### IAM Roles & Workgroup - 🔐
- **Function**: IAM Roles provide secure access control, ensuring services only perform permitted actions. Athena Workgroups manage query execution, permissions, and cost tracking.  
- **Role in Pipeline**: They secure the pipeline by granting Glue access to crawlers/catalogs and Athena access to S3/Glue, while workgroups help organize and monitor queries.  

### Power BI (via ODBC) - 📊
- **Function**: Power BI is a visualization and business intelligence tool that creates interactive dashboards and reports. It connects to Athena through the ODBC driver to fetch live data.  
- **Role in Pipeline**: It serves as the presentation layer, displaying churn metrics, customer segments, and revenue risks in dashboards for business teams and decision-makers.  

---

## ⚙️ Setup Instructions

### ✅ Prerequisites
- AWS Account with S3, Glue, and Athena enabled. ☁️  
- IAM roles with least-privilege permissions. 🔐  
- Amazon Athena ODBC Driver installed locally. 🖥️  
- Power BI Desktop installed. 📊  

### 🛠️ Steps
1. Upload data → Place Telco churn CSV in S3 `/raw/` bucket.  
2. Create curated bucket → Store processed datasets in `/curated/`.  
3. Configure Glue Crawler → Point to `/curated/` and run to register schema.  
4. Validate in Data Catalog → Ensure table metadata is created.  
5. Setup Athena Workgroup → Assign query result location in S3.  
6. Run SQL queries → Create churn-related Athena views.  
7. Install ODBC Driver → Configure DSN with AWS region + workgroup.  
8. Connect Power BI → Import Athena views as datasets.  
9. Build dashboards → Visualize churn KPIs, segments, and revenue loss.  

---

## 📊 Dataset
- 📂 **Source**: Kaggle – Telco Customer Churn  
- 📄 **File**: Telco Customer Churn (CSV)  
- 📑 **Fields**: `customerID`, `gender`, `tenure`, `InternetService`, `PaymentMethod`, `MonthlyCharges`, `TotalCharges`, `Churn`  
- 📐 **Target Schema**: Registered as an external table using Glue Catalog.  

---

## 🎨 Visualization (Power BI Dashboards)
- 📉 **Churn Rate (%)** – Compare Churned vs Retained customers.  
- 📜 **Churn by Contract Type** – Shows higher churn in month-to-month contracts.  
- 🛡️ **Churn by Services** – Displays how Security & Tech Support reduce churn.  
- ⏳ **Tenure Segmentation** – Groups into loyalty bands (0–12, 13–24, etc.).  
- 📊 **Scatter Analysis** – Plots monthly spend vs tenure to find at-risk high-value customers.  

---
