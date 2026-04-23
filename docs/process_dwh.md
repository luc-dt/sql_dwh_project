# Data Warehouse Learning Notes

---

## Table of Contents

| Module | Title |
|--------|-------|
| [Module 1](#module-1-the-big-picture) | The Big Picture |
| [Module 2](#module-2-data-modeling--the-foundation-of-everything) | Data Modeling — The Foundation of Everything |
| [Module 3](#module-3-the-medallion-layers--bronze--silver--gold) | The Medallion Layers — Bronze / Silver / Gold |
| [Module 4](#module-4-bronze-layer--raw-ingestion-ddl-bulk-insert) | Bronze Layer — Raw Ingestion, DDL, BULK INSERT |
| [Module 5](#module-5-silver-layer--etl-cleaning-transforming-deduplicating) | Silver Layer — ETL, Cleaning, Transforming, Deduplicating |
| [Module 6](#module-6-gold-layer--views-star-schema-assembly-surrogate-keys) | Gold Layer — Views, Star Schema Assembly, Surrogate Keys |
| [Module 7](#module-7-data-quality--the-test-scripts) | Data Quality — The Test Scripts |
| [Module 8](#module-8-putting-it-all-together--execution-order-dependency-graph-ops) | Putting It All Together — Execution Order, Dependency Graph, Ops |

---

## Module 1: The Big Picture

### Why does a data warehouse exist?

Companies have data scattered across operational systems:
- A **CRM** (Salesforce, HubSpot) — tracks customers and sales
- An **ERP** (SAP, Oracle) — tracks operations, locations, logistics

These systems are built for *transactions*, not *analysis*. Running a heavy analytics query on a live CRM would slow down the sales team. Also, the data is dirty, inconsistent, and spread across systems that don't talk to each other.

A **data warehouse** is a separate system built specifically for analytics. You copy data out of source systems, clean and integrate it, and serve it to analysts and BI tools.

### This project models exactly that:
- Source CRM → 3 CSV files (`cust_info`, `prd_info`, `sales_details`)
- Source ERP → 3 CSV files (`CUST_AZ12`, `LOC_A101`, `PX_CAT_G1V2`)
- Goal: combine and clean them into a single, trustworthy, queryable warehouse

### The Medallion Architecture

The pattern for how data moves through the warehouse in stages:

```
[CRM CSVs]  ─┐
              ├──► BRONZE (raw copy) ──► SILVER (cleaned) ──► GOLD (business-ready)
[ERP CSVs]  ─┘
```

Each layer has a clear contract:

| Layer | Contract |
|-------|----------|
| **Bronze** | "This is exactly what the source gave us. We changed nothing." |
| **Silver** | "This is clean, typed, and deduplicated. Trust the schema." |
| **Gold** | "This is business logic. Analysts query here. It's a star schema." |

### DS → DE Mindset Shift

| DS World | DE World |
|----------|----------|
| Jupyter notebook | SQL stored procedure |
| `pandas df.dropna()` | Silver layer cleaning logic |
| Feature engineering | Silver → Gold transformation |
| Train/test split | Source → Bronze → Silver |
| Model serving | Gold layer (what analysts query) |
| Data exploration | Data profiling / quality checks |

In DS you *consume* data. In DE you *build the pipes that produce it* — reliably, at scale, for everyone else.

---

## Module 2: Data Modeling — The Foundation of Everything

### 1. WHY — Why model data?

The **shape** of data determines how fast and easily you can answer questions.

**Option A — Normalized (how operational databases look):**
```
orders table:       order_id, customer_id, product_id, date, quantity
customers table:    customer_id, name, country, gender, birthdate
products table:     product_id, name, category, cost, line
categories table:   category_id, name, subcategory
```

**Option B — Dimensional (how warehouses look):**
```
fact_sales:         order_number, customer_key, product_key, date, quantity, sales, price
dim_customers:      customer_key, name, country, gender, birthdate, marital_status
dim_products:       product_key, name, category, subcategory, cost, line
```

For a query like *"Total sales by country and product category in Q1"*:
- Normalized: JOIN 4 tables, navigate foreign keys, worry about cardinality
- Dimensional: JOIN 3 tables, all flat and obvious

**Dimensional modeling trades write efficiency for read efficiency** — optimized for analytics, not transactions.

> DS analogy: normalization = features stored in separate dataframes indexed by ID. Dimensional = one flat feature matrix ready to query.

---

### 2. WHAT — The Two Building Blocks

#### FACT TABLES — "What happened"

Records **business events** — one row per event.

```sql
-- gold.fact_sales
order_number    -- which order
product_key     -- what was sold       ← KEY (pointer to dim)
customer_key    -- who bought it       ← KEY (pointer to dim)
order_date      -- when
sales_amount    -- how much revenue    ← MEASURE
quantity        -- how many units      ← MEASURE
price           -- unit price          ← MEASURE
```

Column types:
- **Keys** — foreign keys pointing to dimensions
- **Measures** — the numbers you aggregate (`SUM`, `AVG`, `COUNT`)

Facts are **tall and narrow**: millions of rows, few columns.
(`sales_details.csv` = ~60,000 rows = 60,000 sale events)

Note: `Sales = Quantity * price` is a **derived measure** — computed rather than stored. This is a design choice.

---

#### DIMENSION TABLES — "The context of what happened"

Describes the **who, what, where** of events. Gives facts meaning.

```sql
-- gold.dim_customers
customer_key        -- surrogate key
customer_id         -- original source ID
customer_number     -- business-facing ID (e.g. AW00011000)
first_name, last_name
country             -- from ERP (LOC_A101)
marital_status      -- from CRM
gender              -- resolved from CRM + ERP
birthdate           -- from ERP (CUST_AZ12)
create_date
```

```sql
-- gold.dim_products
product_key
product_id, product_number, product_name
category_id, category, subcategory   -- from ERP (PX_CAT_G1V2)
maintenance
cost, product_line, start_date
```

Dimensions are **short and wide**: far fewer rows, many descriptive columns.
(`cust_info.csv` = ~18,000 rows, 10 descriptive columns)

---

### 3. HOW — The Star Schema

Fact table in the center, dimensions radiating out — looks like a star.

```
          dim_customers
               |
               | customer_key
               |
dim_products --+-- fact_sales
               |
               | (future: dim_date)
```

**Analyst query pattern:**
```sql
-- "Total sales by country and product category"
SELECT
    c.country,
    p.category,
    SUM(f.sales_amount) AS total_sales
FROM gold.fact_sales f
JOIN gold.dim_customers c ON f.customer_key = c.customer_key
JOIN gold.dim_products  p ON f.product_key  = p.product_key
GROUP BY c.country, p.category;
```

Three tables. One fact, two dims. Every business question follows this same pattern — just swap the GROUP BY columns.

---

### 4. THE SURROGATE KEY

```sql
-- gold.dim_customers (ddl_gold.sql line 26)
ROW_NUMBER() OVER (ORDER BY cst_id) AS customer_key  -- Surrogate key

-- gold.dim_products (ddl_gold.sql line 55)
ROW_NUMBER() OVER (ORDER BY pn.prd_start_dt, pn.prd_key) AS product_key  -- Surrogate key
```

Why generate a new integer key when the source already has IDs?

**Reason 1 — Source systems lie.**
CRM has `cst_id = 11000`. ERP has `CID = NASAW00011000`. Same customer, different IDs. The warehouse needs its own single identity per entity, independent of source systems.

**Reason 2 — History (SCDs — Slowly Changing Dimensions).**
Products change over time (category, price, line). If you update in place, you lose history. Surrogate keys allow multiple versions of the same product (same `product_id`, different `product_key`), so historical facts point to the correct historical version.

In this project, only current products are exposed:
```sql
-- ddl_gold.sql line 69
WHERE pn.prd_end_dt IS NULL  -- Filter out all historical data
```
Historical rows still exist in Silver, preserved for future use.

**Reason 3 — Performance.**
Joining on `INT` is faster than joining on `NVARCHAR(50)`. The warehouse does this join millions of times.

---

### 5. The Integration Problem This Model Solves

```sql
-- gold.dim_customers merges 3 source tables from 2 systems
CREATE VIEW gold.dim_customers AS
SELECT
    ...
    la.cntry   AS country,        -- from ERP: LOC_A101
    CASE
        WHEN ci.cst_gndr != 'n/a' THEN ci.cst_gndr  -- CRM wins on conflict
        ELSE COALESCE(ca.gen, 'n/a')                 -- ERP as fallback
    END        AS gender,         -- resolved from BOTH sources
    ca.bdate   AS birthdate       -- from ERP: CUST_AZ12
FROM silver.crm_cust_info ci
LEFT JOIN silver.erp_cust_az12 ca ON ci.cst_key = ca.cid
LEFT JOIN silver.erp_loc_a101  la ON ci.cst_key = la.cid;
```

Three source tables (two systems) → one clean dimension. The analyst never sees CRM or ERP — they see `dim_customers`. Join logic, conflict resolution, key harmonization — all hidden inside the view.

**That is the purpose of the Gold layer:** give the business a clean, unified, denormalized interface over messy, fragmented source reality.

---

### Summary

| Concept | Rule |
|---------|------|
| **Fact table** | One row per business event; measures + foreign keys; tall & narrow |
| **Dimension table** | One row per business entity; descriptive attributes; short & wide |
| **Star schema** | Fact center + dims radiating out; optimized for SELECT/GROUP BY/aggregation |
| **Surrogate key** | Warehouse-generated integer; source-independent; enables multi-source integration + history |

---

### Open Question (Think Before Module 3)

`fact_sales` has `order_date`, `shipping_date`, `due_date`. In production, these would each point to a **`dim_date`** table with columns like `year`, `quarter`, `month`, `week`, `day_of_week`, `is_holiday`.

**Why doesn't this project have a `dim_date`? What would you gain, and what complexity does it add?**

---

## Module 3: The Medallion Layers — Bronze / Silver / Gold

### The Core Idea: Trust Increases with Each Layer

Every layer has a different audience and a different job:

```
SOURCE  →  BRONZE  →  SILVER  →  GOLD
          (raw)      (clean)    (business)
           DEs        DEs       Analysts
                      QA        BI tools
```

The further right you go, the more you've transformed the data — and the more trust stakeholders can place in it. You never go backward. Silver never writes to Bronze. Gold never writes to Silver.

### Why Three Layers and Not One?

You could skip straight from source to Gold. Why don't we?

**Reason 1 — Debugging.**
When an analyst reports wrong numbers, you trace it back layer by layer. Is the error in Gold logic? Silver cleaning? Or was the source data itself corrupt? With one layer, you can't tell.

**Reason 2 — Reusability.**
Silver is the single clean version of truth. Multiple Gold views can be built from it without re-cleaning. If you added a new Gold report, you don't re-ingest from CSV — you query Silver.

**Reason 3 — Auditability.**
Bronze is a permanent receipt. You can always prove what the source gave you, separate from what you chose to do with it.

---

### Bronze — The Raw Landing Zone

**Contract:** Store exactly what the source sent. No transformations. No filtering. No type casting.

**Who uses it:** Data engineers only — for debugging, lineage, and re-processing.

**Shape:** Mirrors the source file 1:1. Same columns, same dirty data, same types.

In this project, Bronze tables are identical to the CSV structure:
```
bronze.crm_cust_info   ← cust_info.csv        (18,494 rows)
bronze.crm_prd_info    ← prd_info.csv          (398 rows)
bronze.crm_sales_details ← sales_details.csv  (60,399 rows)
bronze.erp_cust_az12   ← CUST_AZ12.csv        (18,484 rows)
bronze.erp_loc_a101    ← LOC_A101.csv          (18,485 rows)
bronze.erp_px_cat_g1v2 ← PX_CAT_G1V2.csv      (37 rows)
```

Notice the naming: `{source_system}_{original_table_name}`. You always know where a Bronze table came from.

---

### Silver — The Cleaned, Integrated Layer

**Contract:** Clean, typed, deduplicated, standardized. Same structure as Bronze but trustworthy.

**Who uses it:** Data engineers building Gold; data scientists who need clean data for modeling.

**Transformations applied:**
- Trim whitespace from strings
- Normalize codes to readable values (`'M'` → `'Male'`, `'S'` → `'Single'`)
- Cast types (INT dates → DATE)
- Deduplicate (keep only the latest record per key)
- Derive new columns (`cat_id` from `prd_key`, `prd_end_dt` from `LEAD()`)
- Fix broken values (recalculate sales if inconsistent)
- Add audit column (`dwh_create_date`) — when did this row land in Silver?

Silver does **not** join across sources. `silver.crm_cust_info` is still CRM data. `silver.erp_cust_az12` is still ERP data. Integration happens in Gold.

---

### Gold — The Business-Ready Layer

**Contract:** Star schema. Business terminology. Ready to query without joins to understand.

**Who uses it:** Analysts, BI tools (Power BI, Tableau), reporting systems.

**Implemented as views** — not physical tables. This is important:
- No storage duplication: Gold always reads live from Silver
- No separate load step: updating Silver automatically updates Gold
- The logic lives in one place: the view definition

**Transformations applied:**
- Join across source systems (`crm_cust_info` + `erp_cust_az12` + `erp_loc_a101`)
- Assign surrogate keys (`ROW_NUMBER()`)
- Resolve conflicts between sources (CRM gender beats ERP gender)
- Filter historical records (`WHERE prd_end_dt IS NULL`)
- Rename columns to business language (`cst_firstname` → `first_name`)

---

### Layer Comparison Table

| Property | Bronze | Silver | Gold |
|----------|--------|--------|------|
| Source | CSV files | Bronze tables | Silver tables |
| Transformations | None | Clean + type + dedupe | Join + rename + enrich |
| Stored as | Tables | Tables | Views |
| Audience | Engineers | Engineers / DS | Analysts / BI |
| Trustworthy? | No (raw) | Yes | Yes |
| Cross-source joins | No | No | Yes |
| Surrogate keys | No | No | Yes |
| Audit columns | No | Yes (`dwh_create_date`) | No (inherited) |

---

## Module 4: Bronze Layer — Raw Ingestion, DDL, BULK INSERT

### Step 1: The DDL — Define the Tables

`scripts/bronze/ddl_bronze.sql` defines 6 tables. The pattern is identical for all:

```sql
-- Drop if exists, then create fresh
IF OBJECT_ID('bronze.crm_cust_info', 'U') IS NOT NULL
    DROP TABLE bronze.crm_cust_info;
GO

CREATE TABLE bronze.crm_cust_info (
    cst_id              INT,
    cst_key             NVARCHAR(50),
    cst_firstname       NVARCHAR(50),
    cst_lastname        NVARCHAR(50),
    cst_marital_status  NVARCHAR(50),
    cst_gndr            NVARCHAR(50),
    cst_create_date     DATE
);
```

**Key design decisions:**
- No `PRIMARY KEY` constraints — Bronze accepts duplicates. The source might send them.
- No `NOT NULL` constraints — Bronze accepts nulls. The source might send them.
- `NVARCHAR` for almost everything — even numeric-looking fields use strings where the source is unpredictable.
- Exception: `cst_id INT` and `cst_create_date DATE` — these are safe because the CRM source is reliable for these specific fields.
- The DDL is idempotent — run it 100 times, same result. Safe to re-run.

---

### Step 2: The Load Procedure — BULK INSERT

`scripts/bronze/proc_load_bronze.sql` loads data into these tables.

**The full procedure pattern:**
```sql
CREATE OR ALTER PROCEDURE bronze.load_bronze AS
BEGIN
    DECLARE @start_time DATETIME, @end_time DATETIME,
            @batch_start_time DATETIME, @batch_end_time DATETIME;
    BEGIN TRY
        SET @batch_start_time = GETDATE();

        -- For each table:
        TRUNCATE TABLE bronze.crm_cust_info;        -- 1. Wipe existing data
        BULK INSERT bronze.crm_cust_info             -- 2. Load from CSV
        FROM 'C:\sql\dwh_project\datasets\source_crm\cust_info.csv'
        WITH (
            FIRSTROW = 2,           -- Skip the header row
            FIELDTERMINATOR = ',',  -- CSV delimiter
            TABLOCK                 -- Lock the whole table for speed
        );

    END TRY
    BEGIN CATCH
        PRINT 'ERROR: ' + ERROR_MESSAGE();
    END CATCH
END
```

**Breaking this down:**

**`CREATE OR ALTER PROCEDURE`** — idempotent. If the procedure already exists, update it in place. If not, create it. Safe to run repeatedly during development.

**`TRUNCATE TABLE` before `BULK INSERT`** — this is a full reload (truncate-and-load pattern), not an incremental append. Every run wipes the table and reloads from scratch. Simple and reliable for small/medium datasets.

**`BULK INSERT`** — SQL Server's high-speed file loader. Far faster than row-by-row `INSERT`. For 60,000 rows it's near-instant.
- `FIRSTROW = 2` — row 1 is the header (`sls_ord_num,sls_prd_key,...`), skip it
- `FIELDTERMINATOR = ','` — CSV column separator
- `TABLOCK` — acquires a table-level lock, which enables minimal logging and maximum speed

**`BEGIN TRY / BEGIN CATCH`** — structured error handling. If any table fails to load, you see exactly which error occurred and why. Without this, a failure would be silent or cryptic.

**Timing instrumentation:**
```sql
SET @start_time = GETDATE();
-- ... load ...
SET @end_time = GETDATE();
PRINT '>> Load Duration: ' + CAST(DATEDIFF(second, @start_time, @end_time) AS NVARCHAR) + ' seconds';
```
Every table load is timed. In production this matters — if `sales_details` used to load in 2s and suddenly takes 45s, you want to know immediately.

---

### What Bronze Does NOT Do

- No data type validation
- No null checks
- No deduplication
- No transformations of any kind

If the source sends `cst_marital_status = 'M '` (with trailing space), Bronze stores `'M '`. That's intentional. Bronze is a mirror. Cleaning is Silver's job.

---

### Running the Bronze Load

```sql
-- Step 1: create the tables (run once, or when schema changes)
-- Execute: scripts/bronze/ddl_bronze.sql

-- Step 2: load the data (run on every refresh)
EXEC bronze.load_bronze;
```

---

## Module 5: Silver Layer — ETL, Cleaning, Transforming, Deduplicating

Silver is where the real engineering happens. Every transformation has a reason — let's walk through each table.

### The Load Procedure Structure

`scripts/silver/proc_load_silver.sql` — same outer structure as Bronze:
- `CREATE OR ALTER PROCEDURE silver.load_silver`
- `BEGIN TRY / BEGIN CATCH`
- `TRUNCATE` then `INSERT INTO ... SELECT ... FROM bronze.*`
- Timing for each table

The difference: instead of `BULK INSERT`, it's `INSERT INTO silver.X SELECT [transformed columns] FROM bronze.X`.

---

### Table 1: `silver.crm_cust_info` — Deduplication + Normalization

```sql
INSERT INTO silver.crm_cust_info (...)
SELECT
    cst_id,
    cst_key,
    TRIM(cst_firstname) AS cst_firstname,          -- Remove whitespace
    TRIM(cst_lastname)  AS cst_lastname,
    CASE
        WHEN UPPER(TRIM(cst_marital_status)) = 'S' THEN 'Single'
        WHEN UPPER(TRIM(cst_marital_status)) = 'M' THEN 'Married'
        ELSE 'n/a'
    END AS cst_marital_status,                     -- Decode abbreviation
    CASE
        WHEN UPPER(TRIM(cst_gndr)) = 'F' THEN 'Female'
        WHEN UPPER(TRIM(cst_gndr)) = 'M' THEN 'Male'
        ELSE 'n/a'
    END AS cst_gndr,
    cst_create_date
FROM (
    SELECT *,
        ROW_NUMBER() OVER (PARTITION BY cst_id ORDER BY cst_create_date DESC) AS flag_last
    FROM bronze.crm_cust_info
    WHERE cst_id IS NOT NULL                       -- Drop rows with no ID
) t
WHERE flag_last = 1;                               -- Keep only the most recent record
```

**Techniques used:**

**`TRIM()`** — removes leading/trailing spaces. The raw CSV has `' Jon'` and `'Yang '`. Without trimming, `WHERE first_name = 'Jon'` fails.

**`UPPER(TRIM(...))`** — normalize before comparing. Handles `'m'`, `'M'`, `' M'` — all mean Male.

**`CASE WHEN`** — decode source abbreviations into readable values. `'S'` → `'Single'`, `'M'` → `'Married'`. The `ELSE 'n/a'` catches anything unexpected rather than leaving a null.

**Deduplication with `ROW_NUMBER()`:**
```sql
ROW_NUMBER() OVER (PARTITION BY cst_id ORDER BY cst_create_date DESC)
```
- `PARTITION BY cst_id` — rank within each customer group
- `ORDER BY cst_create_date DESC` — most recent record gets rank 1
- `WHERE flag_last = 1` — keep only rank 1 (most recent)

If a customer appears 3 times in Bronze (data entry errors, system migrations), Silver keeps only their most recent record.

---

### Table 2: `silver.crm_prd_info` — Key Splitting + SCD End Date Derivation

```sql
SELECT
    prd_id,
    REPLACE(SUBSTRING(prd_key, 1, 5), '-', '_') AS cat_id,  -- Extract category
    SUBSTRING(prd_key, 7, LEN(prd_key))          AS prd_key, -- Extract product key
    prd_nm,
    ISNULL(prd_cost, 0)                          AS prd_cost,
    CASE
        WHEN UPPER(TRIM(prd_line)) = 'M' THEN 'Mountain'
        WHEN UPPER(TRIM(prd_line)) = 'R' THEN 'Road'
        WHEN UPPER(TRIM(prd_line)) = 'S' THEN 'Other Sales'
        WHEN UPPER(TRIM(prd_line)) = 'T' THEN 'Touring'
        ELSE 'n/a'
    END AS prd_line,
    CAST(prd_start_dt AS DATE)                   AS prd_start_dt,
    CAST(
        LEAD(prd_start_dt) OVER (PARTITION BY prd_key ORDER BY prd_start_dt) - 1
        AS DATE
    )                                             AS prd_end_dt
FROM bronze.crm_prd_info;
```

**Key splitting:** The raw `prd_key` looks like `'CO-RF-FR-R92B-58'`.
- Characters 1-5: `'CO-RF'` → replace `-` with `_` → `'CO_RF'` = the category ID
- Characters 7+: `'FR-R92B-58'` = the actual product key

The source encoded two pieces of information in one column. Silver splits them apart.

**`ISNULL(prd_cost, 0)`** — cost can't be null in Silver. If the source didn't provide it, default to 0.

**SCD end date with `LEAD()`:**
```sql
LEAD(prd_start_dt) OVER (PARTITION BY prd_key ORDER BY prd_start_dt) - 1
```
`LEAD()` looks at the *next row's* `prd_start_dt` within the same `prd_key`. Subtract 1 day → that's the last valid day for the current version. The final version gets `NULL` (no next row exists) — meaning it's still current. This creates a proper SCD Type 2 validity range automatically.

---

### Table 3: `silver.crm_sales_details` — Date Casting + Financial Consistency

```sql
-- Date conversion: INT stored as YYYYMMDD → DATE
CASE
    WHEN sls_order_dt = 0 OR LEN(sls_order_dt) != 8 THEN NULL
    ELSE CAST(CAST(sls_order_dt AS VARCHAR) AS DATE)
END AS sls_order_dt,

-- Sales recalculation: fix bad or missing values
CASE
    WHEN sls_sales IS NULL OR sls_sales <= 0
         OR sls_sales != sls_quantity * ABS(sls_price)
        THEN sls_quantity * ABS(sls_price)
    ELSE sls_sales
END AS sls_sales,

-- Price derivation: derive from sales/quantity if invalid
CASE
    WHEN sls_price IS NULL OR sls_price <= 0
        THEN sls_sales / NULLIF(sls_quantity, 0)
    ELSE sls_price
END AS sls_price
```

**Date casting:** Bronze stores dates as `INT` (e.g., `20101229`). SQL Server can't natively cast `INT` → `DATE`, so: `INT → VARCHAR → DATE`. The guard (`= 0 OR LEN != 8`) catches corrupt values like `0`, `99999999` before the cast fails.

**Financial consistency:** The rule `sales = quantity * price` must hold. If it doesn't (bad source data), recalculate from quantity and price. `ABS(sls_price)` handles negative prices (a source system bug).

**`NULLIF(sls_quantity, 0)`** — prevents division by zero when deriving price. `NULLIF(x, 0)` returns NULL if x=0, which causes the division to return NULL instead of crashing.

---

### Table 4: `silver.erp_cust_az12` — Key Cleaning + Birthdate Validation

```sql
CASE
    WHEN cid LIKE 'NAS%' THEN SUBSTRING(cid, 4, LEN(cid))
    ELSE cid
END AS cid,                        -- Strip 'NAS' prefix to match CRM key format

CASE
    WHEN bdate > GETDATE() THEN NULL
    ELSE bdate
END AS bdate,                      -- Future birthdates are clearly wrong → NULL
```

The ERP stores customer IDs as `'NASAW00011000'`. The CRM uses `'AW00011000'`. To JOIN them in Gold, the keys must match. Silver strips the `'NAS'` prefix from ERP IDs.

This is **key harmonization** — aligning foreign keys across source systems so they can be joined later.

---

### Table 5: `silver.erp_loc_a101` — Country Code Normalization

```sql
REPLACE(cid, '-', '') AS cid,     -- 'AW-00011000' → 'AW00011000' (match CRM format)
CASE
    WHEN TRIM(cntry) = 'DE'          THEN 'Germany'
    WHEN TRIM(cntry) IN ('US', 'USA') THEN 'United States'
    WHEN TRIM(cntry) = '' OR cntry IS NULL THEN 'n/a'
    ELSE TRIM(cntry)
END AS cntry
```

Another key harmonization: ERP stores `'AW-00011000'` with a dash. CRM uses `'AW00011000'`. Remove the dash.

Country codes decoded: `'DE'` → `'Germany'`, `'US'`/`'USA'` → `'United States'`. Analysts want readable values, not ISO codes.

---

### Silver Transformation Summary

| Problem in Bronze | Silver Solution |
|------------------|-----------------|
| Trailing spaces in strings | `TRIM()` |
| Abbreviation codes (`'M'`, `'F'`, `'S'`) | `CASE WHEN` decode |
| Duplicate customer records | `ROW_NUMBER()` + `WHERE flag_last = 1` |
| Category embedded in product key | `SUBSTRING()` + `REPLACE()` |
| Dates stored as INT | `CAST(CAST(x AS VARCHAR) AS DATE)` |
| Null/invalid costs | `ISNULL(prd_cost, 0)` |
| Inconsistent sales figures | Recalculate: `quantity * ABS(price)` |
| Future birthdates | `CASE WHEN bdate > GETDATE() THEN NULL` |
| Mismatched keys across systems | `SUBSTRING()` / `REPLACE()` |
| Missing country codes | `CASE WHEN NULL OR '' THEN 'n/a'` |

---

## Module 6: Gold Layer — Views, Star Schema Assembly, Surrogate Keys

Gold is where everything comes together. You've cleaned each source in Silver independently — now you join them, assign business keys, and present a unified model.

Gold is implemented as **SQL Views**, not tables.

### Why Views and Not Tables?

| Views | Tables |
|-------|--------|
| No data stored — reads live from Silver | Data physically stored |
| No load step needed | Requires a load procedure |
| Always in sync with Silver | Can go stale |
| Zero storage cost | Storage cost |
| Slightly slower at query time | Faster (pre-materialized) |

For this project's scale, views are the right call. In production with billions of rows, you'd materialize Gold into physical tables (or use a columnar store like Snowflake/BigQuery where this is done automatically).

---

### `gold.dim_customers` — Cross-Source Integration

```sql
CREATE VIEW gold.dim_customers AS
SELECT
    ROW_NUMBER() OVER (ORDER BY cst_id)  AS customer_key,  -- Surrogate key
    ci.cst_id                            AS customer_id,
    ci.cst_key                           AS customer_number,
    ci.cst_firstname                     AS first_name,
    ci.cst_lastname                      AS last_name,
    la.cntry                             AS country,         -- from ERP
    ci.cst_marital_status                AS marital_status,
    CASE
        WHEN ci.cst_gndr != 'n/a' THEN ci.cst_gndr          -- CRM wins
        ELSE COALESCE(ca.gen, 'n/a')                         -- ERP fallback
    END                                  AS gender,
    ca.bdate                             AS birthdate,       -- from ERP
    ci.cst_create_date                   AS create_date
FROM silver.crm_cust_info ci
LEFT JOIN silver.erp_cust_az12 ca ON ci.cst_key = ca.cid
LEFT JOIN silver.erp_loc_a101  la ON ci.cst_key = la.cid;
```

**`LEFT JOIN` not `INNER JOIN`:** Every customer in CRM appears in the dimension, even if ERP has no matching record. You don't silently drop customers just because ERP data is incomplete.

**Conflict resolution:** Both CRM and ERP have gender. CRM is the system of record for customer data, so it wins. ERP is a fallback only when CRM says `'n/a'`. This is a **business rule** encoded in SQL.

**Column renaming:** `cst_firstname` → `first_name`. Gold uses business language, not source system column names. Analysts don't need to know this came from CRM.

---

### `gold.dim_products` — SCD Filtering + Category Enrichment

```sql
CREATE VIEW gold.dim_products AS
SELECT
    ROW_NUMBER() OVER (ORDER BY pn.prd_start_dt, pn.prd_key) AS product_key,
    pn.prd_id        AS product_id,
    pn.prd_key       AS product_number,
    pn.prd_nm        AS product_name,
    pn.cat_id        AS category_id,
    pc.cat           AS category,        -- from ERP category table
    pc.subcat        AS subcategory,
    pc.maintenance   AS maintenance,
    pn.prd_cost      AS cost,
    pn.prd_line      AS product_line,
    pn.prd_start_dt  AS start_date
FROM silver.crm_prd_info pn
LEFT JOIN silver.erp_px_cat_g1v2 pc ON pn.cat_id = pc.id
WHERE pn.prd_end_dt IS NULL;            -- Only current products
```

**`WHERE prd_end_dt IS NULL`** — Silver contains the full product history (all versions). Gold exposes only current products. Historical versions sit in Silver and can be queried directly when needed.

**Surrogate key ordering:** `ORDER BY prd_start_dt, prd_key` — deterministic ordering ensures the same product always gets the same surrogate key on every view refresh. This matters for consistency.

---

### `gold.fact_sales` — The Central Event Table

```sql
CREATE VIEW gold.fact_sales AS
SELECT
    sd.sls_ord_num   AS order_number,
    pr.product_key   AS product_key,    -- warehouse surrogate key
    cu.customer_key  AS customer_key,   -- warehouse surrogate key
    sd.sls_order_dt  AS order_date,
    sd.sls_ship_dt   AS shipping_date,
    sd.sls_due_dt    AS due_date,
    sd.sls_sales     AS sales_amount,
    sd.sls_quantity  AS quantity,
    sd.sls_price     AS price
FROM silver.crm_sales_details sd
LEFT JOIN gold.dim_products  pr ON sd.sls_prd_key = pr.product_number
LEFT JOIN gold.dim_customers cu ON sd.sls_cust_id = cu.customer_id;
```

**The join logic:** `crm_sales_details` stores the original `sls_prd_key` and `sls_cust_id` from the source. We look those up in the Gold dimensions to replace them with warehouse surrogate keys (`product_key`, `customer_key`). Analysts join using these integer surrogate keys — fast and stable.

**`LEFT JOIN` again:** sales records are preserved even if a product or customer record is missing in the dimension (orphaned facts). The data quality checks will catch these.

---

## Module 7: Data Quality — The Test Scripts

Data quality is not optional. It's the difference between a warehouse people trust and one they ignore. Your project has two test scripts.

### The Philosophy: Expectation-Based Testing

Every check follows the same pattern:
```
Run a query → If it returns rows → Something is wrong
```

Expectation: No Results. Any result = a data problem to investigate.

This is exactly like unit testing in software: you write assertions, and a passing test produces no output.

---

### `tests/quality_checks_silver.sql` — Silver Checks

**1. Duplicate / Null Primary Keys**
```sql
SELECT cst_id, COUNT(*)
FROM silver.crm_cust_info
GROUP BY cst_id
HAVING COUNT(*) > 1 OR cst_id IS NULL;
```
If Silver's deduplication worked, this returns nothing. Any result means a customer appears more than once — the surrogate key in Gold would be non-unique.

**2. Unwanted Spaces**
```sql
SELECT cst_key FROM silver.crm_cust_info
WHERE cst_key != TRIM(cst_key);
```
Verifies `TRIM()` worked. If `'AW00011000 '` slipped through, joins to ERP would silently fail.

**3. Data Standardization**
```sql
SELECT DISTINCT cst_marital_status FROM silver.crm_cust_info;
```
You expect to see only `'Single'`, `'Married'`, `'n/a'`. If `'S'` or `'M'` appears, the CASE WHEN normalization failed.

**4. Invalid Date Orders**
```sql
SELECT * FROM silver.crm_sales_details
WHERE sls_order_dt > sls_ship_dt OR sls_order_dt > sls_due_dt;
```
An order can't ship before it was placed. This catches date corruption.

**5. Financial Consistency**
```sql
SELECT DISTINCT sls_sales, sls_quantity, sls_price
FROM silver.crm_sales_details
WHERE sls_sales != sls_quantity * sls_price
   OR sls_sales IS NULL OR sls_quantity IS NULL OR sls_price IS NULL
   OR sls_sales <= 0 OR sls_quantity <= 0 OR sls_price <= 0;
```
Validates that the recalculation logic in Silver worked: `sales = quantity * price` must hold for every row.

**6. Birthdate Range**
```sql
SELECT DISTINCT bdate FROM silver.erp_cust_az12
WHERE bdate < '1924-01-01' OR bdate > GETDATE();
```
No one born before 1924 is a plausible customer. No one born in the future exists. Catches bad data that slipped past the `GETDATE()` guard.

---

### `tests/quality_checks_gold.sql` — Gold Checks

**1. Surrogate Key Uniqueness**
```sql
SELECT customer_key, COUNT(*) AS duplicate_count
FROM gold.dim_customers
GROUP BY customer_key
HAVING COUNT(*) > 1;
```
`ROW_NUMBER()` should guarantee uniqueness — but you verify it. A duplicate surrogate key would corrupt every fact-to-dim join.

**2. Referential Integrity**
```sql
SELECT *
FROM gold.fact_sales f
LEFT JOIN gold.dim_customers c ON c.customer_key = f.customer_key
LEFT JOIN gold.dim_products  p ON p.product_key  = f.product_key
WHERE p.product_key IS NULL OR c.customer_key IS NULL;
```
The fact table's foreign keys must resolve to actual dimension rows. Any `NULL` after the LEFT JOIN means an orphaned fact — a sale referencing a customer or product that doesn't exist in the dim. These are invisible data gaps that silently reduce your sales totals.

---

### When to Run These Checks

```
After Bronze load  → (optional) basic row count check
After Silver load  → Run quality_checks_silver.sql
After Gold DDL     → Run quality_checks_gold.sql
Before reporting   → Run both
```

In production, these checks would be automated — run as part of the pipeline and alert on failure.

---

## Module 8: Putting It All Together — Execution Order, Dependency Graph, Ops

### The Dependency Graph

Every script depends on the previous one. Run them out of order and things break.

```
init_database.sql
      │
      ▼
ddl_bronze.sql          ← creates bronze tables
      │
      ▼
proc_load_bronze.sql    ← defines the bronze load procedure
      │
      ▼
EXEC bronze.load_bronze ← actually loads the CSV data
      │
      ▼
quality_checks_bronze   ← (optional: row counts, spot checks)
      │
      ▼
ddl_silver.sql          ← creates silver tables
      │
      ▼
proc_load_silver.sql    ← defines the silver load procedure
      │
      ▼
EXEC silver.load_silver ← transforms bronze → silver
      │
      ▼
quality_checks_silver.sql ← verify silver is clean
      │
      ▼
ddl_gold.sql            ← creates gold views (reads live from silver)
      │
      ▼
quality_checks_gold.sql ← verify star schema integrity
```

### First-Time Setup (Run Once)

```sql
-- 1. Create the database and schemas
-- Execute: scripts/init_database.sql

-- 2. Create bronze tables
-- Execute: scripts/bronze/ddl_bronze.sql

-- 3. Create bronze load procedure
-- Execute: scripts/bronze/proc_load_bronze.sql

-- 4. Create silver tables
-- Execute: scripts/silver/ddl_silver.sql

-- 5. Create silver load procedure
-- Execute: scripts/silver/proc_load_silver.sql

-- 6. Create gold views
-- Execute: scripts/gold/ddl_gold.sql
```

### Daily / Recurring Refresh (Run on Each Data Update)

```sql
-- Load bronze from CSVs
EXEC bronze.load_bronze;

-- Transform bronze → silver
EXEC silver.load_silver;

-- Gold is automatic (views read live from silver)

-- Validate
-- Execute: tests/quality_checks_silver.sql
-- Execute: tests/quality_checks_gold.sql
```

---

### The Full Data Flow in One Picture

```
[CRM: cust_info.csv]     ──BULK INSERT──► bronze.crm_cust_info
[CRM: prd_info.csv]      ──BULK INSERT──► bronze.crm_prd_info      ─┐
[CRM: sales_details.csv] ──BULK INSERT──► bronze.crm_sales_details  │
[ERP: CUST_AZ12.csv]     ──BULK INSERT──► bronze.erp_cust_az12      │  TRUNCATE+INSERT
[ERP: LOC_A101.csv]      ──BULK INSERT──► bronze.erp_loc_a101       │  (with transforms)
[ERP: PX_CAT_G1V2.csv]   ──BULK INSERT──► bronze.erp_px_cat_g1v2  ─┘
                                                │
                                                ▼
                              silver.crm_cust_info     ─┐
                              silver.crm_prd_info       │
                              silver.crm_sales_details  │  SELECT + JOIN
                              silver.erp_cust_az12      │  (views)
                              silver.erp_loc_a101      ─┘
                              silver.erp_px_cat_g1v2
                                                │
                                                ▼
                              gold.dim_customers  (VIEW over silver)
                              gold.dim_products   (VIEW over silver)
                              gold.fact_sales     (VIEW over gold dims + silver)
                                                │
                                                ▼
                                        Analysts / BI Tools
```

---

### Key Engineering Principles in This Project

| Principle | How It's Applied |
|-----------|-----------------|
| **Idempotency** | DDL scripts use `IF EXISTS DROP`. Procedures use `CREATE OR ALTER`. Load steps `TRUNCATE` before insert. Run anything twice — same result. |
| **Separation of concerns** | Bronze = ingestion only. Silver = cleaning only. Gold = business logic only. Never mix. |
| **Observability** | Every table load prints start time, end time, duration. Errors print message, number, state. |
| **Auditability** | Bronze preserves raw source. Silver adds `dwh_create_date`. You can always trace a Gold row back to its source. |
| **Fail loudly** | `BEGIN TRY / BEGIN CATCH` catches errors and prints them. The pipeline doesn't silently succeed with bad data. |
| **No backward writes** | Gold reads from Silver. Silver reads from Bronze. Data only flows forward. |

---

### What's Missing in This Project (Production Gaps)

This is a learning project. In production you'd also have:

| Gap | Production Solution |
|-----|-------------------|
| No `dim_date` | Generate a date dimension table with year/quarter/month/week/day attributes |
| Manual execution | Orchestration tool (Azure Data Factory, Apache Airflow, dbt) to schedule and chain runs |
| Hardcoded file paths | Parameterized paths or external config |
| No incremental loading | Delta/incremental load for large tables (don't full-reload 100M rows daily) |
| No row count validation | Assert `COUNT(silver) == COUNT(bronze)` after each load |
| No data lineage tracking | Tool like Apache Atlas or dbt docs to track column-level lineage |
| Views only in Gold | Materialized tables or indexed views for large-scale performance |
