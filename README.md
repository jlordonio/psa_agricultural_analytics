# 🌾 Philippines PSA Agricultural Production dbt Pipeline

A modular analytics engineering data pipeline built with **dbt Cloud** and **Google BigQuery** to transform wide-format historical crop data (1987–2026) from the Philippine Statistics Authority (PSA) into a clean, normalized, production-ready analytics mart.

## 🏗️ Architecture & Data Transformation Flow
- **Staging (`stg_psa_crop_production`):** Dynamically unpivots wide-format crop yield columns into a long-format structure using a custom Jinja macro (`get_unpivot_columns`).
- **Intermediate (`int_psa_crop_production_transformed`):** Uses BigQuery SQL REGEX expressions to parse out `production_year` and separate quarterly totals (`Quarter 1` to `Quarter 4`) from annual aggregations (`null`).
- **Marts Layer (`fct_psa_crop_production`):** Creates the finalized fact table (130,000+ rows) optimized for downstream Business Intelligence platforms (e.g., Looker Studio, Power BI).

## 🛠️ Tech Stack & Best Practices
- **Data Warehouse:** Google BigQuery
- **Transformation Engine:** dbt Cloud (SQL, Jinja Macros)
- **Version Control:** GitHub
- **Data Quality & Testing:** Implemented schema testing (`not_null`, `unique`) across primary keys and key dimensional fields.
