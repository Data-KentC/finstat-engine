# Milestone 3 – Financial Statement Mapping Engine

## Objective

Build a deterministic mapping engine that converts company-specific Trial Balance accounts into standardized Financial Statement line items.

This milestone transforms raw accounting data into a structure suitable for generating audited financial statements.

The Mapping Engine serves as the translation layer between:

```text
Company Chart of Accounts
                ↓
Standard Financial Statement Structure
```

Without this layer, automated financial statement generation is impossible.

---

# Problem Statement

Every company uses a different Chart of Accounts.

Example:

Company A:

```text
1000 Cash at Bank
1100 Trade Receivables
1200 Inventory
```

Company B:

```text
001 Bank Current Account
002 Accounts Receivable
003 Stock on Hand
```

Both companies represent identical economic activity but use different account numbering and naming conventions.

The Mapping Engine standardizes these accounts into a common reporting structure.

---

# Core Principle

The Mapping Engine must be:

```text
Deterministic
Explainable
Auditable
Repeatable
```

No AI decision-making.

No probabilistic classification.

Every mapping must be traceable.

---

# Inputs

From Milestone 2:

```text
normalized_tb.csv
```

Example:

| Account Code | Account Name      | Balance |
| ------------ | ----------------- | ------- |
| 1000         | Cash at Bank      | 150000  |
| 1100         | Trade Receivables | 90000   |
| 1200         | Inventory         | 70000   |

---

# Mapping Library

The system maintains a company-specific mapping library.

Example:

| Account Code | Account Name      | FS Line Item              |
| ------------ | ----------------- | ------------------------- |
| 1000         | Cash at Bank      | Cash and Cash Equivalents |
| 1100         | Trade Receivables | Trade Receivables         |
| 1200         | Inventory         | Inventories               |

---

# Internal Financial Statement Taxonomy

Version 1 standard taxonomy:

## Balance Sheet

### Assets

```text
Cash and Cash Equivalents
Trade Receivables
Other Receivables
Inventories
Prepayments
Property Plant Equipment
Intangible Assets
Investment Property
Deferred Tax Assets
Other Assets
```

### Liabilities

```text
Trade Payables
Accruals
Borrowings
Lease Liabilities
Deferred Tax Liabilities
Other Liabilities
```

### Equity

```text
Share Capital
Retained Earnings
Reserves
Current Year Profit
```

---

## Income Statement

```text
Revenue
Cost of Sales
Gross Profit

Administrative Expenses
Selling Expenses
Finance Costs
Other Income
Other Expenses

Profit Before Tax
Income Tax Expense
Profit After Tax
```

---

# Mapping Workflow

```text
Normalized TB
      ↓
Read Mapping Table
      ↓
Validate Mapping Completeness
      ↓
Assign FS Categories
      ↓
Aggregate Balances
      ↓
Generate Mapped Trial Balance
```

---

# Mapping Validation Rules

## Rule 1 – Every Account Must Map

No account may remain unmapped.

Failure:

```text
Account 7310 Office Pantry Expense not mapped
```

---

## Rule 2 – One-to-One Assignment

Each account can only map to one FS category.

Failure:

```text
Account mapped to multiple categories
```

---

## Rule 3 – Duplicate Mapping Detection

System identifies duplicate entries.

Failure:

```text
Account 1000 appears multiple times
```

---

## Rule 4 – Balance Preservation

Total TB Balance must equal:

```text
Total Mapped Balance
```

No balances may disappear.

---

# Audit Requirements

Every mapping action must be logged.

Example:

```json
{
  "account_code": "1100",
  "account_name": "Trade Receivables",
  "mapped_to": "Trade Receivables",
  "mapping_version": "v1.0"
}
```

---

# Reclassification Support

Version 1 must support audit adjustments.

Example:

Original Mapping:

```text
Motor Vehicle Expense
→ Administrative Expenses
```

Audit Reclassification:

```text
Motor Vehicle Expense
→ Cost of Sales
```

System must allow:

```text
Version 1
Version 2
Version 3
```

without modifying historical records.

---

# Mapping Version Control

Each mapping library receives:

```text
mapping_id
version
effective_date
prepared_by
approved_by
```

Example:

```json
{
  "mapping_id": "CLIENT001",
  "version": "2.0",
  "effective_date": "2026-03-31"
}
```

---

# Output Structure

Mapped Trial Balance:

| Account Code | Account Name      | FS Category               | Balance |
| ------------ | ----------------- | ------------------------- | ------- |
| 1000         | Cash at Bank      | Cash and Cash Equivalents | 150000  |
| 1100         | Trade Receivables | Trade Receivables         | 90000   |
| 1200         | Inventory         | Inventories               | 70000   |

---

# Deliverables

Output File:

```text
mapped_tb.csv
```

Additional Outputs:

```text
mapping_log.csv
mapping_exceptions.csv
```

---

# Error Handling

Examples:

```text
Unmapped account detected

Duplicate mapping detected

Invalid FS category

Balance mismatch after mapping
```

System must stop processing until resolved.

---

# Success Criteria

Milestone 3 is complete when:

✓ Trial Balance is fully mapped

✓ All accounts assigned to FS categories

✓ No unmapped accounts remain

✓ Mapping audit trail generated

✓ Reclassifications supported

✓ Balance integrity preserved

✓ Output ready for statement generation

---

# Deliverables (Private Repo)

```text
src/
└── mapping/
    ├── mapper.py
    ├── validator.py
    ├── taxonomy.py
    ├── reclass.py
    └── audit_log.py
```

Output:

```text
mapped_tb.csv
```

This becomes the direct input into Milestone 4 – Financial Statement Generator.
