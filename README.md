# Azure Data Factory – Dynamic Fact File Processing Pipeline

## Project Overview

This project demonstrates an end-to-end Azure Data Factory (ADF) pipeline that dynamically processes source files whose names begin with **"Fact"**, applies data transformations using **Mapping Data Flow**, and stores the processed data in a destination container. The pipeline is fully automated and can be executed on a schedule using ADF Triggers.

---

## Objective

Build a dynamic ETL pipeline that:

* Reads files from an Azure Blob Storage source container.
* Identifies only files whose names start with **"Fact"**.
* Processes multiple matching files automatically.
* Applies basic data transformations.
* Writes the transformed data to a destination container.
* Supports automated execution through ADF Triggers.

---

## Architecture

```
Source Container
       │
       ▼
Get Metadata
       │
       ▼
ForEach (Iterate Files)
       │
       ▼
If Condition (Filename starts with "Fact")
       │
      True
       │
       ▼
Copy / Pass Dynamic File Name
       │
       ▼
Mapping Data Flow
       │
       ▼
Destination Container
       │
       ▼
Trigger (Scheduled Execution)
```

---

## Azure Services Used

| Service               | Purpose                                               |
| --------------------- | ----------------------------------------------------- |
| Azure Data Factory    | Pipeline orchestration                                |
| Azure Blob Storage    | Source and destination storage                        |
| Get Metadata Activity | Retrieves the list of files from the source container |
| ForEach Activity      | Iterates through all files dynamically                |
| If Condition Activity | Filters files based on filename prefix ("Fact")       |
| Parameters            | Dynamically passes the selected filename              |
| Mapping Data Flow     | Performs basic data transformations                   |
| Trigger               | Automates pipeline execution                          |

---

## Pipeline Workflow

### 1. Get Metadata

Retrieves the list of files available in the source Azure Blob Storage container.

### 2. ForEach Activity

Iterates through every file returned by the Get Metadata activity.

### 3. If Condition

Checks whether the current filename starts with **"Fact"**.

* **True:** Process the file.
* **False:** Skip the file.

### 4. Dynamic Parameter Passing

The selected filename is passed dynamically to the pipeline, allowing the solution to process any matching file without hardcoding file names.

### 5. Mapping Data Flow

Basic transformations were implemented, including:

* Column selection
* Column renaming
* Row filtering
* Conditional branching
* Data aggregation
* Alter Row transformation

### 6. Sink

The transformed data is written into the destination Azure Blob Storage container.

### 7. Trigger

The pipeline can be executed automatically using Azure Data Factory Triggers.

---

## Key Features

* Dynamic file processing
* Filename-based filtering
* Automated iteration using ForEach
* Parameterized pipeline design
* Basic ETL transformations with Mapping Data Flow
* Automated execution through Triggers
* End-to-end Azure Data Factory implementation

---

## Learning Outcomes

Through this project, I gained hands-on experience with:

* Azure Data Factory pipeline development
* Azure Blob Storage integration
* Dynamic pipeline parameterization
* Metadata-driven processing
* ForEach and If Condition activities
* Mapping Data Flow transformations
* Trigger-based pipeline automation
* Designing a basic ETL workflow in Azure

---

This project represents my **practical Azure Data Factory implementation**, where I built a dynamic ETL pipeline using metadata-driven orchestration, conditional processing, parameterization, and Mapping Data Flows to automate the ingestion and transformation of source files. It served as a hands-on introduction to building scalable data integration pipelines in Azure.
