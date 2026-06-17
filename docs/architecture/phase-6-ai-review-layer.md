# Phase 6 – AI Review Layer

## Objective

Create an AI-powered review engine that examines:

- Trial Balance
- Financial Statements
- Notes to Financial Statements
- Audit Evidence Pack

and produces:

- Review comments
- Risk flags
- Disclosure observations
- Analytical review commentary
- Auditor response drafts

The AI never changes accounting records.

The AI never posts journals.

The AI never overrides calculations.

The AI only reviews.

---

# Philosophy

AI should behave like:

Senior Accountant
↓
Financial Controller
↓
Audit Manager
↓
CFO Reviewer

Not like:
Bookkeeper

Not like:
ERP system

Not like:
General Ledger

All accounting calculations remain deterministic.

---

# Inputs

Phase 1
Trial Balance

Phase 2
Mapping Library

Phase 3
Financial Statements

Phase 4
Notes

Phase 5
Audit Evidence Pack

---

# High Level Flow

Financial Statements
↓
Notes
↓
Audit Pack
↓
AI Review Engine
↓
Review Report

---

# AI Review Categories

1. Financial Review

2. Disclosure Review

3. Audit Risk Review

4. Analytical Review

5. Consistency Review

6. Management Commentary

---

# Financial Review

Objective:
Identify unusual balances.

Example:

Revenue increased 150%
while
Trade Receivables increased 5%

Flag generated:
Revenue growth may not be supported by corresponding receivable movement.

Review recommended.

---

# Analytical Review

Perform ratio analysis.

Examples:

Gross Margin

Current Ratio

Quick Ratio

Debt to Equity

Inventory Turnover

Receivable Days

Payable Days

Return on Equity

Return on Assets

---

# Example Output

Gross Margin

2025: 45%

2024: 31%

Observation:

Significant increase in gross margin.

Recommend review of cost classification.

---

# Trend Analysis

Review:

Current Year

vs

Previous Year

vs

3-Year Trend

Examples:

Revenue

Expense Categories

Payroll

Marketing

Rent

Professional Fees

---

# Variance Analysis

Automatically identify:

Large movements

Unexpected balances

Material changes

Threshold examples:

>20%
or
>$50,000

---

# Consistency Review

Example:

Financial Statements:

Revenue
500,000

Revenue Note:
480,000

Flag:
Inconsistency detected.

Review required.

---

# Disclosure Review

Review notes against disclosure checklist.

Example:
PPE balance exists.
No PPE note found.

Flag:
Potential missing disclosure.

---

# Accounting Policy Review

Example:

Lease liability detected.

No lease accounting policy found.

Flag generated.

---

# Related Party Review

Example:

Director Loan Account exists.

No related party note detected.

Flag generated.

---

# Tax Review

Example:
Profit Before Tax 200,000
Tax Expense 0
Effective Tax Rate 0%

Flag:
Tax expense appears unusually low.

Review required.

---

# Going Concern Review

Example:

Current Liabilities 250,000
Current Assets 100,000
Current Ratio 0.40

Flag: Potential going concern consideration.

---

# Audit Risk Engine

Risk Categories:
Low
Medium
High
Critical

---

# Revenue Risk Examples

Revenue spike

Large manual journals

Year-end revenue concentration

Single customer dependency

---

# Cash Risk Examples

Negative cash

Frequent adjustments

Unreconciled bank balances

---

# Receivable Risk Examples

Large overdue balances

Customer concentration

Aging deterioration

---

# Fraud Indicators

Version 1

Simple rules

Examples:
Round-dollar journals
Weekend postings
Large manual entries
Unusual account combinations

---

# Future Version

Benford's Law

Duplicate payments

Anomaly detection

Machine learning scoring

---

# Management Commentary Generator

Input:
Financial Statements

Output:
Draft management discussion.

Example:
Revenue increased by 19% compared to the prior year, primarily driven by expansion of the customer base and improved sales performance.

Generated automatically.

---

# CFO Summary Generator

Produce:
1-page executive summary.

Example:
Revenue ↑ 19%

Gross Margin ↑ 8%

Cash ↓ 12%

Receivables ↑ 25%

Key Risks

- Receivable collection
- Revenue concentration

---

# Auditor Response Generator

Example:

Auditor Query:

Explain increase in marketing expenses.

Draft Response:

Marketing expenditure increased due to additional customer acquisition initiatives launched during FY2025.

Human reviews before sending.

---

# AI Review Report

Outputs

review/

    ai_review_report.docx

    risk_dashboard.xlsx

    variance_report.xlsx

    disclosure_review.xlsx

---

# Confidence Scoring

Every AI comment includes:

Confidence

Example:

Observation

Revenue concentration risk identified.

Confidence

92%

---

# Human Approval Principle

AI can:

Recommend

Review

Summarize

Explain

AI cannot:

Approve

Sign

File

Override

Post

Delete

---

# Model Strategy

Version 1

Cloud LLM

OpenAI

Claude

Gemini

via API

Version 2

Bring-your-own-model

Version 3

Multi-model review

Example:

GPT

+

Claude

+

Deterministic Rules

Consensus generated.

---

# Future Controller Copilot

Natural language interface.

Examples:

"Why did revenue increase?"

"Show me unusual balances."

"What changed from last year?"

"Which notes are incomplete?"

"Which balances are highest risk?"

---

# Future Auditor Copilot

Examples:

"Show support for Note 8."

"Provide AR aging."

"Explain tax movement."

"Show reconciliation."

---

# Success Criteria

Phase 6 complete when:
✓ Variance review generated
✓ Disclosure review generated
✓ Risk scoring generated
✓ Ratio analysis generated
✓ Management commentary generated
✓ CFO summary generated

✓ Review package exported

At completion of Phase 6 the platform functions as an AI-assisted Financial Controller reviewing the entire reporting package.
