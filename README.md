# MegaCart End-to-End Azure Data Pipeline

An enterprise-grade Data Engineering pipeline designed to process transactional retail data using the **Medallion Architecture** on Microsoft Azure.

## 📐 Architecture Diagram
*(Upload your architecture image to GitHub and replace this line with the image link)*

## 🛠️ Tech Stack & Azure Ecosystem
- **Orchestration:** Azure Data Factory (ADF)
- **Storage:** Azure Data Lake Storage Gen2 (ADLS)
- **Processing Engine:** Azure Databricks (Apache Spark / PySpark)
- **Storage Format:** Delta Lake (with ACID compliance and Transaction Logs)
- **BI & Analytics:** Power BI Desktop

## 🔄 Data Pipeline Flow (Medallion Architecture)

1. **Data Ingestion (Bronze Layer):** Raw operational CSV records are loaded into the storage layer. (Automated using ADF integration pipelines).
2. **Data Transformation & Cleaning (Silver Layer):** PySpark scripts running on Databricks clean the data by performing:
   - Deduplication using `dropDuplicates(["CustomerId"])`
   - Explicit Schema Enforcement via `cast()` for data types (Integer, Date).
3. **Data Aggregation (Gold Layer):** Cleansed profiles are structured and optimized for business needs using analytical aggregations (`groupBy("City").count()`) and stored as high-performance **Delta Tables**.
4. **Analytics Consumption:** Power BI connects directly to the Gold Delta Tables via authenticated Storage Keys to display interactive insights on regional customer concentrations across 300+ cities.

## 🚀 Key Features Demonstrated
- Implementation of modern Lakehouse Architecture.
- Storage-to-Compute isolation and secure inline configuration management.
- Analytical data modeling optimized for instantaneous dashboard rendering.
