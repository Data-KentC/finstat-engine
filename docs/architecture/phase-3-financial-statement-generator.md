# Phase 3 – Financial Statement Generator

## Objective
Transform the mapped Trial Balance into a complete set of financial statements.

Inputs:
Mapped Trial Balance

Outputs:
1. Statement of Financial Position
2. Statement of Profit or Loss
3. Statement of Changes in Equity
4. Cash Flow Statement (future phase)
5. Financial Statement Working Papers

The Financial Statement Generator must be:

- Deterministic
- Reproducible
- Auditable
- SFRS(I) compliant

No AI is required.

---

# Why This Matters

Most accounting systems stop here:

Trial Balance
↓
Excel

Human prepares financial statements manually.

This project eliminates that manual step.

The Financial Statement Generator becomes the first layer that produces auditor-ready outputs automatically.

---

# Inputs

Phase 2 Output

mapped_trial_balance.csv

Example:

| Account Code | Account Name | Balance | FS Category |
|-------------|--------------|---------|-------------|
| 1000 | Cash | 100000 | Cash and Cash Equivalents |
| 1100 | AR | 50000 | Trade Receivables |
| 2000 | AP | -30000 | Trade Payables |
| 3000 | Revenue | -500000 | Revenue |

---

# Processing Flow

Mapped TB
↓
Aggregate Categories
↓
Calculate Financial Statement Totals
↓
Generate Statement Layouts
↓
Export Outputs

---

# Statement of Financial Position

Categories are aggregated.

Example:

Cash and Cash Equivalents

100000

Trade Receivables

50000

Inventory

25000

Total Current Assets

175000

Property Plant Equipment

300000

Total Assets

475000

---

# Liabilities

Trade Payables

30000

Accruals

20000

Borrowings

100000

Total Liabilities

150000

---

# Equity

Share Capital

100000

Retained Earnings

225000

Total Equity

325000

---

# Validation Rule

Assets must equal:

Liabilities + Equity

If not:

Generation fails.

Exception report generated.

No financial statements produced.

---

# Statement of Profit or Loss

Revenue

500000

Less:

Cost of Sales

(250000)

Gross Profit

250000

Less:

Operating Expenses

(100000)

Profit Before Tax

150000

Less:

Income Tax

(25000)

Profit After Tax

125000

---

# Validation Rule

Net Profit must reconcile to:

Movement in Retained Earnings

If mismatch exists:

Exception report generated.

---

# Statement of Changes in Equity

Opening Equity

Add:

Profit After Tax

Less:

Dividends

Equals:

Closing Equity

---

# Working Paper Generation

Every figure must have traceability.

Example:

Revenue
500000

Source:

Account 3000
Account 3010
Account 3020

Working paper generated automatically.

---

# Supporting Schedules

The generator creates:

revenue_schedule.csv

expense_schedule.csv

asset_schedule.csv

liability_schedule.csv

equity_schedule.csv

These become audit support files.

---

# Output Structure

outputs/

financial_statements/

    balance_sheet.xlsx

    income_statement.xlsx

    equity_statement.xlsx

working_papers/

    revenue_schedule.xlsx

    expense_schedule.xlsx

    asset_schedule.xlsx

    liability_schedule.xlsx

audit/

    reconciliation_report.xlsx

---

# Reconciliation Engine

Before finalisation:

System performs:

1. TB agrees to mapped TB
2. Assets = Liabilities + Equity
3. P&L agrees to Equity Movement
4. No unmapped accounts exist
5. No duplicate mappings exist

Only then:

Financial statements released.

---

# Exception Handling

Examples:

Unmapped account

Duplicate account

Balance sheet out of balance

Negative asset category

Missing retained earnings

All exceptions written to:

exceptions_report.csv

---

# Auditability

Every generated figure stores:

Source account

Account balance

Timestamp

Generator version

Example:

Cash and Cash Equivalents

100000

Generated From:

1000 Cash

1010 DBS Current Account

1020 UOB Current Account

Generator Version:

v1.0.0

Timestamp:

2026-06-17 14:35:22

---

# Future Enhancements

Version 1

Basic financial statements

Version 2

Comparative year support

Version 3

Multi-entity consolidation

Version 4

Foreign currency translation

Version 5

Automated cash flow generation

Version 6

Automated notes generation

Version 7

XBRL generation

Version 8

Continuous accounting support

---

# Success Criteria

The Financial Statement Generator is complete when:

✓ Balance Sheet generated

✓ Income Statement generated

✓ Equity Statement generated

✓ Working papers generated

✓ Reconciliation checks completed

✓ Audit trail created

✓ Outputs exported automatically

At completion of Phase 3 the system can produce a complete first draft financial statement package from a mapped Trial Balance with zero manual spreadsheet work.
