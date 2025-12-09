# Databricks Medallion Architecture --- Ecommerce Analytics Project

A complete end‑to‑end **data engineering project** built on **Databricks
Free Edition**, using:

-   **Delta Lake (Bronze → Silver → Gold)**
-   **Medallion Architecture**
-   **Dimension & Fact Modeling**
-   **Databricks SQL Dashboard**
-   **Python Notebooks**
-   **Ecommerce Dataset**

This project is fully reproducible and can be cloned and run locally or
in Databricks.

------------------------------------------------------------------------

# 📂 Project Structure

    ecommerce-databricks/
    │
    ├── dimension_modelling/
    │   ├── 1_bronze_modelling.ipynb
    │   ├── gold_dimension.ipynb
    │   ├── silver_dimension.ipynb
    │   └── fact_modelling/
    │       ── bronze_dim.ipynb
    │       ├── final_BI_table.ipynb
    │       ├── gold_dim.ipynb
    │       └── silver_dim.ipynb
    │
    ├── bronze_dim.ipynb
    ├── silver_dim.ipynb
    ├── gold_dim.ipynb
    ├── final_BI_table.ipynb
    │
    ├── Sales-Dashboard.lvdash.json   # Databricks SQL Dashboard export
    │
    └── README.md

------------------------------------------------------------------------

# 🧱 Medallion Architecture Breakdown

### **1. Bronze Layer --- Raw Ingestion**

-   Raw CSV/JSON is loaded into **Delta tables**.
-   Minimal transformations.
-   Ensures data lineage and reproducibility.

**Tables Created:** - `ecommerce.bronze.orders_raw` -
`ecommerce.bronze.customers_raw` - `ecommerce.bronze.products_raw`

------------------------------------------------------------------------

### **2. Silver Layer --- Cleaned & Modeled**

-   Null handling
-   Standardized formats
-   Removing duplicates
-   Joining relevant entities

**Tables Created:** - `ecommerce.silver.orders_clean` -
`ecommerce.silver.customers_clean` - `ecommerce.silver.product_clean`

------------------------------------------------------------------------

### **3. Gold Layer --- Business Ready**

-   Aggregated for BI & reporting
-   Fact & dimension tables created

**Tables Created:** - `dim_customer` - `dim_product` - `dim_date` -
`fact_sales`

These are used to generate the Databricks dashboard.

------------------------------------------------------------------------

# 🧩 Dimension & Fact Modeling

### **Dimensions**

Contain descriptive attributes:

-   `dim_customer` → customer details
-   `dim_product` → product metadata
-   `dim_date` → normalized date table

### **Fact Table**

`fact_sales` includes:

-   order_id\
-   customer_id\
-   product_id\
-   quantity\
-   price\
-   revenue\
-   order_date

👍 Fully optimized for BI dashboards and SQL analytics.

------------------------------------------------------------------------

# 📊 Dashboard

This repo includes:

### ✔ JSON Export

`Sales-Dashboard.lvdash.json`

### ✔ Screenshot (recommended to add)

Place it under:

    assets/dashboard.png

------------------------------------------------------------------------

# 🚀 How to Run This Project

## **Step 1 --- Clone Repo**

    git clone https://github.com/YOUR_USERNAME/ecommerce-databricks.git
    cd ecommerce-databricks

------------------------------------------------------------------------

## **Step 2 --- Create Databricks Catalog & Schemas**

In Databricks SQL:

``` sql
CREATE CATALOG ecommerce;
USE CATALOG ecommerce;

CREATE SCHEMA bronze;
CREATE SCHEMA silver;
CREATE SCHEMA gold;
```

------------------------------------------------------------------------

## **Step 3 --- Import the Notebooks**

In Databricks:

1.  Workspace → Import
2.  Select all `.ipynb` files from the repo
3.  Place them in your Dev folder

------------------------------------------------------------------------

## **Step 4 --- Load Bronze Layer**

Run:

    1_bronze_modelling.ipynb

This creates raw delta tables.

------------------------------------------------------------------------

## **Step 5 --- Run Silver Layer**

Execute:

    silver_dimension.ipynb
    silver_dim.ipynb

This cleans and standardizes data.

------------------------------------------------------------------------

## **Step 6 --- Run Gold Layer**

Execute:

    gold_dimension.ipynb
    gold_dim.ipynb
    final_BI_table.ipynb

This creates all fact and dimension tables needed for reporting.

------------------------------------------------------------------------

# 📈 Step 7 --- Import Dashboard

Go to:\
**SQL → Dashboards → Import Dashboard**

Upload:

    Sales-Dashboard.lvdash.json

Your dashboard will be recreated automatically.

------------------------------------------------------------------------

# 🏗 Tech Stack

  Layer             Tool
  ----------------- --------------------------
  Storage           Delta Lake
  Compute           Databricks Runtime
  Modeling          Python, PySpark
  Orchestration     Notebooks
  Analytics         Databricks SQL Dashboard
  Version Control   GitHub

------------------------------------------------------------------------

# 🤝 Contribution

Feel free to fork, clone, or extend this project with:

-   Airflow / Workflows\
-   Unity Catalog lineage\
-   Streaming ingestion\
-   DBT modeling

------------------------------------------------------------------------

# ⭐ Author

**Shaheer Beig**\
Data Engineer \| Analytics Engineer\
Databricks • Python • SQL • ETL • Delta Lake

------------------------------------------------------------------------

# 📝 License

MIT License
