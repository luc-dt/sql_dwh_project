# Data Warehouse & Analytics Project

A portfolio project demonstrating a modern data warehousing solution built with SQL Server, following Medallion Architecture from raw ingestion to business-ready analytics.

---

## Business Problem

> **Objective:** Develop a modern data warehouse using SQL Server to consolidate sales data, enabling analytical reporting and informed decision making.

### Requirements

| # | Area | Specification |
|---|---|---|
| 1 | **Data Sources** | Import data from two source systems — ERP and CRM — provided as CSV files |
| 2 | **Data Quality** | Clean and fix data quality issues before analysis (raw data is never perfect) |
| 3 | **Integration** | Combine both sources into a single, user-friendly data model designed for analytics and reporting |
| 4 | **Scope** | Focus on the latest data only — no historization required |
| 5 | **Documentation** | Provide clear documentation of the data model to support business users and analytical teams |

### Analytical Goals

Once the data warehouse is built, it serves as the foundation for analytics projects using Advanced SQL techniques to:

- Find trends over time
- Compare performance across different dimensions
- Segment data into different sections
- Generate reports for stakeholders

---

## Dataset Overview

The source data represents **Adventure Works Cycles**, a bicycle retail company selling bikes, accessories, clothing, and components globally. Data comes from two systems ingested as CSV files:

| Source | Table | Description |
|---|---|---|
| CRM | `cust_info` | Customer registration records (name, gender, marital status) |
| CRM | `prd_info` | Product catalog with versioned pricing (SCD Type 2) |
| CRM | `sales_details` | Sales order line items (revenue, quantity, dates) |
| ERP | `CUST_AZ12` | Customer demographics (birth date, gender) |
| ERP | `LOC_A101` | Customer country of residence |
| ERP | `PX_CAT_G1V2` | Product category and subcategory hierarchy |

**Key integration notes:**
- Customer IDs require normalization across CRM and ERP (prefix/hyphen differences)
- Gender encoding differs between systems (`M`/`F` vs `Male`/`Female`)
- Sales dates are stored as integers (`YYYYMMDD`) and must be cast
- Products follow SCD Type 2 — the same SKU has multiple rows tracking cost history

See [`datasets/explain_dataset.md`](datasets/explain_dataset.md) for the full data dictionary including column definitions, join keys, and data quality issues.

---

## Architecture

![Data Architecture](docs/data_architecture.png)

| Layer | Description |
|-------|-------------|
| **Bronze** | Raw data ingested as-is from CSV source files (ERP & CRM) |
| **Silver** | Cleansed, standardized, and normalized data |
| **Gold** | Business-ready star schema for reporting and analytics |

---

## Project Scope

- **Data Sources**: ERP and CRM systems provided as CSV files
- **ETL Pipelines**: Extract, transform, and load across all three layers
- **Data Modeling**: Fact and dimension tables optimized for analytical queries
- **Analytics**: SQL-based reports covering customer behavior, product performance, and sales trends

---

## Repository Structure

```
data-warehouse-project/
│
├── datasets/                           # Raw datasets used for the project (ERP and CRM data)
│
├── docs/                               # Project documentation and architecture details
│   ├── etl.drawio                      # Draw.io file shows all different techniquies and methods of ETL
│   ├── data_architecture.drawio        # Draw.io file shows the project's architecture
│   ├── data_catalog.md                 # Catalog of datasets, including field descriptions and metadata
│   ├── data_flow.drawio                # Draw.io file for the data flow diagram
│   ├── data_models.drawio              # Draw.io file for data models (star schema)
│   ├── naming_conventions.md           # Consistent naming guidelines for tables, columns, and files
│
├── scripts/                            # SQL scripts for ETL and transformations
│   ├── bronze/                         # Scripts for extracting and loading raw data
│   ├── silver/                         # Scripts for cleaning and transforming data
│   ├── gold/                           # Scripts for creating analytical models
│
├── tests/                              # Test scripts and quality files
│
├── README.md                           # Project overview and instructions
├── LICENSE                             # License information for the repository
├── .gitignore                          # Files and directories to be ignored by Git
```

---

## Tools

- **[SQL Server Express](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)** — database host
- **[SSMS](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms)** — database GUI
- **[DrawIO](https://www.drawio.com/)** — architecture diagrams
