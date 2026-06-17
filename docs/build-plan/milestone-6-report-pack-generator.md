# Milestone 6 – Financial Statements Report Pack Generator

## Objective

Build a report generation engine that transforms validated financial statements into a professional, audit-ready financial statements package.

At the end of this milestone, the system no longer produces raw accounting outputs.

It produces a deliverable that can be:

* Reviewed by management
* Submitted to auditors
* Used for annual reporting
* Used as the foundation for ACRA filing preparation

This milestone converts accounting data into a presentation layer.

---

# Why This Matters

Current workflow:

```text
Trial Balance
     ↓
Excel Workpapers
     ↓
Financial Statements
     ↓
Manual Formatting
     ↓
Partner Review
     ↓
Final Report
```

Version 1 FSOS:

```text
Trial Balance
     ↓
FSOS
     ↓
Financial Statements Pack
```

The goal is to eliminate repetitive formatting work.

---

# Inputs

From Milestone 5:

```text
balance_sheet.xlsx

income_statement.xlsx

financial_summary.xlsx

validation_report.xlsx

audit_log.csv
```

---

# Report Pack Structure

Version 1 generates:

```text
Financial Statements Pack

1. Cover Page

2. Statement of Financial Position

3. Statement of Profit or Loss

4. Supporting Schedules

5. Validation Summary

6. Audit Exceptions

7. Preparation Metadata
```

---

# Section 1 – Cover Page

Automatically generate:

```text
Entity Name

Reporting Period

Preparation Date

Prepared By

Version Number
```

Example:

```text
ABC Pte Ltd

Financial Statements

For the Year Ended
31 December 2025

Prepared by FSOS

Version 1.0
```

---

# Section 2 – Statement of Financial Position

Display:

```text
Assets

Liabilities

Equity
```

Professional formatting.

Consistent layout.

Automatically generated totals.

---

# Section 3 – Statement of Profit or Loss

Display:

```text
Revenue

Cost of Sales

Gross Profit

Operating Expenses

Profit Before Tax

Income Tax

Profit After Tax
```

---

# Section 4 – Supporting Schedules

Version 1 schedules:

### Cash

```text
Account
Balance
```

---

### Trade Receivables

```text
Account
Balance
```

---

### Trade Payables

```text
Account
Balance
```

---

### Fixed Assets

```text
Account
Balance
```

---

# Section 5 – Validation Summary

Display all audit checks.

Example:

| Validation                  | Result  |
| --------------------------- | ------- |
| Balance Sheet Balances      | PASS    |
| Income Statement Reconciles | PASS    |
| Mapping Complete            | PASS    |
| Variance Review             | WARNING |

---

# Section 6 – Audit Exceptions

Display all warnings and exceptions.

Example:

```text
Inventory balance increased 40%

Revenue increased 85%

Negative prepayment balance detected
```

Purpose:

Provide reviewer focus areas.

---

# Section 7 – Preparation Metadata

Store:

```text
Run ID

Statement Version

Generation Date

Source File

Validation Status
```

Example:

```json
{
  "run_id": "FS-2026-001",
  "version": "1.0",
  "status": "PASS"
}
```

---

# Formatting Standards

Version 1 principles:

```text
Clean

Professional

Auditor-Friendly

Consistent
```

No manual formatting required.

---

# Report Templates

Version 1:

Single standard template.

Future versions:

```text
SME Template

Group Reporting Template

Audit Template

Management Reporting Template
```

---

# Output Formats

Version 1:

```text
Excel (.xlsx)

PDF
```

---

# Generated Outputs

```text
financial_statements_pack.xlsx

financial_statements_pack.pdf
```

---

# Generation Workflow

```text
Validated Statements
         ↓

Report Builder
         ↓

Formatting Engine
         ↓

Schedules
         ↓

Validation Summary
         ↓

PDF / Excel Pack
```

---

# Quality Control Checks

Before release:

Verify:

```text
All statements included

Page count generated

No missing schedules

Validation status available

No critical audit exceptions
```

---

# Version Control

Every report receives:

```text
report_id

version

generated_date
```

Example:

```text
FSPACK-2026-001

Version 1.0
```

---

# Future Expansion

Version 2:

```text
Notes to Financial Statements

Comparative Year Columns

Lead Schedules

Working Papers

Disclosure Automation
```

Version 3:

```text
Full IFRS Financial Statements

Full Singapore SME Financial Statements

XBRL-ready Outputs
```

---

# Success Criteria

Milestone 6 is complete when:

✓ Financial Statements generated automatically

✓ Supporting schedules generated

✓ Validation summary included

✓ Audit exceptions included

✓ PDF export available

✓ Excel export available

✓ No manual formatting required

✓ Professional report pack produced

---

# Deliverables (Private Repo)

```text
src/
└── reports/
    ├── report_builder.py
    ├── formatter.py
    ├── schedules.py
    ├── pdf_exporter.py
    └── metadata.py
```

Outputs:

```text
financial_statements_pack.xlsx

financial_statements_pack.pdf
```

---

# Strategic Importance

Milestone 1–5 prove:

```text
We can ingest, map, generate and validate financial statements.
```

Milestone 6 proves:

```text
We can produce a deliverable that humans can actually use.
```

This is the first milestone where a business owner, finance manager, auditor, or accounting firm can receive a finished package instead of a collection of accounting outputs.

At the completion of Milestone 6, the platform has effectively automated the majority of the traditional financial statement preparation workflow.
