# Phase 1 Specification: Trial Balance Ingestion Engine

## Purpose
The Trial Balance Ingestion Engine is the first component of the Financial Statement Engine (FSE).

Its purpose is to ingest trial balances from different companies and transform them into a standardized internal data structure that can be consumed by downstream modules including:

* Mapping Engine
* Financial Statement Generator
* Notes Generator
* Audit Support Package
* AI Review Layer

This module performs no accounting judgement.

It is responsible only for validation, normalisation and standardisation.

---

# Objectives
The engine shall:
1. Accept trial balances from Excel workbooks.
2. Validate structural integrity.
3. Identify data quality issues.
4. Normalise account data.
5. Produce a standardised output dataset.
6. Generate an audit trail of ingestion results.

---

# Scope

## Included
* Excel file ingestion
* Multi-sheet support
* Trial balance validation
* Data normalisation
* Error reporting
* Standardised output generation

## Excluded
* Account mapping
* Financial statement generation
* Note disclosures
* AI interpretation
* Journal entry creation

These functions belong to later phases.

---

# Supported Input Formats

## Version 1
Accepted file types:
* .xlsx
* .xlsm

Maximum file size:
* 25 MB

Maximum rows:
* 100,000

---

# Expected Trial Balance Structure
Minimum required fields:
| Field        | Required |
| ------------ | -------- |
| Account Code | Yes      |
| Account Name | Yes      |
| Balance      | Yes      |

Optional fields:
| Field        |
| ------------ |
| Entity       |
| Department   |
| Cost Centre  |
| Currency     |
| Period       |
| Year         |
| Account Type |

---

# Sample Input
| Account Code | Account Name   | Balance |
| ------------ | -------------- | ------- |
| 1000         | Cash at Bank   | 150000  |
| 2000         | Trade Payables | -45000  |
| 3000         | Share Capital  | -100000 |

---

# Validation Rules

## Rule 1: Mandatory Columns

System verifies:
* Account Code exists
* Account Name exists
* Balance exists

Failure Result:
Critical Error

Processing stops.

---

## Rule 2: Blank Account Codes

Account Code cannot be blank.

Failure Result:
Critical Error

Processing stops.

---

## Rule 3: Duplicate Account Codes

System identifies duplicate account codes.

Failure Result:
Warning

Continue processing.

Duplicates logged.

---

## Rule 4: Non-Numeric Balances

Balance field must be numeric.

Failure Result:
Critical Error

Processing stops.

---

## Rule 5: Trial Balance Equality Check

Total Debits must equal Total Credits.

Validation:
Sum(Balance) = 0

Tolerance:
0.01

Failure Result:
Critical Error

Processing stops.

---

## Rule 6: Empty File Detection

If no valid records exist:

Failure Result:
Critical Error
Processing stops.

---

# Normalization Rules

## Account Code

Convert to string.

Examples:
1000 → "1000"
0010 → "0010"

Leading zeros preserved.

---

## Account Name

Trim spaces.

Remove non-printable characters.

Standardize Unicode encoding.

---

## Balance

Convert to decimal.

Store to 2 decimal places.

Examples:
1000
1000.00
-500.50

---

# Internal Standard Output Schema

Every imported trial balance will be transformed into:

| Field              |
| ------------------ |
| account_code       |
| account_name       |
| balance            |
| source_file        |
| upload_timestamp   |
| ingestion_batch_id |

Example:

{
"account_code": "1000",
"account_name": "Cash at Bank",
"balance": 150000.00,
"source_file": "TB_2025.xlsx",
"upload_timestamp": "2026-06-17T10:00:00",
"ingestion_batch_id": "BATCH001"
}

---

# Audit Trail Requirements

Each ingestion run must generate:
* Batch ID
* Upload timestamp
* Source file name
* Record count
* Validation results
* Error log
* Warning log

Audit trail must be immutable.

---

# Output Files

Successful processing generates:
1. standardized_tb.csv
Standardized trial balance.

2. validation_report.csv
Validation findings.

3. ingestion_log.json
Execution metadata.

---

# User Workflow

Step 1
User uploads trial balance.

Step 2
Validation engine executes.

Step 3
Errors displayed.

Step 4

If validation passes:
Standardized dataset generated.

Step 5
Dataset passed to Mapping Engine.

---

# Success Criteria

A trial balance is considered successfully ingested when:

* All mandatory fields exist
* No critical validation errors exist
* Trial balance balances
* Standardized dataset created
* Audit log generated

---

# Deliverables

Version 1 Deliverables:

* Excel Reader
* Validation Engine
* Normalization Engine
* Error Reporting Engine
* Standardized Output Generator

Phase Status:

Ready for Development
