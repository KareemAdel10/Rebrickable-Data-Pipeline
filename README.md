# Rebrickable Data Ingestion Pipeline
---
The **Rebrickable Data Pipeline project** is a comprehensive data ingestion system designed to securely ingest and process data from two distinct sources: **the Rebrickable LEGO Database** and **the Rebrickable User Database**.
This project leverages Azure Data Factory (ADF) to build and manage separate pipelines for each database, ensuring secure access control, daily automation, environment synchronization, and failure alerting.
# Project Goals
---
The primary objective is to establish a robust pipeline architecture to ingest, transform, and store data from **Rebrickable’s APIs** while maintaining strict security standards and operational efficiency.
# Architecture
--
![User_Dataset_pipeline](https://dev.azure.com/1900286/CI-CD/_git/Ingestion%20Task?path=/Images/Api%20Pipeline.png&version=GBsecondarybranch)
![LEGO_Database_pipeline](https://dev.azure.com/1900286/CI-CD/_git/Ingestion%20Task?path=/Images/Database%20pipeline.png&version=GBsecondarybranch)