# Phase 5 – Audit Evidence Pack Generator

## Objective

Automatically generate an auditor-ready support package directly from:

- Trial Balance
- General Ledger
- Mapping Engine
- Financial Statements
- Notes to Financial Statements

The output should significantly reduce manual Prepared By Client (PBC) work.

---

# Why This Matters

Preparing financial statements is only half the work.

Most audit effort comes from:

- collecting evidence
- preparing schedules
- reconciliations
- supporting balances
- answering audit requests

This phase converts the platform from:

Financial Reporting Engine

to

Audit Preparation Engine.

---

# Inputs

Phase 1
Trial Balance

Phase 2
Mapping Engine

Phase 3
Financial Statements

Phase 4
Notes Generator
General Ledger Export
Subledger Reports

Optional:
Bank Statements
Fixed Asset Registers
Tax Computations

---

# High Level Flow

Trial Balance
↓
Financial Statements
↓
Notes
↓
Audit Support Engine
↓
Evidence Pack
↓
Auditor Review

---

# Core Principle

Every disclosed figure must have evidence.

No figure should exist without support.

Example:

Revenue
500,000
↓
Revenue Schedule
↓
GL Transactions
↓
Source Documents

---

# Evidence Hierarchy

Level 1
Financial Statements
↓
Level 2
Notes
↓
Level 3
Lead Schedules
↓
Level 4
Supporting Schedules
↓
Level 5
Source Transactions

---

# Lead Schedule Generator

Automatically create:

Lead Schedule – Cash

Lead Schedule – Trade Receivables

Lead Schedule – Inventory

Lead Schedule – PPE

Lead Schedule – Payables

Lead Schedule – Revenue

Lead Schedule – Tax

Lead Schedule – Equity

---

# Example

Lead Schedule – Trade Receivables

Opening Balance
40,000

Movement
10,000

Closing Balance
50,000

Cross-reference:

Note 6
Balance Sheet
Trade Receivables

---

# Supporting Schedule Generator

Generate detailed support.

Example:

Trade Receivables

Customer A
20,000

Customer B
15,000

Customer C
15,000

Total
50,000

Automatically reconciles.

---

# Reconciliation Engine

Every schedule must reconcile.

Example:

AR Schedule
50,000
=
Balance Sheet
50,000

If mismatch:
Exception raised.

---

# Audit Tickmark Engine

Every figure receives:

Reference ID

Example:

AR-001

Cash-001

REV-001

PPE-001

TAX-001

Auditors can trace balances instantly.

---

# Cross Reference System

Example:

Balance Sheet

Trade Receivables
50,000
↓
Note 6
50,000
↓
Lead Schedule AR-001
50,000
↓
Customer Listing
50,000

Everything links together.

---

# Working Paper Generator

Create standard audit working papers.

Outputs:

working_papers/

    WP-AR.xlsx

    WP-Cash.xlsx

    WP-Revenue.xlsx

    WP-Tax.xlsx

    WP-PPE.xlsx

---

# Analytical Review Engine

Automatically generate:

Current Year

vs

Prior Year

analysis

Example:

Revenue
2025: 500,000
2024: 420,000

Variance: +19.0%

Comment:
Increase primarily driven by customer growth.

Version 1:
Template comments

Version 2:
AI-generated comments

---

# Bank Reconciliation Module

Input:

Bank Statement

Cash Ledger

Output:

Outstanding Deposits

Outstanding Payments

Reconciling Items

Bank Reconciliation Report

---

# Accounts Receivable Module

Generate:

Customer Listing

AR Aging

Collection Analysis

Large Balance Report

Concentration Analysis

---

# Accounts Payable Module

Generate:

Vendor Listing

AP Aging

Large Supplier Analysis

Unusual Transactions Report

---

# Revenue Module

Generate:

Revenue by Customer

Revenue by Month

Revenue by Product

Top 10 Customers

Revenue Trend Analysis

---

# Fixed Asset Module

Generate:

Opening Cost

Additions

Disposals

Depreciation

Closing Cost

Net Book Value

Automatically reconciled.

---

# Tax Module

Generate:

Tax Computation

Deferred Tax Rollforward

Effective Tax Rate Reconciliation

Tax Provision Schedule

---

# Exception Engine

Automatically identify:

Negative balances

Unusual movements

Missing mappings

Unreconciled schedules

Balance mismatches

Potential audit risks

---

# Risk Dashboard

Create:

Low Risk

Medium Risk

High Risk

classification

Example:

Cash
Low Risk

Receivables
Medium Risk

Revenue
High Risk

---

# Audit Request Tracker

Future enhancement.

Auditor Request
↓
System searches evidence repository
↓
Returns supporting schedules automatically

---

# Evidence Repository

Folder Structure

audit_pack/

    lead_schedules/

    support_schedules/

    reconciliations/

    analytics/

    exceptions/

---

# Audit Index

Automatically generated.

Example:

Reference

Description

AR-001
Trade Receivables Lead Schedule

AR-002
Customer Listing

AR-003
AR Aging

Cash-001
Bank Reconciliation

PPE-001
Fixed Asset Rollforward

---

# AI Layer (Future)

Version 1
No AI

Version 2
AI Review Assistant

Capabilities:
- identify unusual balances
- suggest audit risks
- draft explanations
- prepare PBC responses

AI never alters figures.

Only reviews.

---

# Success Criteria

Phase 5 complete when:
✓ Lead schedules generated
✓ Support schedules generated
✓ Reconciliations generated
✓ Audit index generated
✓ Tickmark references generated
✓ Exception reports generated

✓ Audit pack exported

At completion of Phase 5 the system can generate a complete auditor-ready support package directly from accounting records.
