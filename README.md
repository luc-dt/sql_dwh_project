# Data Warehouse & Analytics Project

![SQL Server](https://img.shields.io/badge/SQL%20Server-Express-CC2927?logo=microsoftsqlserver)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)
![License](https://img.shields.io/badge/License-MIT-blue)

A portfolio project demonstrating a modern data warehousing solution built with SQL Server, following **Medallion Architecture** (Bronze → Silver → Gold) from raw ingestion to business-ready analytics.

---

## Skills Demonstrated

- Medallion Architecture design (Bronze → Silver → Gold)
- Multi-source data integration (ERP + CRM normalization)
- Data quality engineering: type casting, deduplication, SCD Type 2 handling
- Star schema modeling (fact + dimension tables)
- Stored procedure-based ETL pipelines
- Advanced SQL analytics: window functions, aggregations, segmentation, ranking
- Consolidated reporting views (Customer & Product reports)

---

## Business Problem

> **Objective:** Develop a modern data warehouse using SQL Server to consolidate sales data from two source systems (ERP & CRM), enabling analytical reporting and informed decision making.

### Requirements

| #   | Area              | Specification                                                                   |
| --- | ----------------- | ------------------------------------------------------------------------------- |
| 1   | **Data Sources**  | Import data from two source systems — ERP and CRM — provided as CSV files       |
| 2   | **Data Quality**  | Clean and fix data quality issues before analysis                               |
| 3   | **Integration**   | Combine both sources into a single, analytics-ready data model                  |
| 4   | **Scope**         | Focus on the latest data only — no full historization required                  |
| 5   | **Documentation** | Provide clear documentation of the data model for business and analytical teams |

### Analytical Goals

Once the data warehouse is built, it supports SQL-based analytics to:

- Find trends over time
- Compare performance across dimensions
- Segment customers and products into meaningful groups
- Generate executive-level reports

---

## Dataset Overview

Source data represents **Adventure Works Cycles**, a bicycle retail company selling bikes, accessories, clothing, and components globally. Data is ingested from two systems as CSV files:

| Source | File / Table        | Description                                                  |
| ------ | ------------------- | ------------------------------------------------------------ |
| CRM    | `cust_info.csv`     | Customer registration records (name, gender, marital status) |
| CRM    | `prd_info.csv`      | Product catalog with versioned pricing (SCD Type 2)          |
| CRM    | `sales_details.csv` | Sales order line items (revenue, quantity, dates)            |
| ERP    | `CUST_AZ12.csv`     | Customer demographics (birth date, gender)                   |
| ERP    | `LOC_A101.csv`      | Customer country of residence                                |
| ERP    | `PX_CAT_G1V2.csv`   | Product category and subcategory hierarchy                   |

**Key integration challenges solved:**

- Customer IDs normalized across CRM and ERP (prefix/hyphen differences)
- Gender encoding reconciled (`M`/`F` vs `Male`/`Female`)
- Sales dates cast from integer `YYYYMMDD` format to `DATE`
- SCD Type 2 products deduplicated — only current records (`prd_end_dt IS NULL`) flow to Gold

See [`datasets/explain_dataset.md`](datasets/explain_dataset.md) for the full data dictionary.

---

## Architecture

The project follows the **Medallion Architecture** with three progressive layers:

![Data Architecture](docs/data_architecture.png)

| Layer      | Schema   | Object Type | Description                                            |
| ---------- | -------- | ----------- | ------------------------------------------------------ |
| **Bronze** | `bronze` | Tables      | Raw data ingested as-is from CSV source files          |
| **Silver** | `silver` | Tables      | Cleansed, standardized, type-cast, and normalized data |
| **Gold**   | `gold`   | Views       | Business-ready star schema for reporting and analytics |

---

## ETL Pipeline

![ETL Flow](docs/data_flow.png)

### Step 1 — Initialize Database

`scripts/init_database.sql` — Creates the `DataWarehouse` database and three schemas (`bronze`, `silver`, `gold`).

### Step 2 — Bronze Layer (Raw Ingestion)

| Script                                | Purpose                                                  |
| ------------------------------------- | -------------------------------------------------------- |
| `scripts/bronze/ddl_bronze.sql`       | Creates 6 raw staging tables                             |
| `scripts/bronze/proc_load_bronze.sql` | Stored procedure: bulk-inserts all CSV files into Bronze |

### Step 3 — Silver Layer (Cleansing & Standardization)

| Script                                | Purpose                                                      |
| ------------------------------------- | ------------------------------------------------------------ |
| `scripts/silver/ddl_silver.sql`       | Creates 6 cleansed Silver tables                             |
| `scripts/silver/proc_load_silver.sql` | Stored procedure: type casting, normalization, deduplication |

### Step 4 — Gold Layer (Business Views)

| Script                      | Purpose                                                     |
| --------------------------- | ----------------------------------------------------------- |
| `scripts/gold/ddl_gold.sql` | Creates `dim_customers`, `dim_products`, `fact_sales` views |

---

## Data Model (Gold Layer — Star Schema)

![Data Model](docs/data_model.png)

| Object               | Type | Description                                                         |
| -------------------- | ---- | ------------------------------------------------------------------- |
| `gold.dim_customers` | View | Customer dimension enriched with ERP demographics and location      |
| `gold.dim_products`  | View | Product dimension with ERP category hierarchy; current records only |
| `gold.fact_sales`    | View | Sales fact table linked to both dimension views                     |

---

## Data Quality Tests

| Script                        | Scope           | Checks                                                              |
| ----------------------------- | --------------- | ------------------------------------------------------------------- |
| `tests/quality_checks_silver.sql` | Silver Layer | Nulls, duplicates, out-of-range values, invalid gender/date codes |
| `tests/quality_checks_gold.sql`   | Gold Layer   | Referential integrity, null keys in fact table                    |

---

## Analytics

The Gold layer supports a full analytical workload across **14 SQL scripts** in `scripts/analytics/`:

### Exploration Scripts

| Script                             | Purpose                                                             |
| ---------------------------------- | ------------------------------------------------------------------- |
| `00_init_database.sql`             | Standalone analytics DB (`DataWarehouseAnalytics`) setup + CSV load |
| `01_database_exploration.sql`      | Discover available schemas, tables, and columns                     |
| `02_dimension_exploration.sql`     | Explore distinct values in dimension tables                         |
| `03_date_range_exploration.sql`    | Understand order date ranges and time span of the data              |
| `04_measures_exploration.sql`      | High-level metrics: total sales, orders, customers, products        |

### Analytical Reports

| Script                             | Technique                              | Business Questions Answered                             |
| ---------------------------------- | -------------------------------------- | ------------------------------------------------------- |
| `05_magnitude_analysis.sql`        | `GROUP BY`, `SUM()`, `COUNT()`         | Revenue by category, customers by country/gender        |
| `06_ranking_analysis.sql`          | `RANK()`, `ROW_NUMBER()`, `TOP N`      | Top products and customers by revenue                   |
| `07_change_over_time_analysis.sql` | `DATETRUNC()`, `DATEPART()`, `FORMAT()` | Monthly and yearly sales trends                        |
| `08_cumulative_analysis.sql`       | `SUM() OVER()` (running totals)        | Cumulative revenue and moving averages over time        |
| `09_performance_analysis.sql`      | `LAG()`, year-over-year comparison     | Product performance vs. average and vs. previous year   |
| `10_data_segmentation.sql`         | `CASE WHEN` segmentation               | Customer and product groupings by spend / cost tier     |
| `11_part_to_whole_analysis.sql`    | Proportional `SUM()`, category share   | Category contribution to total revenue                  |

### Consolidated Report Views

| Script                  | View Created                 | Description                                                               |
| ----------------------- | ---------------------------- | ------------------------------------------------------------------------- |
| `12_report_customers.sql` | `gold.report_customers`    | Per-customer KPIs: recency, AOV, monthly spend, segment (VIP/Regular/New) |
| `13_report_products.sql`  | `gold.report_products`     | Per-product KPIs: revenue, orders, quantity, recency, segment             |



## Repository Structure

```
sql_dwh_project/
│
├── datasets/
│   ├── source_crm/                      # CRM CSV source files
│   │   ├── cust_info.csv
│   │   ├── prd_info.csv
│   │   └── sales_details.csv
│   ├── source_erp/                      # ERP CSV source files
│   │   ├── CUST_AZ12.csv
│   │   ├── LOC_A101.csv
│   │   └── PX_CAT_G1V2.csv
│   ├── csv-files/                       # Exported Gold layer CSVs
│   │   ├── gold.dim_customers.csv
│   │   ├── gold.dim_products.csv
│   │   └── gold.fact_sales.csv
│   └── explain_dataset.md               # Data dictionary and quality notes
│
├── docs/
│   ├── data_architecture.drawio/.png    # Medallion architecture diagram
│   ├── data_model.drawio/.png           # Star schema (Gold layer)
│   ├── data_flow.drawio/.png            # End-to-end ETL data flow
│   ├── data_integration.drawio/.png     # Source-to-Silver integration map
│   ├── ETL.drawio/.png                  # Detailed ETL process diagram
│   ├── data_catalog.md                  # Column-level metadata for Gold layer
│   └── naming_conventions.md            # Naming rules for tables, views, procedures
│
├── scripts/
│   ├── init_database.sql                # Create DataWarehouse DB + schemas
│   ├── bronze/
│   │   ├── ddl_bronze.sql               # Raw table definitions
│   │   └── proc_load_bronze.sql         # Bulk-load stored procedure
│   ├── silver/
│   │   ├── ddl_silver.sql               # Cleansed table definitions
│   │   └── proc_load_silver.sql         # Transform & load stored procedure
│   ├── gold/
│   │   └── ddl_gold.sql                 # Star schema view definitions
│   └── analytics/                       # Exploration + analytical SQL scripts
│       ├── 00_init_database.sql         # Analytics DB setup (standalone)
│       ├── 01_database_exploration.sql
│       ├── 02_dimension_exploration.sql
│       ├── 03_date_range_exploration.sql
│       ├── 04_measures_exploration.sql
│       ├── 05_magnitude_analysis.sql
│       ├── 06_ranking_analysis.sql
│       ├── 07_change_over_time_analysis.sql
│       ├── 08_cumulative_analysis.sql
│       ├── 09_performance_analysis.sql
│       ├── 10_data_segmentation.sql
│       ├── 11_part_to_whole_analysis.sql
│       ├── 12_report_customers.sql      # Creates gold.report_customers view
│       └── 13_report_products.sql       # Creates gold.report_products view
│
├── tests/
│   ├── quality_checks_silver.sql        # Silver layer data quality checks
│   └── quality_checks_gold.sql          # Gold layer referential integrity checks
│
├── README.md
└── .gitignore
```

---

## How to Run

> **Prerequisites:** SQL Server Express + SSMS installed locally.

### Option A — Full ETL Pipeline (recommended)

1. Run `scripts/init_database.sql` — creates `DataWarehouse` DB and schemas
2. Run `scripts/bronze/ddl_bronze.sql` — creates raw tables
3. Run `scripts/bronze/proc_load_bronze.sql`, then:
   ```sql
   EXEC bronze.load_bronze;
   ```
   > Update file paths inside the procedure to match your local CSV locations
4. Run `scripts/silver/ddl_silver.sql` — creates cleansed tables
5. Run `scripts/silver/proc_load_silver.sql`, then:
   ```sql
   EXEC silver.load_silver;
   ```
6. Run `scripts/gold/ddl_gold.sql` — creates analytical views
7. Query `gold.dim_customers`, `gold.dim_products`, `gold.fact_sales`

### Data Quality Validation

After each layer loads, run the corresponding test script:

```sql
-- After loading Silver:
-- Run tests/quality_checks_silver.sql

-- After loading Gold:
-- Run tests/quality_checks_gold.sql
```

### Option B — Analytics Only (pre-exported CSVs)

If you want to run analytics scripts without the full pipeline:

1. Run `scripts/analytics/00_init_database.sql`
   - Creates a standalone `DataWarehouseAnalytics` DB
   - Bulk-loads the exported CSVs from `datasets/csv-files/`
   - Update the file paths in the script to match your local directory
2. Run any script in `scripts/analytics/` (01 – 13)


---

## Documentation

| Document                                                     | Description                                     |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [`docs/data_catalog.md`](docs/data_catalog.md)               | Column-level definitions for Gold layer objects |
| [`docs/naming_conventions.md`](docs/naming_conventions.md)   | Naming rules for all objects                    |
| [`datasets/explain_dataset.md`](datasets/explain_dataset.md) | Source data dictionary and quality notes        |

---
