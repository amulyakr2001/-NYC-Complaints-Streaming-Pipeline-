# NYC-Complaints-Streaming-Pipeline

This project builds a scalable, cloud-native pipeline to analyze NYC 311 noise complaint data. The system leverages Google Cloud Platform (GCP) to ingest, process, store, and visualize data, providing insights into patterns of noise pollution across New York City.

---

## Project Objective

To identify and understand the trends in noise complaints reported to NYC’s 311 service. The analysis aims to uncover geographic hotspots, frequent noise types, and complaint resolution trends to support better urban planning and enforcement.

---

## Data Pipeline Overview

### 1. **Data Ingestion**
- **Cloud Functions**: Retrieves raw complaint data from the NYC Open Data API.
- **Cloud Pub/Sub**: Acts as the messaging layer to stream data into storage asynchronously.

### 2. **Data Storage**
- **Cloud Storage**: Stores raw and staged data.
- **BigQuery**: Stores processed datasets optimized for analysis and querying.

### 3. **Data Processing**
- **Dataproc + PySpark**: Transforms and cleanses large volumes of complaint data.

### 4. **Automation**
- **Cloud Scheduler**: Automates ingestion and transformation at scheduled intervals.

### 5. **Visualization**
- **Looker Studio**: Interactive dashboards created using BigQuery datasets.

---

##  Setup Instructions

### Step 1: Google Cloud Setup
- Create a GCP project and enable billing.
- Set up a new **Service Account** and download its credentials (`.json` file).
- Assign roles for BigQuery Admin, Storage Admin, Pub/Sub Publisher, and Cloud Functions Developer.

### Step 2: Provision GCP Services
- Create **Cloud Storage buckets** for raw and processed data.
- Deploy a **Dataproc cluster** to handle PySpark jobs.
- Set up a **BigQuery** dataset for transformed data.

### Step 3: Deploy Components
- **Cloud Functions**: Ingest data and publish messages to Pub/Sub.
- **Pub/Sub**: Acts as an event broker between ingestion and storage layers.
- **Dataproc Jobs**: Clean and transform data, outputting to BigQuery.
- **Cloud Scheduler**: Schedule Cloud Functions to run periodically.

### Step 4: Visualization
- Use **Looker Studio** to connect with BigQuery and build dashboards.
- Generate charts and reports to analyze borough-wise complaint distribution, noise types, and resolution timelines.

---

## 🧪 Problem Statement

This project aims to:
- Detect trends and high-frequency areas of noise complaints.
- Improve data reliability and make it suitable for large-scale querying.
- Visualize insights that help city planners and analysts address urban noise issues.

---

##  Dataset Overview

Data is sourced from NYC Open Data:  
🔗 [311 Service Requests from 2010 to Present](https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9/data_preview)

### Key Fields Used:
- `Unique Key`: Unique ID for each complaint
- `Created Date` / `Closed Date`: Complaint lifecycle
- `Complaint Type`, `Descriptor`: Type and details of the noise issue
- `Location Type`, `Incident Zip`, `City`, `Borough`: Geo-location info
- `Agency`, `Status`, `Resolution Description`: Response and outcomes
- `Latitude`, `Longitude`: For mapping complaints
- `Open Data Channel Type`: Source of complaint (Phone, Online, etc.)

---

##  Insights Derived
- **Residential noise** leads as the top complaint type.
- **Brooklyn** consistently registers the highest number of noise complaints.
- **Loud music/parties** are the most frequently reported disturbances.
- Complaints linked to **places of worship** are typically resolved faster than others.

---

##  GCP Services Breakdown

| Component         | Role                                                                 |
|------------------|----------------------------------------------------------------------|
| Cloud Functions   | Triggers data collection from NYC API                                |
| Pub/Sub           | Messaging between ingestion and storage                              |
| Cloud Storage     | Stores raw and transformed datasets                                  |
| Dataproc (PySpark)| Handles distributed data processing and transformation               |
| BigQuery          | Stores structured data for fast querying                             |
| Looker Studio     | Dashboards and visual exploration of complaint data                  |
| Cloud Scheduler   | Automates data flow and transformation jobs                          |

---

## 📌 Summary

This project demonstrates how to build a robust, cloud-native data pipeline for public datasets using Google Cloud. The end-to-end system offers automated ingestion, real-time transformation, scalable querying, and insightful visualization — all focused on understanding NYC's urban noise challenges.

