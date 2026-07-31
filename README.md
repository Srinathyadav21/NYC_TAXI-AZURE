
# 🚖 NYC Taxi Data Engineering Pipeline on Azure

## 📌 Project Overview

This project demonstrates an end-to-end Azure Data Engineering pipeline that ingests **NYC Taxi trip data** from a public API, processes it using the **Medallion Architecture (Bronze, Silver, Gold)**, and stores the data in **Azure Data Lake Storage Gen2** using **Delta format**.

The pipeline is orchestrated using **Azure Data Factory**, where a **dynamic parameterized pipeline** processes data for **all 12 months of 2024** using a **ForEach** activity. Data transformations and aggregations are performed using **Azure Databricks (PySpark)**.

---

# 🏗️ Architecture

![Architecture](architecture/architecture.png)

### Data Flow

```
NYC Taxi API
      │
      ▼
Azure Data Factory
(Dynamic Pipeline - 2024)
(ForEach: Jan → Dec)
      │
      ▼
ADLS Gen2
Bronze Layer (Raw Data)
      │
      ▼
Azure Databricks (PySpark)
Data Cleaning & Validation
      │
      ▼
ADLS Gen2
Silver Layer (Clean Data)
      │
      ▼
Azure Databricks (PySpark)
Business Aggregations
      │
      ▼
ADLS Gen2
Gold Layer (Business Ready Data)
      │
      ▼
SQL Analytics / Power BI
```

---

# 🛠️ Technologies Used

| Service | Purpose |
|----------|---------|
| Azure Data Factory | Pipeline orchestration |
| Azure Data Lake Storage Gen2 | Data storage |
| Azure Databricks | Data processing |
| PySpark | Data transformations |
| Delta Lake | Transactional data storage |
| Azure | Cloud platform |
| Git & GitHub | Version control |

---

# 🔄 Pipeline Flow

### Step 1 — Data Ingestion

- Extract NYC Taxi data from Public API
- Dynamic pipeline for Year = 2024
- ForEach loop processes January to December
- Store raw data in Bronze layer

---

### Step 2 — Bronze Layer

- Store raw API data
- Delta format
- No transformations

---

### Step 3 — Silver Layer

Using Azure Databricks:

- Remove null values
- Standardize column names
- Data type conversions
- Data validation
- Clean dataset

Store processed data in Delta format.

---

### Step 4 — Gold Layer

Perform business transformations:

- Aggregations
- Trip analysis
- Business-ready datasets

Store final dataset in Delta format.

---

### Step 5 — Analytics

Gold layer can be consumed by:

- Power BI
- SQL Analytics
- Databricks SQL

---

# 📁 Project Structure

```
NYC_TAXI-AZURE/
│
├── adf/
│   ├── pipeline/
│   ├── dataset/
│   ├── linkedService/
│   └── factory/
│
├── databricks/
│   └── nyc_taxi.py
│
├── architecture/
│   └── architecture.png
│
├── screenshots/
│   ├── adf_pipeline.png
│   ├── bronze_layer.png
│   ├── silver_layer.png
│   ├── gold_layer.png
│   └── databricks_notebook.png
│
├── sql/
│   └── analytics_queries.sql
│
└── README.md
```

---

# 📸 Screenshots

### Azure Data Factory Pipeline

![ADF Pipeline](screenshots/adf_pipeline.png)

---

### Bronze Layer

![Bronze](screenshots/bronze_layer.png)

---

### Silver Layer

![Silver](screenshots/silver_layer.png)

---

### Gold Layer

![Gold](screenshots/gold_layer.png)

---

### Databricks Notebook

![Notebook](screenshots/databricks_notebook.png)

---

# ▶️ How to Run

### Prerequisites

- Azure Subscription
- Azure Data Factory
- Azure Databricks
- Azure Data Lake Storage Gen2
- GitHub Repository

### Steps

1. Deploy Azure resources.
2. Configure Linked Services in Azure Data Factory.
3. Update storage credentials and API configuration.
4. Execute the ADF pipeline.
5. Verify Bronze, Silver, and Gold layers in ADLS.
6. Run SQL queries or connect Power BI to the Gold layer.

---

# 📈 Key Features

- Dynamic ADF Pipeline
- Parameterized Data Ingestion
- ForEach Activity
- Medallion Architecture
- Delta Format Storage
- Azure Databricks Transformations
- Business Aggregations
- GitHub Version Control

---

# 🚀 Future Improvements

- Incremental Data Loading
- Data Quality Validation Framework
- Delta Table Optimization (OPTIMIZE & VACUUM)
- CI/CD using Azure DevOps or GitHub Actions
- Azure Key Vault Integration
- Automated Monitoring & Alerts
- Power BI Dashboard
- Logging & Error Handling

---

# 👨‍💻 Author

**Srinath Yadav**

Azure Data Engineer

GitHub: https://github.com/Srinathyadav21

LinkedIn: *(Add your LinkedIn profile URL here)*

---
⭐ If you found this project useful, consider giving it a star!
