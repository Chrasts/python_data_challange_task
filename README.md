# Challenge Task – Monthly Price Output & Trading Optimization

## Overview
This repository contains two independent solutions based on the provided case study:

- Solution 1–2: Reconstruction of monthly OUTPUT table from historical share price data.
- Solution 3: Maximum wealth calculation using at most 3 trades under a simplified trading model.

The goal is reproducibility and clarity rather than production-grade generalization.

---

## Input Data

Expected Excel structure:

Sheet: HISTORICAL_SHARE_PRICE
- COMPANY
- CURRENCY
- SHARE_PRICE
- S_FROM

Sheet: CURRENT_SHARE_PRICE
- COMPANY
- CURRENCY
- SHARE_PRICE
- S_FROM

Default input file name used in scripts:
ChallengeTask_data.xlsx

---

## How to Run

Solution 1–2:
python "solution 1 and 2.py"

Output:
OUTPUT.xlsx

Solution 3:
python "solution 3.py"

Console output:
- Max wealth
- Max profit

---

## Solution Logic

### Solution 1–2 (Monthly OUTPUT Reconstruction)
For each month boundary:
- Take price at start of month T
- Take price at start of month T+1
- If price difference ≠ 0 → write record into OUTPUT

Records are generated only when a full month price change exists.

---

### Solution 3 (Trading Optimization)
Dynamic programming solution computing maximum achievable wealth using:
- Initial capital = 1
- Maximum = 3 trades (buy + sell pairs)
- Chronological trade ordering

Note: The implementation assumes standard time-ordered trading, not literal unrestricted time travel.

---

## Assumptions

- Input data are internally consistent.
- Price timestamps represent valid effective-from dates.
- Missing months imply no valid OUTPUT record.
- Dataset used here contains a single company and currency.

---

## Known Limitations / TODO

Deduplication:
Currently deduplicates by pairs of timestamp and company name only.

Multi-Entity Support:
Scripts are not fully generalized for multiple companies or currencies in one run.
For multi-currency datasets it should chose one and convert, or group by currencies and deduplicate by triple of timestap, company name and currency.



Input Configurability:
Input filename is currently hardcoded.

---

## Dependencies

Typical environment:
pandas
openpyxl

---

## Reproducibility

Run scripts in directory containing the input Excel file.
