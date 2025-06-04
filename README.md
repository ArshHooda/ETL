# 🌍 Earthquake ETL Pipeline on Azure

Welcome to the **Earthquake Data Pipeline** project! This solution implements a scalable, end-to-end ETL pipeline on **Microsoft Azure** to process live earthquake data from the **USGS Earthquake API** using a **medallion architecture** pattern.

---

## 🚀 Overview

This pipeline fetches, transforms, and stores seismic event data in Azure Data Lake using three structured layers:

🔹 **Bronze** → Raw Data  
🔸 **Silver** → Cleaned Data  
🔶 **Gold** → Enriched Data

Technologies used include **Azure Databricks**, **PySpark**, and **reverse_geocoder** for geolocation tagging.

---

## 🏗️ Pipeline Architecture


USGS API 🌐

↓

Bronze Layer 📦 (Raw JSON)

↓

Silver Layer 🧹 (Cleaned Parquet)

↓

Gold Layer ✨ (Enriched CSV + Metadata)



---

## 🥇 Medallion Layer Details

### 🥉 Bronze (Raw Layer)
- 📥 Extracts raw earthquake JSON from the [USGS API](https://earthquake.usgs.gov/fdsnws/event/1/).
- 💾 Stores data in **ADLS Gen2** under `bronze/` container.

### 🥈 Silver (Cleaned Layer)
- 🧽 Transforms raw JSON into structured schema.
- 🛠️ Cleans missing values, converts timestamps.
- 💾 Stores as **Parquet** in `silver/` container.

### 🥇 Gold (Enriched Layer)
- 🗺️ Adds geolocation using `reverse_geocoder`.
- 📊 Classifies earthquakes by significance (`Low`, `Moderate`, `High`).
- 💾 Stores final **CSV** data in `gold/` container.

---

## 🧰 Technologies Used

| Tool / Service        | Purpose                        |
|-----------------------|--------------------------------|
| ⚡ Databricks         | Orchestration & Spark compute |
| 🧊 ADLS Gen2          | Scalable storage for all layers |
| 🌍 USGS API           | Earthquake data source        |
| 🐍 PySpark + Python   | ETL & UDF logic               |
| 📍 reverse_geocoder   | Country code enrichment       |

---

## ⚙️ Setup & Execution

### ✅ 1. Prerequisites
- ✔️ Azure Databricks workspace
- ✔️ ADLS Gen2 with containers:
  - `bronze` → Raw JSON
  - `silver` → Cleaned Parquet
  - `gold` → Enriched CSV
- ✔️ Databricks cluster with:
  - PySpark
  - `reverse_geocoder` Python lib installed

---

### ▶️ 2. Running the Pipeline

#### 🟤 Bronze Notebook
- 📅 Input: `start_date`, `end_date` (YYYY-MM-DD)
- 📂 Output: Raw JSON files → `bronze/`

#### ⚪ Silver Notebook
- 🔄 Input: Reads from Bronze layer
- 📂 Output: Cleaned Parquet → `silver/`

#### 🟡 Gold Notebook
- 🔄 Input: Reads from Silver layer
- 🌐 Enrichment: Adds location + tags magnitude
- 📂 Output: Enriched CSV → `gold/`

---

## 📈 Example Use Case
Build real-time dashboards in **Power BI** or **Synapse Analytics** using the Gold layer to:
- 🗺️ Map earthquake hotspots
- 📉 Track seismic trends
- 🚨 Set up alerts for high-risk zones

