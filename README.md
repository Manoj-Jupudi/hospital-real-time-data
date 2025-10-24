# Real-Time Patient Flow Analytics on Azure

![Azure](https://img.shields.io/badge/Azure-Cloud-blue?logo=microsoft-azure&style=flat-square)
![PySpark](https://img.shields.io/badge/PySpark-Big%20Data-orange?logo=apache-spark&style=flat-square)
![Azure Data Factory](https://img.shields.io/badge/Azure-Data%20Factory-blue?logo=microsoft-azure&style=flat-square)
![Azure Synapse](https://img.shields.io/badge/Azure-Synapse%20Analytics-blue?logo=microsoft-azure&style=flat-square)
![Python](https://img.shields.io/badge/Python-3.9+-yellow?logo=python&style=flat-square)
![Databricks](https://img.shields.io/badge/Databricks-PySpark-red?logo=databricks&style=flat-square)
![Git](https://img.shields.io/badge/Git-CI%2FCD-green?logo=git&style=flat-square)



## 📌 Project Overview
This project demonstrates a **real-time data engineering pipeline** for healthcare, designed to analyze **patient flow across hospital departments** using Azure cloud services.  

## Pipeline

<img width="4719" height="2432" alt="Architecture" src="https://github.com/user-attachments/assets/cb1a1775-ab64-45d7-b45b-50ba97660e1d" />


---

## 🎯 Objectives
- Collect real-time patient data via **Azure Event Hub**.
- Process and cleanse data using **Databricks** (Bronze → Silver → Gold layers).
- Implement a **star schema** in **Synapse SQL Pool** for efficient querying.
- Enable **Version Control** with Git.

---

## 🛠️ Tools & Technologies
- **Azure Event Hub** – Real-time data ingestion
- **Azure Databricks** – PySpark-based ETL processing
- **Azure Data Lake Storage** – Staging raw and curated data
- **Azure Synapse SQL Pool** – Data warehouse for analytics
- **Python 3.9+** – Core programming
- **Git** – Version control

---

## 📐 Data Architecture
The pipeline follows a **multi-layered architecture**:
- **Bronze Layer**: Raw JSON data from Event Hub stored in ADLS.
- **Silver Layer**: Cleaned and structured data (validated types, null handling).
- **Gold Layer**: Aggregated and transformed data ready for BI consumption.

---

## ⭐ Star Schema Design
The **Gold layer** data in Synapse follows a **star schema** for optimized analytics:
- **Fact Table**: `FactPatientFlow` (patient visits, timestamps, wait times, discharge)
- **Dimension Tables**:
  - `DimDepartment` – Department details
  - `DimPatient` – Patient demographic info
  - `DimTime` – Date and time dimension

---

## ⚙️ Step-by-Step Implementation

### **1. Event Hub Setup**
- Created **Event Hub namespace** and **patient-flow hub**.
- Configured **consumer groups** for Databricks streaming.

---

### **2. Data Simulation**
- Developed **Python script** `patient_flow_generator.py` to stream fake patient data (departments, wait time, discharge status) to Event Hub.
- [Producer Code](simulator/patient_flow_generator.py)

---

### **3. Storage Setup**
- Configured **Azure Data Lake Storage (ADLS Gen2)**.
- Created containers for **bronze**, **silver**, and **gold** layers.

---

### **4. Databricks Processing**
- [**Notebook 1**](databricks-notebooks/01_bronze_rawdata.py): Reads Event Hub stream into Bronze.
- [**Notebook 2**](databricks-notebooks/02_silver_cleandata.py): Cleans and validates schema.
- [**Notebook 3** ](databricks-notebooks/03_gold_transform.py): Aggregates and prepares star schema tables.

---

### **5. Synapse SQL Pool**
- Created **dedicated SQL Pool**.
- Executed schema and fact/dimension creation queries from:
  - [DDL_Qureis](sqlpool-quries/SQL_pool_quries.sql)

---

### **6. Version Control**
- Version control with **Git**:
  - [Commands reference](git_commands/git_bash)

---


## ✅ Key Outcomes
- **End-to-End Pipeline:** From **real-time ingestion → transformation → warehouse → analytics**.  
- **Scalable Architecture:** Easily adaptable for different hospital datasets.  
- **Business Insights:** Hospital admins can monitor **bed usage, patient flow, and department efficiency** in real time.  
- **Portfolio Value:** Demonstrates  **Data Engineering** skills in this  project.  
