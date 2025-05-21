🛒 Retail ETL Pipeline with Apache Airflow + dbt + BigQuery
============================================================

An end-to-end data engineering project for processing retail transaction data using Apache Airflow. This pipeline automates the loading of CSV data to Google Cloud Storage (GCS), transforms it with dbt and BigQuery, and includes optional data quality checks via Soda.

📦 Project Overview
-------------------
This project demonstrates a modern ETL pipeline using:

- Apache Airflow for orchestration
- Google Cloud Storage (GCS) for raw data staging
- BigQuery for data warehousing
- dbt (data build tool) for SQL transformations
- Soda for data quality validation

🧭 Architecture Diagram
------------------------

[CSV File] 
    ↓
[Upload to GCS]
    ↓
[BigQuery Staging]
    ↓
[dbt Transformations] → [Analytics Tables]
           ↓
      [Soda Scan]
           ↓
 [Airflow DAG Monitoring]

🗂️ Project Structure
---------------------
pipeline-airflow/
├── dags/retail.py                 # Main DAG with Astro SDK and GCP operators
├── include/                       # dbt and dataset files
│   └── soda/                      # Data quality checks
├── docker-compose.override.yml   # Local Airflow orchestration
├── airflow_settings.yaml         # Connections and variables setup
├── requirements.txt              # Python dependencies
├── Dockerfile                    # Airflow image setup
└── tests/                        # Test structure

🚀 How It Works
----------------
1. Upload Task: A CSV file is uploaded to GCS using LocalFilesystemToGCSOperator.
2. Create Dataset: A BigQuery dataset is created (if needed).
3. dbt: SQL models are transformed from staging to final tables.
4. Optional: Soda scan validates data quality and schema integrity.

⚙️ Technologies Used
---------------------
- Apache Airflow
- Google Cloud (GCS, BigQuery)
- dbt
- Soda
- Docker + Docker Compose

🧪 Running Locally
-------------------
```bash
# Step 1: Clone repo
git clone https://github.com/CiciDing-0814/pipeline-airflow.git
cd pipeline-airflow

# Step 2: Launch Airflow locally
docker-compose up --build

# Step 3: Access Airflow UI at localhost:8080
