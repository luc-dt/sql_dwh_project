# Data Warehouse & Analytics Project

A portfolio project demonstrating a modern data warehousing solution built with SQL Server, following Medallion Architecture from raw ingestion to business-ready analytics.

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
│   ├── naming-conventions.md           # Consistent naming guidelines for tables, columns, and files
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
