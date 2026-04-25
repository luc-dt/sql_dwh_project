# Data Warehouse & Analytics Project

A portfolio project demonstrating a modern data warehousing solution built with SQL Server, following **Medallion Architecture** (Bronze → Silver → Gold) from raw ingestion to business-ready analytics.

---

## Business Problem

> **Objective:** Develop a modern data warehouse using SQL Server to consolidate sales data from two source systems (ERP & CRM), enabling analytical reporting and informed decision making.

### Requirements

| # | Area | Specification |
|---|---|---|
| 1 | **Data Sources** | Import data from two source systems — ERP and CRM — provided as CSV files |
| 2 | **Data Quality** | Clean and fix data quality issues before analysis |
| 3 | **Integration** | Combine both sources into a single, analytics-ready data model |
| 4 | **Scope** | Focus on the latest data only — no full historization required |
| 5 | **Documentation** | Provide clear documentation of the data model for business users and analytical teams |

### Analytical Goals

Once the data warehouse is built, it serves as the foundation for analytics using Advanced SQL techniques to:

- Find trends over time
- Compare performance across different dimensions
- Segment data into meaningful groups
- Generate reports for stakeholders

---

## Dataset Overview

The source data represents **Adventure Works Cycles**, a bicycle retail company selling bikes, accessories, clothing, and components globally. Data is ingested from two systems as CSV files:

| Source | File / Table | Description |
|--------|-------------|-------------|
| CRM | `cust_info.csv` | Customer registration records (name, gender, marital status) |
| CRM | `prd_info.csv` | Product catalog with versioned pricing (SCD Type 2) |
| CRM | `sales_details.csv` | Sales order line items (revenue, quantity, dates) |
| ERP | `CUST_AZ12.csv` | Customer demographics (birth date, gender) |
| ERP | `LOC_A101.csv` | Customer country of residence |
| ERP | `PX_CAT_G1V2.csv` | Product category and subcategory hierarchy |

**Key integration notes:**
- Customer IDs require normalization across CRM and ERP (prefix/hyphen differences)
- Gender encoding differs between systems (`M`/`F` vs `Male`/`Female`)
- Sales dates are stored as integers (`YYYYMMDD`) and must be cast to `DATE`
- Products follow SCD Type 2 — the same SKU has multiple rows tracking cost history; only current records (`prd_end_dt IS NULL`) flow into Gold

See [`datasets/explain_dataset.md`](datasets/explain_dataset.md) for the full data dictionary including column definitions, join keys, and data quality notes.

---

## Architecture

The project follows the **Medallion Architecture** with three progressive layers:

![Data Architecture](docs/data_architecture.png)

| Layer | Schema | Object Type | Description |
|-------|--------|-------------|-------------|
| **Bronze** | `bronze` | Tables | Raw data ingested as-is from CSV source files (ERP & CRM) |
| **Silver** | `silver` | Tables | Cleansed, standardized, type-cast, and normalized data |
| **Gold** | `gold` | Views | Business-ready star schema for reporting and analytics |

---

## Data Model (Gold Layer — Star Schema)

![Data Model](docs/data_model.png)

| Object | Type | Description |
|--------|------|-------------|
| `gold.dim_customers` | View | Customer dimension — enriched with ERP demographics and location |
| `gold.dim_products` | View | Product dimension — joined with ERP category hierarchy; current records only |
| `gold.fact_sales` | View | Sales fact — transactional data linked to both dimension views |

---

## ETL Pipeline

![ETL Flow](docs/data_flow.png)

### Step 1 — Initialize Database
`scripts/init_database.sql` — Creates the `DataWarehouse` database and three schemas: `bronze`, `silver`, `gold`.

### Step 2 — Bronze Layer (Raw Ingestion)
| Script | Purpose |
|--------|---------|
| `scripts/bronze/ddl_bronze.sql` | Creates 6 raw tables: `crm_cust_info`, `crm_prd_info`, `crm_sales_details`, `erp_cust_az12`, `erp_loc_a101`, `erp_px_cat_g1v2` |
| `scripts/bronze/proc_load_bronze.sql` | Stored procedure `load_bronze` — bulk-inserts all CSV files into bronze tables |

### Step 3 — Silver Layer (Cleansing & Standardization)
| Script | Purpose |
|--------|---------|
| `scripts/silver/ddl_silver.sql` | Creates 6 cleansed tables mirroring the bronze schema |
| `scripts/silver/proc_load_silver.sql` | Stored procedure `load_silver` — applies data quality fixes: type casting, gender normalization, customer ID deduplication, date parsing |

### Step 4 — Gold Layer (Business Views)
| Script | Purpose |
|--------|---------|
| `scripts/gold/ddl_gold.sql` | Creates 3 Gold views: `dim_customers`, `dim_products`, `fact_sales` |

---

## Repository Structure

```
luc-dt_dwh_project/
│
├── datasets/                           # Source CSV files used for ingestion
│   ├── source_crm/
│   │   ├── cust_info.csv               # CRM customer records
│   │   ├── prd_info.csv                # CRM product catalog (SCD Type 2)
│   │   └── sales_details.csv           # CRM sales transactions
│   ├── source_erp/
│   │   ├── CUST_AZ12.csv               # ERP customer demographics
│   │   ├── LOC_A101.csv                # ERP customer locations
│   │   └── PX_CAT_G1V2.csv             # ERP product categories
│   └── explain_dataset.md              # Full data dictionary and quality notes
│
├── docs/                               # Project documentation and diagrams
│   ├── data_architecture.drawio/.png   # Medallion architecture diagram
│   ├── data_model.drawio/.png          # Star schema (Gold layer)
│   ├── data_flow.drawio/.png           # End-to-end ETL data flow
│   ├── data_integration.drawio/.png    # Source-to-target integration map
│   ├── ETL.drawio/.png                 # ETL techniques and methods reference
│   ├── data_catalog.md                 # Column-level metadata for Gold layer
│   ├── naming_conventions.md           # Naming rules for tables, columns, procedures
│   └── process_dwh.md                  # Detailed DWH build process notes (local only — gitignored)
│
├── scripts/                            # SQL scripts for ETL pipeline
│   ├── init_database.sql               # Create DataWarehouse DB + bronze/silver/gold schemas
│   ├── bronze/
│   │   ├── ddl_bronze.sql              # Create 6 raw Bronze tables
│   │   └── proc_load_bronze.sql        # Stored proc: bulk-insert CSVs into Bronze
│   ├── silver/
│   │   ├── ddl_silver.sql              # Create 6 cleansed Silver tables
│   │   └── proc_load_silver.sql        # Stored proc: clean & load Bronze → Silver
│   └── gold/
│       └── ddl_gold.sql                # Create dim_customers, dim_products, fact_sales views
│
├── README.md                           # Project overview (this file)
└── .gitignore                          # Git ignore rules
```

---

## How to Run

> Prerequisites: SQL Server Express + SSMS installed on your machine.

1. **Initialize the database**
   - Open SSMS and run `scripts/init_database.sql`
   - This creates the `DataWarehouse` database and all three schemas

2. **Create Bronze tables**
   - Run `scripts/bronze/ddl_bronze.sql`

3. **Load Bronze layer**
   - Run `scripts/bronze/proc_load_bronze.sql` to create the stored procedure
   - Then execute: `EXEC bronze.load_bronze;`
   - Update the file paths inside the procedure to match your local CSV locations

4. **Create Silver tables**
   - Run `scripts/silver/ddl_silver.sql`

5. **Load Silver layer**
   - Run `scripts/silver/proc_load_silver.sql` to create the stored procedure
   - Then execute: `EXEC silver.load_silver;`

6. **Create Gold views**
   - Run `scripts/gold/ddl_gold.sql`
   - Query `gold.dim_customers`, `gold.dim_products`, `gold.fact_sales` directly

---

## Documentation

| Document | Description |
|----------|-------------|
| [`docs/data_catalog.md`](docs/data_catalog.md) | Column-level definitions for all Gold layer objects |
| [`docs/naming_conventions.md`](docs/naming_conventions.md) | Naming rules for tables, views, columns, and stored procedures |
| `docs/process_dwh.md` | Step-by-step DWH build process and design decisions *(local only — excluded from repo)* |
| [`datasets/explain_dataset.md`](datasets/explain_dataset.md) | Source data dictionary, join keys, and known quality issues |

---

## Tools

- **[SQL Server Express](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)** — database host
- **[SSMS](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms)** — database GUI
- **[DrawIO](https://www.drawio.com/)** — architecture and data flow diagrams
