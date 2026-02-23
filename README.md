# ETL_Project_First_Delivery

ETL project analyzing COVID-19 vaccination data in Ecuador aligned with SDG 3 (Good Health and Well-being). The project evaluates territorial vaccination coverage, regional inequalities, and temporal trends using Python, a relational database, SQL, and data visualizations.

# COVID-19 Vaccination Coverage Analysis in Ecuador

### SDG 3 – Good Health and Well-being

## 📖 Project Overview

This project analyzes COVID-19 vaccination data in Ecuador to evaluate territorial coverage and health equity in alignment with the United Nations Sustainable Development Goal 3 (Good Health and Well-being).

The objective is to assess vaccination progress across provinces and cantons, identify potential regional inequalities, and provide data-driven insights to support public health decision-making.

The project follows a complete ETL pipeline:

* Data extraction from a CSV dataset
* Transformation and cleaning using Python
* Migration into a relational database
* Exploratory Data Analysis (EDA)
* Visualization and reporting based exclusively on database queries

---

## 🧾 Dataset Description

The project uses a cleaned CSV dataset (`vacunacion_limpia.csv`) with **66,320 rows** and **12 columns**, containing territorial vaccination records aggregated at the **canton** level.

### Main fields

**Geography**

* `zona`: macro-zone category used in the dataset
* `region`: geographic region (e.g., Coast / Sierra / Amazon)
* `provincia`: province name
* `canton`: canton name

**Population**

* `provincia_poblacion`: province population
* `canton_poblacion`: canton population

**Vaccination measures**

* `dosis_total`: total administered doses
* `primera_dosis`: first doses
* `segunda_dosis`: second doses
* `dosis_unica`: single-dose vaccines 
* `dosis_refuerzo`: booster doses

**Time**

* `created_at`: record date 

---

## 🎯 SDG Alignment

This project directly contributes to:

**SDG 3 – Good Health and Well-being**

* Target 3.8: Achieve universal health coverage
* Target 3.d: Strengthen capacity for health risk management

By combining vaccination records with population data, we evaluate:

* Vaccination coverage rates by province and canton
* Progress of first, second, and booster doses
* Geographic disparities in vaccine distribution
* Temporal evolution of vaccination campaigns

---

## 🏗️ Architecture

The proposed ETL architecture includes:

1. **Data Ingestion Layer** – CSV dataset
2. **Transformation Layer** – Data cleaning and validation (Python)
3. **Storage Layer** – Relational Database (MySQL)
4. **Data Model** – Structured schema
5. **Analytics Layer** – SQL-based extraction
6. **Visualization Layer** – Charts and dashboards generated from DB queries 

---

## ⭐ Star Schema (Data Warehouse Model)

To support fast analytics and clean SQL queries, the database is organized as a **star schema**: one central **fact table** (metrics) connected to **dimension tables** (context).

### ✅ Fact Table: `fact_vaccination`


**Foreign Keys**

* `date_id` → `dim_date`
* `territory_id` (or `canton_id`) → `dim_territory` (or `dim_canton`)

**Measures**

* `dosis_total`
* `primera_dosis`
* `segunda_dosis`
* `dosis_unica`
* `dosis_refuerzo`

### ✅ Dimension Table: `dim_date`

Describes time for trend analysis.

* `date_id`
* `date` (from `created_at`)
* optional derived attributes: `year`, `month`, `week`, `day`

### ✅ Dimension Table: `dim_territory`

Describes the geographic hierarchy and reference population.

* `territory_id`
* `zona`
* `region`
* `provincia`
* `canton`
* `provincia_poblacion`
* `canton_poblacion`


---

## 🛠️ Technology Stack

* Python
* MySQL
* SQL
* Matplotlib / Seaborn / Power BI
* Git & GitHub

---

## 📊 Key Analyses

* Vaccination coverage rate = (total doses / population) × 100
* Comparison across regions (Coast, Sierra, Amazon)
* First vs second vs booster dose distribution
* Geographic mapping using latitude and longitude
* Temporal trends of vaccine administration

---

## 📌 Conclusion

This project demonstrates how data engineering and analytics can support global development objectives by transforming raw public health data into actionable insights aligned with the SDG framework.

---
