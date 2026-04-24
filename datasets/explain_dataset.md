# Dataset Dictionary — Adventure Works Cycles

## Business Context

This dataset represents **Adventure Works Cycles**, a fictional bicycle retail company that sells bikes, accessories, clothing, and components globally. Data is sourced from two systems:

- **CRM** — Customer-facing system: sales transactions, customer profiles, product catalog
- **ERP** — Back-office system: customer demographics, geographic locations, product categorization

---

## Source Tables

### CRM Source (`datasets/source_crm/`)

#### `cust_info.csv` — Customer Master
Stores customer registration data from the CRM system.

| Column | Type | Description |
|---|---|---|
| `cst_id` | INT | Internal numeric customer ID (e.g. `11000`) |
| `cst_key` | VARCHAR | Business customer code (e.g. `AW00011000`) — used as join key across systems |
| `cst_firstname` | VARCHAR | Customer first name — has leading/trailing spaces, requires `TRIM()` |
| `cst_lastname` | VARCHAR | Customer last name — same whitespace issue |
| `cst_marital_status` | CHAR | Marital status: `M` = Married, `S` = Single |
| `cst_gndr` | CHAR | Gender: `M` = Male, `F` = Female — conflicts with ERP full-word format |
| `cst_create_date` | DATE | Date the customer was registered in the CRM |

---

#### `prd_info.csv` — Product Catalog
Stores product definitions with versioned pricing (Slowly Changing Dimension Type 2).

| Column | Type | Description |
|---|---|---|
| `prd_id` | INT | Internal numeric product ID |
| `prd_key` | VARCHAR | Product SKU (e.g. `AC-HE-HL-U509-R`) — first 5 chars encode category+subcategory, joins to ERP `PX_CAT_G1V2.ID` after replacing `-` with `_` |
| `prd_nm` | VARCHAR | Product name (e.g. `Sport-100 Helmet- Red`) |
| `prd_cost` | INT | Unit cost to the company — some rows are NULL (data quality issue) |
| `prd_line` | CHAR | Sales channel / product line: `R` = Road, `M` = Mountain, `S` = Sport, `T` = Touring |
| `prd_start_dt` | DATE | Start date of this product version — SCD2 pattern |
| `prd_end_dt` | DATE | End date of this product version — NULL means currently active |

> **Note:** The same `prd_key` appears multiple times with different costs and date ranges, representing price history over time (SCD Type 2).

---

#### `sales_details.csv` — Sales Transactions
Stores individual line items for every sales order.

| Column | Type | Description |
|---|---|---|
| `sls_ord_num` | VARCHAR | Sales order number (e.g. `SO43697`) — one order can have multiple line items |
| `sls_prd_key` | VARCHAR | Product SKU sold — joins to `prd_info.prd_key` |
| `sls_cust_id` | INT | Customer who placed the order — joins to `cust_info.cst_id` |
| `sls_order_dt` | INT | Order date stored as integer `YYYYMMDD` — must be cast to DATE |
| `sls_ship_dt` | INT | Ship date stored as integer `YYYYMMDD` — must be cast to DATE |
| `sls_due_dt` | INT | Payment due date stored as integer `YYYYMMDD` — must be cast to DATE |
| `sls_sales` | INT | Total revenue for the line item — should equal `sls_quantity × sls_price` |
| `sls_quantity` | INT | Number of units ordered |
| `sls_price` | INT | Unit selling price to the customer — margin = `sls_price - prd_cost` |

---

### ERP Source (`datasets/source_erp/`)

#### `CUST_AZ12.csv` — Customer Demographics
Stores customer birth date and gender from the ERP system.

| Column | Type | Description |
|---|---|---|
| `CID` | VARCHAR | ERP customer ID (e.g. `NASAW00011000`) — strip `NAS` prefix to get `AW00011000`, which maps to CRM `cst_key` |
| `BDATE` | DATE | Date of birth — use to calculate customer age segments |
| `GEN` | VARCHAR | Gender: `Male` / `Female` — full words, must be standardized with CRM's `M`/`F` |

---

#### `LOC_A101.csv` — Customer Location
Stores country of residence per customer from the ERP system.

| Column | Type | Description |
|---|---|---|
| `CID` | VARCHAR | ERP customer ID (e.g. `AW-00011000`) — strip the hyphen to get `AW00011000`, mapping to CRM `cst_key` |
| `CNTRY` | VARCHAR | Country of residence (e.g. `Australia`, `US`) — may have inconsistent country name formats |

---

#### `PX_CAT_G1V2.csv` — Product Category Master
Stores the product category hierarchy from the ERP system.

| Column | Type | Description |
|---|---|---|
| `ID` | VARCHAR | Category+subcategory code (e.g. `AC_HE`) — joins to first 5 chars of `prd_key` after replacing `-` with `_` |
| `CAT` | VARCHAR | Top-level category: `Accessories`, `Bikes`, `Clothing`, `Components` |
| `SUBCAT` | VARCHAR | Subcategory (e.g. `Helmets`, `Mountain Bikes`, `Road Bikes`, `Jerseys`) |
| `MAINTENANCE` | VARCHAR | Whether the product requires periodic maintenance: `Yes` / `No` |

---

## Cross-System Join Keys

| CRM Field | ERP Field | Transformation Needed |
|---|---|---|
| `cust_info.cst_key` (e.g. `AW00011000`) | `CUST_AZ12.CID` (e.g. `NASAW00011000`) | Strip `NAS` prefix from ERP |
| `cust_info.cst_key` (e.g. `AW00011000`) | `LOC_A101.CID` (e.g. `AW-00011000`) | Remove hyphen from ERP |
| `prd_info.prd_key` first 5 chars (e.g. `AC-HE`) | `PX_CAT_G1V2.ID` (e.g. `AC_HE`) | Replace `-` with `_` |

---

## Known Data Quality Issues

| Issue | Table | Recommended Fix |
|---|---|---|
| Customer ID format mismatch (prefix/hyphen) | `CUST_AZ12`, `LOC_A101` | Normalize CID in silver layer using `REPLACE` / `SUBSTRING` |
| Gender encoding mismatch (`M`/`F` vs `Male`/`Female`) | `cust_info`, `CUST_AZ12` | Standardize to full words in silver layer |
| Dates stored as integers (`YYYYMMDD`) | `sales_details` | Cast to DATE in silver layer |
| Leading/trailing whitespace in names | `cust_info` | Apply `TRIM()` in silver layer |
| NULL product costs | `prd_info` | Investigate; consider inheriting cost from prior active version |
| Inconsistent country naming | `LOC_A101` | Normalize country names (e.g. `US` → `United States`) |

---

## Key Business Metrics Derivable from This Data

| Metric | Formula / Source |
|---|---|
| **Gross Margin** | `sls_price - prd_cost` per line item |
| **Revenue** | `sls_sales` (or `sls_quantity × sls_price`) |
| **Shipping Lead Time** | `sls_ship_dt - sls_order_dt` in days |
| **Customer Age** | Current date - `BDATE` |
| **Customer Lifetime Value** | Sum of `sls_sales` per `sls_cust_id` |
