# 🏗️ Data Warehouse & Mart Build: Production ETL Pipeline

An end-to-end data engineering pipeline that transforms raw CSV files from Google Cloud Storage into a structured star schema data warehouse and builds specialised analytical data marts for business intelligence and reporting.

<img width="1620" height="768" alt="1_2_Project2_Data_Pipeline" src="https://github.com/user-attachments/assets/e55896e7-2c4a-4bc9-ad81-caf1e7fde924" />


---

## 📌 Executive Summary

- ✅ **Pipeline Scope:** Built an end-to-end ETL pipeline transforming raw CSV datasets into a structured data warehouse and analytical data marts.
- ✅ **Data Modelling:** Designed a star schema incorporating fact tables, dimension tables and bridge tables to manage complex data relationships.
- ✅ **ETL Development:** Implemented Extract, Transform and Load (ETL) processes with data validation, transformation and repeatable execution.
- ✅ **Data Mart Architecture:** Developed specialised analytical data marts for flat reporting, skill demand analysis and priority job tracking.
- ✅ **Incremental Processing:** Applied SQL MERGE operations to support incremental updates and efficient data maintenance.

---

## 🎯 Problem & Context

### Challenge

Organisations often manage large volumes of raw data across multiple sources, making it difficult to maintain consistent, accurate and accessible information for analytical reporting.

Without a centralised data warehouse, organisations may encounter data inconsistencies, duplicated processing, complex analytical queries and inefficient reporting.

### Solution

Designed an end-to-end data engineering solution that extracts CSV datasets from Google Cloud Storage, transforms the data using SQL and loads it into a structured star schema data warehouse.

The solution also incorporates specialised analytical data marts to simplify queries, organise business metrics and support data-driven decision-making.

---

## 🛠️ Tech Stack

| Category | Technologies |
|---|---|
| Database | DuckDB |
| Cloud Storage | Google Cloud Storage |
| Programming Language | SQL |
| Data Engineering | ETL, Data Integration, Data Transformation |
| Data Modelling | Star Schema, Fact Tables, Dimension Tables, Bridge Tables |
| Development Environment | Visual Studio Code, DuckDB CLI |
| Automation | Master SQL Pipeline Script |
| Version Control | Git, GitHub |
| Data Format | CSV |

---

## 🏗️ Pipeline Architecture
<img width="1620" height="768" alt="1_2_Project2_Data_Pipeline" src="https://github.com/user-attachments/assets/9933d9fd-4c24-496a-861d-d29c17d580fc" />



The pipeline transforms job posting CSV datasets from Google Cloud Storage into a structured data warehouse before generating specialised analytical data marts.

The resulting datasets are designed to support business intelligence, analytical reporting and integration with tools such as Excel, Power BI, Tableau and Python.

### 1. Data Warehouse

The centralised data warehouse uses a star schema with the following tables:

- `company_dim`
- `skills_dim`
- `job_postings_fact`
- `skills_job_dim`

<img width="1586" height="1254" alt="1_2_Data_Warehouse" src="https://github.com/user-attachments/assets/6c6a997f-80c8-4275-871e-63729547d2c2" />


**SQL Files:**

- `01_create_tables_dw.sql` — Defines the data warehouse schema and four core tables.
- `02_load_schema_dw.sql` — Extracts CSV datasets from Google Cloud Storage and loads them into warehouse tables.

**Purpose:** Establish a centralised, structured source of data for analytical queries.

**Grain:** One row per job posting in `job_postings_fact`.

### 2. Flat Mart

A denormalised analytical table that combines job posting data with related dimensions to simplify reporting.

<img width="1656" height="1248" alt="1_2_Flat_Mart" src="https://github.com/user-attachments/assets/e9f81018-1d3f-4cc2-8dbb-dee130215c0b" />


**SQL File:** `03_create_flat_mart.sql`

**Purpose:** Support ad-hoc analytical queries by reducing the need for repeated joins.

**Grain:** One row per job posting with related dimension attributes.

### 3. Skills Mart

A specialised analytical data mart designed to investigate technical skill demand and employment trends over time.

<img width="1644" height="728" alt="1_2_Skills_Mart" src="https://github.com/user-attachments/assets/5cb7c49d-cd67-4275-bef8-c6b5e1815630" />


**SQL File:** `04_create_skills_mart.sql`

**Purpose:** Analyse technical skill demand through time-series reporting.

**Grain:** `skill_id + month_start_date + job_title_short`

**Key Features:**

- Additive measures using counts and sums.
- Monthly aggregation of technical skill demand.
- Structured datasets supporting trend analysis.
- Reliable re-aggregation across reporting dimensions.

### 4. Priority Mart

An analytical data mart focused on priority job roles and incremental data updates.

<img width="1976" height="1316" alt="1_2_Priority_Mart" src="https://github.com/user-attachments/assets/e8d35d4e-4576-428b-8597-c1668b6bd6e0" />


**SQL Files:**

- `05_create_priority_mart.sql` — Creates the initial priority role and job posting snapshot.
- `06_update_priority_mart.sql` — Implements incremental updates using SQL MERGE operations.

**Purpose:** Track priority job roles and maintain updated analytical snapshots.

**Grain:** One row per job posting with an assigned priority level.

**Key Features:**

- Incremental data processing.
- SQL MERGE operations.
- INSERT, UPDATE and DELETE logic.
- Repeatable data maintenance workflows.

### 5. Company Mart (Optional)

A specialised analytical data mart designed to investigate company hiring activity.

<img width="1692" height="1084" alt="1_2_Company_Mart" src="https://github.com/user-attachments/assets/585c76e0-a09e-4335-b84a-e7f7007750eb" />


**SQL File:** `07_create_company_mart.sql`

**Purpose:** Analyse company hiring trends across job roles, locations and reporting periods.

**Grain:** `company_id + job_title_short_id + location_id + month_start_date`

**Key Features:**

- Company hiring trend analysis.
- Bridge tables supporting many-to-many relationships.
- Structured reporting by company, role, location and month.
- Optional implementation depending on reporting requirements.

---

## 💻 Data Engineering Skills Demonstrated

### ETL Pipeline Development

- **Extract:** Retrieved CSV datasets from Google Cloud Storage using DuckDB's `httpfs` extension.
- **Transform:** Applied SQL-based data cleaning, normalisation, filtering and type conversion.
- **Load:** Populated warehouse tables using structured SQL operations.
- **Incremental Updates:** Implemented MERGE operations for inserting, updating and deleting records.
- **Orchestration:** Used `build_dw_marts.sql` to coordinate pipeline execution.

### Dimensional Modelling

- **Star Schema Design:** Structured fact and dimension tables for analytical reporting.
- **Bridge Tables:** Modelled many-to-many relationships using intermediate tables.
- **Fact Table Granularity:** Defined the level of detail represented by analytical records.
- **Additive Measures:** Applied counts and sums to support reliable aggregation.
- **Surrogate Keys:** Used sequential identifiers where required for dimensional modelling.

### Advanced SQL Techniques

- **DDL:** `CREATE TABLE`, `DROP TABLE`, `CREATE SCHEMA`
- **DML:** `INSERT INTO ... SELECT`
- **MERGE:** Incremental updates with matched and unmatched conditions.
- **CTEs:** Common Table Expressions for structured data transformations.
- **Date Functions:** `DATE_TRUNC`, `EXTRACT`
- **String Functions:** `STRING_AGG`, `REPLACE`
- **Conditional Logic:** `CASE WHEN` for data classification and transformation.
- **Joins and Aggregations:** Combining datasets and generating analytical measures.

### Data Quality & Production Practices

- **Idempotency:** Designed scripts for repeatable execution.
- **Data Validation:** Applied verification queries throughout the pipeline.
- **Type Safety:** Defined appropriate SQL data types, including `VARCHAR`, `INTEGER`, `DOUBLE`, `BOOLEAN` and `TIMESTAMP`.
- **Schema Organisation:** Separated analytical data marts into logical schemas.
- **Error Handling:** Structured SQL execution and validation to support troubleshooting.

---

## 🎯 Project Outcomes

The project demonstrates an end-to-end data engineering workflow, from cloud-based data extraction to structured analytical data marts.

**Key Deliverables:**

- Centralised star schema data warehouse.
- SQL-based ETL pipeline.
- Specialised analytical data marts.
- Incremental data update logic.
- Data validation and transformation workflows.
- Reusable SQL scripts for analytical data processing.

The resulting architecture provides a structured foundation for business intelligence, employment trend analysis and data-driven decision-making.

---

## 🚀 Future Enhancements

- Integrate interactive Power BI dashboards for analytical reporting.
- Introduce automated pipeline scheduling and monitoring.
- Implement additional data quality checks.
- Expand incremental processing capabilities.
- Explore cloud-based deployment and performance optimisation.

---

## 📚 Key Skills Demonstrated

**Data Engineering | SQL | ETL Development | Data Warehousing | Dimensional Modelling | Star Schema | Data Integration | Data Transformation | Data Quality | Analytical Data Marts | Incremental Processing | Business Intelligence | Problem-Solving**

