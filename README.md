# 📊 Credit Card Transaction Analysis for Fraud Risk
[![GitHub Repo](https://img.shields.io/badge/GitHub-Repository-blue?logo=github)](https://github.com/Somanshu693/Credit-Card-Transaction-Analysis-For-Fraud-Risk)
[![Credit Card Transactions CICD](https://github.com/Somanshu693/Credit-Card-Transaction-Analysis-For-Fraud-Risk/actions/workflows/ci-cd.yaml/badge.svg)](https://github.com/Somanshu693/Credit-Card-Transaction-Analysis-For-Fraud-Risk/actions/workflows/ci-cd.yaml)

An end-to-end **data pipeline project** that analyzes daily credit card transactions to assess **fraud risk**. It uses **PySpark** on **GCP Dataproc Serverless**, orchestrated by **Airflow**, with results stored in **BigQuery** for analytics. **Unit testing** is implemented with **PyTest** to ensure code reliability, and automated **CI/CD pipelines** using **GitHub Actions** manage seamless deployments across development and production environments. Final analytics and dashboards are built using **Looker Studio** for interactive reporting.

---

## 🚀 Workflow Overview

### Architecture:
![Credit Card Transaction Analysis for Fraud Risk (1)](https://github.com/user-attachments/assets/93cb36b2-4d11-4465-bba7-c2045aa7047a)

### Unit Testing:

#### Failed:
![Unit Test Failed](https://github.com/user-attachments/assets/a9724bc1-e039-4d7b-9308-336304ac6208)

#### Passed:
![Unit Test Passed](https://github.com/user-attachments/assets/938aa963-8e16-441c-bf77-ea2ff8790f6d)

### Airflow DAG:
![Airflow DAG](https://github.com/user-attachments/assets/fe082eb2-0364-478b-9d4e-4c0f63b7510e)
![Airflow DAG](https://github.com/user-attachments/assets/af7e9170-afcd-49f0-8c4b-b5c955fdfdf0)

### BigQuery Table:
![BQ Table](https://github.com/user-attachments/assets/1fa5ffef-c605-49e2-aeec-7c4923214d78)


---

## 🧱 Folder Structure
```
├── .github/
|  ├── workflows/
|      ├── ci-cd.yaml                         # GitHub Actions CI/CD pipeline
├── airflow_job/
|      ├── airflow_job.py                     # Airflow DAG definition
├── spark_job/
|      ├── spark_job.py                       # PySpark transformation script
├── tests/
|      ├── test_transactions_processing.py    # Unit testing script
├── data/                                     # Sample credit card transaction dataset
|      ├── cardholders.csv
|      ├── transactions.json
├── requirements.txt                          # Required dependencies                                               
├── README.md                                 # Project documentation
```

---

## ⚙️ Tech Stack
| Component       | Tool/Service           |
| --------------- | ---------------------- |
| Data Processing | PySpark                |
| Orchestration   | GCP Composer (Airflow) |
| Storage & ETL   | Google Cloud Storage   |
| Compute Engine  | Dataproc Serverless    |
| Data Warehouse  | Google BigQuery        |
| Testing         | PyTest                 |
| CI/CD           | GitHub Actions         |
| Version Control | Git & GitHub           |
| Dashboarding    | Looker Studio          |

---

## 🔍 Execution Logic
- **Initialize:** Load static Card Holders data into BigQuery.
- **Ingestion:** Airflow senses new daily transaction JSON files in GCS.
- **Processing:** DAG triggers PySpark job on Dataproc:
  - Reads Card Holders info from BigQuery
  - Reads transactional data from GCS
  - Applies data validations & fraud risk transformations
- **Load:** Results are saved back into BigQuery.
- **Archive:** On success, moves processed JSON files to archive/ in GCS.
- **CI/CD Pipeline:**
   - Push triggers GitHub Action
   - Runs unit tests via PyTest
   - Deploys updated DAG and Spark scripts to GCS

---

## 🌟 Key Features
- **Fraud Risk Analysis:** Calculates risk scores for each transaction using PySpark.  
- **Serverless Data Processing:** Runs jobs efficiently on GCP Dataproc Serverless.  
- **Automated Workflow:** Airflow DAG automatically picks up new data.  
- **Data Validation:** Ensures transactional data integrity before analysis.  
- **CI/CD & Testing:** PyTest unit tests and GitHub Actions for automatic deployment.  
- **Interactive Dashboard:** Built using Looker Studio for real-time insights and reporting.

---

## 📈 Business Use Case
Credit card fraud is a major challenge for financial institutions and digital payment providers. This project simulates a real-world industrial pipeline designed to analyze and score transactional data for fraud risk, enabling:

- **Fraud teams** to automatically flag high-risk transactions based on configurable scoring logic.
- **Risk and compliance teams** to monitor anomalies and generate audit-ready reports.
- **Business analysts** to gain insights into fraud trends through interactive dashboards in Looker Studio.
- **Data scientists** to leverage enriched transaction data for training fraud detection models.
- **Operations teams** to benefit from automated, serverless data processing with Airflow and Dataproc.
- **Audit & governance teams** to maintain traceability via archived data and logs.

---
