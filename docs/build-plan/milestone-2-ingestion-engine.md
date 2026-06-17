# Milestone 2 – Trial Balance Ingestion Engine

## Objective
Build a deterministic ingestion engine capable of accepting trial balances exported from any ERP system and transforming them into a standardised internal format for downstream processing.

This milestone establishes the data entry point of the Financial Statements Operating System (FSOS).

The output of this phase is a validated, normalised Trial Balance dataset that can be consumed by the Mapping Engine.

---

# Problem Statement

Every ERP exports data differently.

Examples:

* SAP S/4HANA
* Oracle NetSuite
* Oracle Fusion
* Microsoft Dynamics
* Xero
* QuickBooks
* Legacy Excel-based accounting systems

Column names, account structures, and export formats vary significantly.

The system therefore requires a normalisation layer before financial statement generation can begin.

---

# Inputs

Supported Version 1 Inputs:

### Excel

```text
.xlsx
.xls
```

### CSV

```text
.csv
```

### Manual Trial Balance Templates

Standardized Excel template provided by FSOS.

---

# Expected Minimum Fields

The ingestion engine must extract:

| Field            | Required |
| ---------------- | -------- |
| Account Code     | Yes      |
| Account Name     | Yes      |
| Debit            | Optional |
| Credit           | Optional |
| Balance          | Yes      |
| Reporting Period | Yes      |

---

# Internal Canonical Structure

Regardless of source system, all data will be converted into:

```json
{
  "account_code": "1000",
  "account_name": "Cash at Bank",
  "balance": 150000.00,
  "period": "2025-12"
}
```

This becomes the standard internal representation used throughout the platform.

---

# Validation Rules

Before acceptance, the ingestion engine must validate:

## Rule 1 – Mandatory Columns

Required fields must exist.

Failure results in rejection.

---

## Rule 2 – Numeric Validation

Balances must be numeric.

Failure results in rejection.

---

## Rule 3 – Duplicate Accounts

Duplicate account codes detected.

System flags duplicates for review.

---

## Rule 4 – Trial Balance Integrity

Verify:

```text
Total Debits = Total Credits
```

or

```text
Net Balance = 0
```

depending on source structure.

Failure results in rejection.

---

## Rule 5 – Empty Rows

Automatically remove:

* Blank rows
* Totals rows
* Formatting rows

---

# Processing Flow

```text
Upload File
    ↓
Read Workbook
    ↓
Identify Columns
    ↓
Validate Structure
    ↓
Normalise Data
    ↓
Validate Balances
    ↓
Create Standard Dataset
    ↓
Store Internal TB
```

---

# Outputs

Version 1 Output:

```text
normalised_tb.csv
```

Future Version:

```text
normalised_tb.parquet
```

---

# Logging Requirements

Every ingestion run must generate:

```text
run_id
timestamp
source_file
row_count
validation_status
error_count
```

Example:

```json
{
  "run_id": "TB-2026-0001",
  "rows": 542,
  "status": "PASS",
  "errors": 0
}
```

---

# Error Handling

The engine must never silently fail.

All failures must produce explicit messages.

Examples:

```text
Missing Account Code column

Duplicate account detected

Trial Balance does not balance

Invalid numeric value
```

---

# Success Criteria

Milestone 2 is complete when:

✓ User uploads Excel Trial Balance

✓ System reads file automatically

✓ System validates structure

✓ System normalizes data

✓ System confirms Trial Balance integrity

✓ System produces standardized output dataset

✓ No manual manipulation required

---

# Deliverables

Private Repository Components:

```text
src/
└── ingestion/
    ├── loader.py
    ├── validator.py
    ├── normalizer.py
    └── logger.py
```

Output:

```text
normalised_tb.csv
```

This standardized Trial Balance becomes the sole input into Milestone 3 – Mapping Engine.
