# 📊 Exploratory Data Analysis with SQL: Job Market Analysis

A SQL-based data analytics project investigating the data engineering job market using real-world job posting data. This project demonstrates the ability to write analytical SQL queries, work with relational data models, perform statistical analysis and transform business questions into actionable, data-driven insights.

![alt text](1_1_Project1_EDA.png)

---

## 📌 Executive Summary

- ✅ **Project Scope:** Developed three analytical SQL queries to investigate technical skill demand, salary trends and career opportunities in data engineering.
- ✅ **Data Modelling:** Utilised a star schema consisting of fact tables, dimension tables and bridge tables to perform relational data analysis.
- ✅ **SQL Analytics:** Applied multi-table joins, aggregations, filtering, sorting and mathematical functions to analyse job market datasets.
- ✅ **Business Insights:** Identified high-demand programming languages, emerging cloud technologies and technical skills associated with competitive salaries.

### Quick Access to SQL Analysis

1. [01_top_demanded_skills.sql](./01_top_demanded_skills.sql) — Technical skill demand analysis.
2. [02_top_paying_skills.sql](./02_top_paying_skills.sql) — Salary analysis and compensation trends.
3. [03_optimal_skills.sql](./03_optimal_skills.sql) — Combined salary and demand analysis.

---

## 🎯 Problem & Context

The technology job market continues to evolve as organisations adopt cloud computing, automation and data-driven technologies.

Understanding which technical skills are in demand, which offer competitive compensation and which provide the best balance between demand and salary can help professionals make informed career decisions.

This project addresses three key analytical questions:

- **Most In-Demand Skills:** Which technical skills appear most frequently in data engineering job postings?
- **Highest-Paying Skills:** Which skills are associated with the highest median salaries?
- **Optimal Skills:** Which technical skills provide the strongest balance between market demand and compensation?

### Data Warehouse Structure

The analysis uses a relational data warehouse designed around a star schema.

![alt text](1_2_Data_Warehouse.png)

The warehouse consists of:

**Fact Table**

- `job_postings_fact` — Contains job posting information, including job titles, locations, salary details and posting dates.

**Dimension Tables**

- `company_dim` — Contains company information associated with job postings.
- `skills_dim` — Contains technical skill names and categories.

**Bridge Table**

- `skills_job_dim` — Connects job postings to technical skills and manages many-to-many relationships.

By joining these tables, the analysis identifies patterns in skill demand, compensation and employment opportunities.

---

## 🛠️ Tech Stack

| Category | Technologies |
|---|---|
| Query Engine | DuckDB |
| Programming Language | SQL |
| Data Architecture | Star Schema |
| Database Concepts | Fact Tables, Dimension Tables, Bridge Tables |
| Development Environment | Visual Studio Code |
| Query Execution | DuckDB CLI / Terminal |
| Version Control | Git, GitHub |
| Analytical Techniques | Joins, Aggregations, Filtering, Statistical Analysis |

---

## 🔍 Analysis Overview

### 1. Top Demanded Skills

**SQL File:** [01_top_demanded_skills.sql](./01_top_demanded_skills.sql)

**Objective:** Identify the ten most frequently requested technical skills for remote data engineering positions.

**Approach:**

- Joined job posting and technical skill tables.
- Filtered job postings based on role and remote-work criteria.
- Applied `COUNT()` to measure demand for each skill.
- Used `GROUP BY`, `ORDER BY` and `LIMIT` to identify the ten most frequently requested skills.

**Outcome:** Identified technical skills that employers most frequently request, supporting evidence-based learning and career development priorities.

**[Insert Top Demanded Skills Results Image Here]**

### 2. Top Paying Skills

**SQL File:** [02_top_paying_skills.sql](./02_top_paying_skills.sql)

**Objective:** Identify the 25 highest-paying technical skills and investigate their relationship with job market demand.

**Approach:**

- Combined job posting salary information with technical skill data.
- Excluded records with missing salary values.
- Used `MEDIAN()` and `ROUND()` to calculate salary statistics.
- Applied aggregation and sorting to identify skills associated with higher compensation.

**Outcome:** Produced a ranked analysis of technical skills based on salary, highlighting technologies associated with higher-paying data engineering opportunities.

**[Insert Top Paying Skills Results Image Here]**

### 3. Optimal Skills Analysis

**SQL File:** [03_optimal_skills.sql](./03_optimal_skills.sql)

**Objective:** Identify technical skills offering a favourable balance between employer demand and compensation.

**Approach:**

- Calculated job posting counts for individual skills.
- Determined median salaries for each technical skill.
- Applied the `LN()` mathematical function to transform demand values.
- Developed a calculated score combining log-transformed demand and median salary.
- Used the `HAVING` clause to focus on skills appearing in at least 100 job postings.

**Outcome:** Developed a comparative scoring approach to highlight skills offering a strong combination of market demand and salary potential.

**[Insert Optimal Skills Analysis Results Image Here]**

---

## 📈 Key Findings & Business Insights

### 1. SQL and Python Dominate Skill Demand

SQL and Python each appeared in approximately 29,000 job postings in the analysed dataset.

**Insight:** These programming languages remain important foundational skills for data engineering roles.

### 2. Cloud Computing Skills Are Highly Relevant

AWS and Microsoft Azure featured prominently in the data engineering job market.

**Insight:** Cloud platform knowledge can complement traditional database and programming skills.

### 3. Infrastructure Technologies Offer Valuable Opportunities

Kubernetes, Docker and Terraform were associated with competitive salary opportunities.

**Insight:** Infrastructure automation and containerisation skills can strengthen a data engineering skill set.

### 4. Big Data Technologies Remain Important

Apache Spark demonstrated strong market demand alongside competitive compensation.

**Insight:** Distributed data processing technologies are valuable areas for professional development.

*These findings reflect the analysed job posting dataset and should not be interpreted as current market-wide estimates.*

---

## 💻 SQL Skills Demonstrated

### Query Design and Optimisation

- **Complex Joins:** Used multi-table `INNER JOIN` operations across fact, dimension and bridge tables.
- **Aggregations:** Applied `COUNT()`, `MEDIAN()` and `ROUND()` for statistical analysis.
- **Filtering:** Used `WHERE` clauses with multiple conditions to select relevant records.
- **Sorting:** Applied `ORDER BY DESC` to rank results.
- **Top-N Analysis:** Used `LIMIT` to identify the most relevant results.

### Data Analysis Techniques

- **Grouping:** Applied `GROUP BY` for categorical skill analysis.
- **Conditional Logic:** Used `CASE WHEN` statements to derive analytical measures.
- **Mathematical Functions:** Applied `LN()` to transform skill demand metrics.
- **Calculated Metrics:** Combined salary and demand into a comparative score.
- **Aggregate Filtering:** Used `HAVING` to exclude skills with insufficient posting counts.
- **NULL Handling:** Excluded incomplete salary records using `IS NOT NULL`.

---

## 🎯 Project Outcomes

The project demonstrates the practical application of SQL and relational database concepts to solve business-oriented analytical problems.

**Key Deliverables:**

- Three structured analytical SQL queries.
- Technical skill demand analysis.
- Salary and compensation analysis.
- Combined salary-demand scoring.
- Relational data analysis using a star schema.
- Actionable insights into data engineering employment trends.

The analysis demonstrates how structured SQL queries can transform large datasets into useful information for career planning, skills development and strategic decision-making.

---

## 🚀 Future Enhancements

- Develop interactive Power BI dashboards to visualise technical skill demand and salary trends.
- Expand the analysis to additional technology roles and geographic regions.
- Introduce historical comparisons to investigate changes in technical skill demand.
- Automate dataset updates and SQL analysis workflows.
- Explore predictive analytics techniques to forecast future skill demand.

---

## 📚 Key Skills Demonstrated

**SQL | Exploratory Data Analysis | Data Analytics | DuckDB | Data Warehousing | Relational Databases | Star Schema | SQL Joins | Aggregations | Statistical Analysis | Data Interpretation | Business Intelligence | Problem-Solving | Analytical Thinking | Data-Driven Decision-Making**

