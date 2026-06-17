# Phase 4 – Notes to Financial Statements Generator

## Objective
Automatically generate Notes to the Financial Statements (NFS) from:

- Trial Balance
- Mapping Library
- Financial Statement Outputs
- Supporting Schedules

The system should produce a complete first draft of financial statement disclosures compliant with:

- SFRS(I)
- Companies Act (Singapore)
- ACRA filing expectations
- Typical SME and Mid-Market audit requirements

This phase transforms the project from:

Financial Statement Generator

into

Financial Reporting Engine.

---

# Why This Matters
Most accounting software can generate:

- Balance Sheet
- Income Statement

Very few can generate:

- Notes to Financial Statements

Yet the notes typically represent:

70% to 90%

of the total annual report.

For auditors:

Notes are often more important than the primary statements.

---

# Inputs

Phase 3 Outputs

balance_sheet.xlsx

income_statement.xlsx

equity_statement.xlsx

working_papers/

mapped_trial_balance.csv

---

# High Level Flow

Trial Balance
↓
Mapping Engine
↓
Financial Statements
↓
Disclosure Engine
↓
Notes Generator
↓
Draft Financial Statements Package

---

# Notes Architecture

The notes engine contains:
1. Static Notes
2. Semi-Dynamic Notes
3. Dynamic Notes

---

# Static Notes

Rarely change.

Examples:
Nature of Business
Basis of Preparation
Functional Currency
Revenue Recognition Policy
Property Plant Equipment Policy
Inventory Policy
Taxation Policy
Financial Instruments Policy

---

# Storage Structure

templates/

accounting_policies/

    revenue.md

    inventory.md

    ppe.md

    taxation.md

    leases.md

These templates are maintained manually.

---

# Semi-Dynamic Notes

Text remains fixed.

Values change automatically.

Example:

Share Capital

Issued and fully paid:

2025: SGD 100,000

2024: SGD 100,000

Only numbers change.

---

# Dynamic Notes

Generated from schedules.

Examples:

Property Plant & Equipment

Trade Receivables

Trade Payables

Revenue

Tax Expense

Cash & Bank

---

# Example

Property Plant & Equipment

Opening Balance

100,000

Additions

25,000

Disposals

(5,000)

Closing Balance

120,000

Generated automatically.

---

# Disclosure Engine

The disclosure engine maps:

Financial Statement Line Item

↓

Required Note

Example:

Cash and Cash Equivalents

↓

Note 5

Trade Receivables

↓

Note 6

Revenue

↓

Note 12

Property Plant Equipment

↓

Note 8

---

# Disclosure Mapping Table

Stored in:

config/disclosure_mapping.csv

Example:

| FS Line Item | Note Number |
|-------------|-------------|
| Cash and Cash Equivalents | 5 |
| Trade Receivables | 6 |
| Inventory | 7 |
| PPE | 8 |
| Revenue | 12 |

---

# Supporting Schedules

The engine automatically creates:

cash_schedule.xlsx

receivable_schedule.xlsx

payable_schedule.xlsx

revenue_schedule.xlsx

ppe_schedule.xlsx

tax_schedule.xlsx

equity_schedule.xlsx

These schedules become note sources.

---

# Note Numbering Engine

Automatically assigns:

Note 1
Corporate Information

Note 2
Basis of Preparation

Note 3
Significant Accounting Policies

Note 4
Critical Estimates

Note 5
Cash and Cash Equivalents

Note 6
Trade Receivables

...

No manual renumbering required.

---

# Comparative Year Support

Version 1:

Current Year Only

Version 2:

Current Year
Previous Year

Example:

2025
2024

Revenue

500,000

450,000

---

# Cross Reference Engine

Automatically links:

Financial Statements

to

Notes

Example:

Revenue
500,000

See Note 12

Property Plant Equipment
120,000

See Note 8

---

# Validation Rules

Every note must reconcile.

Example:

Trade Receivables Note

50,000

must equal

Balance Sheet

50,000

If mismatch:

Generation stops.

Exception created.

---

# Required Reconciliations

Cash Note

=
Balance Sheet Cash

PPE Note

=
Balance Sheet PPE

Revenue Note

=
Income Statement Revenue

Tax Note

=
Income Statement Tax Expense

Equity Note

=
Statement of Changes in Equity

---

# Materiality Engine

Version 1:

Simple threshold.

Example:

Balance < 1,000

Do not disclose separately.

Aggregate into:

Other Assets

or

Other Liabilities

---

# Future Materiality Logic

Auditor-adjustable.

Example:

Materiality %

Materiality SGD

Performance Materiality

Clearly Trivial Threshold

---

# Draft Financial Statements Package

Outputs/

financial_report/

    Financial Statements.xlsx

    Notes.xlsx

    Disclosure Checklist.xlsx

---

# Disclosure Checklist

Generated automatically.

Example:

Cash Note

✓

Receivables Note

✓

Revenue Note

✓

PPE Note

✓

Tax Note

✓

Lease Note

Pending

This becomes an internal quality-control tool.

---

# Future AI Enhancement

Version 1

Rule Based

Version 2

AI Assisted

Example:

AI reviews notes for:

- inconsistencies
- missing disclosures
- unusual wording

AI does not create figures.

AI only reviews.

---

# Auditability

Every note stores:

Source Accounts

Source Schedule

Calculation Logic

Generator Version

Timestamp

Example:

Note 5
Cash and Cash Equivalents

Generated From:

1000 Cash

1010 DBS Current Account

1020 UOB Current Account

Version:

1.0.0

Generated:

2026-06-17

---

# Success Criteria

The Notes Generator is complete when:

✓ Accounting policies generated

✓ Disclosure schedules generated

✓ Note numbering generated

✓ Cross references generated

✓ Reconciliations completed

✓ Disclosure checklist generated

✓ Draft notes package exported

At completion of Phase 4 the system can produce a complete draft set of financial statements and notes with minimal manual intervention.
