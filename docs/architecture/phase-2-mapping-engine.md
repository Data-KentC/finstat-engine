# Phase 2 – Mapping Engine

## Objective

Convert raw Trial Balance accounts into Financial Statement line items.

This is the core accounting layer of Finstat Engine.

The Mapping Engine transforms:

Raw Trial Balance
↓
Standardised Financial Statement Categories
↓
Balance Sheet
Income Statement
Cash Flow Statement (future)

The engine must be deterministic.

No AI is used.

Every account must map to a defined financial statement category.

---

## Why This Matters

Every company uses different account names.

Examples:

Company A
- Cash at Bank
- DBS Current Account
- UOB Operating Account

Company B
- Cash
- OCBC Main Account

Although names differ,
all represent:

Cash and Cash Equivalents

The Mapping Engine standardises these differences.

---

## Inputs

Phase 1 Output:

trial_balance_standardised.csv

Example:

| Account Code | Account Name | Balance |
|--------------|-------------|---------|
| 1000 | Cash at Bank | 100000 |
| 2000 | Trade Payables | -50000 |
| 3000 | Revenue | -300000 |

---

## Mapping Library

The engine reads:

mapping_library.csv

Example:

| Account Code | FS Category |
|-------------|------------|
| 1000 | Cash and Cash Equivalents |
| 1100 | Trade Receivables |
| 1200 | Inventory |
| 2000 | Trade Payables |
| 3000 | Revenue |
| 4000 | Cost of Sales |

---

## Processing Logic

For each account:

1. Read Account Code
2. Search Mapping Library
3. Find matching FS Category
4. Assign category
5. Output mapped record

Pseudo-code:

FOR each TB account

    FIND mapping

    IF mapping exists

        assign category

    ELSE

        flag exception

END

---

## Exception Handling

Unmapped accounts are never ignored.

Example:

| Account Code | Account Name |
|-------------|--------------|
| 9999 | New Account |

Output:

unmapped_accounts.csv

The user must review and assign a category.

This prevents silent classification errors.

---

## Outputs

mapped_trial_balance.csv

Example:

| Account Code | Account Name | Balance | FS Category |
|-------------|--------------|---------|------------|
| 1000 | Cash at Bank | 100000 | Cash and Cash Equivalents |
| 2000 | Trade Payables | -50000 | Trade Payables |
| 3000 | Revenue | -300000 | Revenue |

---

## Audit Trail

Every mapping decision is logged.

Example:

mapping_log.csv

| Timestamp | Account | Category |
|------------|---------|-----------|
| 2026-06-17 | 1000 | Cash and Cash Equivalents |

This creates a full audit trail.

---

## Future Enhancements

Version 1:
- Exact account code matching

Version 2:
- Exact account name matching

Version 3:
- Rule-based matching

Version 4:
- AI-assisted mapping suggestions

Version 5:
- Self-learning mapping memory

---

## Success Criteria

The Mapping Engine is complete when:

✓ Trial Balance imports successfully

✓ Mapping Library loads successfully

✓ Accounts map automatically

✓ Unmapped accounts identified

✓ Audit log generated

✓ Output file created

Once complete, the system can classify financial data automatically.

This becomes the foundation for Balance Sheet and Income Statement generation.
