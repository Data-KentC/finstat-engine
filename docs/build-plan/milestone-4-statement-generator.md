# Milestone 4 – Financial Statement Generator

## Objective
Build a deterministic financial statement generation engine that converts the mapped Trial Balance into a complete set of financial statements.
This milestone represents the first major visible outcome of the system.

For the first time, the user can upload a Trial Balance and automatically generate:

```text
Statement of Financial Position
Statement of Profit or Loss
Trial Balance Summary
Supporting Schedules
```

without manually building Excel workpapers.

---

# Purpose

Current financial statement preparation typically involves:

```text
ERP Export
      ↓
Excel Cleanup
      ↓
Mapping
      ↓
Manual Financial Statements
      ↓
Review
```

The Financial Statement Generator eliminates the manual statement preparation stage.

---

# Inputs

From Milestone 3:

```text
mapped_tb.csv
```

Example:

| Account Code | FS Category               | Balance |
| ------------ | ------------------------- | ------- |
| 1000         | Cash and Cash Equivalents | 150000  |
| 1100         | Trade Receivables         | 90000   |
| 1200         | Inventories               | 70000   |

---

# Statement Outputs

Version 1 produces:

## Statement of Financial Position

### Assets

```text
Cash and Cash Equivalents
Trade Receivables
Other Receivables
Inventories
Prepayments
Property Plant and Equipment
Intangible Assets

Total Assets
```

### Liabilities

```text
Trade Payables
Accruals
Borrowings
Lease Liabilities

Total Liabilities
```

### Equity

```text
Share Capital
Retained Earnings
Current Year Profit

Total Equity
```

---

## Statement of Profit or Loss

```text
Revenue

Less:
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

# Processing Flow

```text
Mapped Trial Balance
         ↓
Aggregate Categories
         ↓
Build Balance Sheet
         ↓
Build Income Statement
         ↓
Calculate Totals
         ↓
Validate Balancing
         ↓
Generate Outputs
```

---

# Statement Construction Rules

## Rule 1 – Category Aggregation

Multiple accounts may roll into one FS line.

Example:

```text
1001 OCBC Current Account
1002 DBS Current Account
1003 UOB Current Account
```

becomes

```text
Cash and Cash Equivalents
```

---

## Rule 2 – Sign Normalization

The engine must consistently display:

```text
Assets = Positive

Liabilities = Positive

Equity = Positive

Expenses = Positive

Revenue = Positive
```

Internally, accounting signs may differ.

The engine standardizes presentation.

---

## Rule 3 – Current Year Earnings

Current year profit must automatically flow into:

```text
Profit After Tax
```

and subsequently reconcile with Equity.

---

# Balance Sheet Validation

The generator must verify:

```text
Assets
=
Liabilities + Equity
```

Example:

```text
Assets        5,000,000

Liabilities   2,000,000

Equity        3,000,000
```

Pass.

---

Failure Example:

```text
Assets        5,000,000

Liabilities   2,000,000

Equity        2,900,000
```

System stops.

Error:

```text
Balance Sheet Out of Balance
Difference: 100,000
```

---

# Income Statement Validation

Verify:

```text
Revenue
-
Expenses
=
Profit After Tax
```

Any mismatch triggers rejection.

---

# Output Formats

Version 1:

```text
Excel (.xlsx)
CSV
```

Future:

```text
PDF
Word
HTML
XBRL
```

---

# Generated Files

```text
balance_sheet.xlsx

income_statement.xlsx

financial_summary.xlsx
```

---

# Supporting Schedules

Version 1 includes:

### Cash Schedule

```text
Cash Accounts
Opening Balance
Closing Balance
```

---

### Trade Receivables Schedule

```text
Account
Balance
```

---

### Trade Payables Schedule

```text
Account
Balance
```

---

# Materiality Engine (Future)

Future releases may support:

```text
Automatic grouping

Immaterial line suppression

Disclosure thresholds
```

Not required for Version 1.

---

# Logging Requirements

Each statement generation run records:

```text
run_id
timestamp
client
period
statement_version
```

Example:

```json
{
  "run_id": "FS-2026-0001",
  "client": "ABC Pte Ltd",
  "period": "2025-12",
  "status": "PASS"
}
```

---

# Error Handling

Examples:

```text
Balance Sheet Out of Balance

Missing Revenue Account

Missing Equity Account

Invalid Mapping Category

Calculation Error
```

Generation must stop until resolved.

---

# Deliverables

Output Files:

```text
balance_sheet.xlsx

income_statement.xlsx

financial_summary.xlsx
```

---

# Success Criteria

Milestone 4 is complete when:

✓ Mapped Trial Balance is accepted

✓ Balance Sheet generated automatically

✓ Income Statement generated automatically

✓ Statement totals calculated correctly

✓ Balance Sheet balances

✓ Profit reconciles correctly

✓ Excel outputs generated

✓ No manual spreadsheet formulas required

---

# Deliverables (Private Repo)

```text
src/
└── statements/
    ├── balance_sheet.py
    ├── income_statement.py
    ├── aggregator.py
    ├── validator.py
    └── exporter.py
```

Outputs:

```text
balance_sheet.xlsx

income_statement.xlsx

financial_summary.xlsx
```

Milestone 4 transforms accounting data into financial statements.

Milestone 5 transforms those financial statements into an audit-ready reporting package.
