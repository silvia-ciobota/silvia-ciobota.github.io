# Excel cash reconciliation analysis

A portfolio demonstration comparing fictional internal cash records with a fictional external statement for October 2026. The workbook covers three synthetic CAD accounts.

[Download the Excel workbook](Silvia_Ciobota_Reconciliation_Analysis.xlsx?raw=1)

## Business question

Do the internal and external cash records agree, which differences require investigation, and what evidence is needed before review can be completed?

## Method

- Preserve the original source fields in separate Ledger and Statement tabs.
- Validate required fields, numeric amounts, currency and original record ID uniqueness. A blank amount is invalid; a numeric zero is valid.
- Build a comparison key from account, currency and transaction reference, with normalised spaces and letter case.
- Count source records to identify duplicates before comparing amounts.
- Compare period cash and posting dates using an inclusive CAD 0.01 amount tolerance.
- Classify exceptions and assign an owner and required action. Record review stage, evidence and reviewer decision separately.

The workbook uses native Excel formulas, including COUNTIFS, SUMIFS, IF, VLOOKUP, TRIM and UPPER. No macros, SQL or live data connections are required.

## Sample results

| Measure | Result |
| --- | ---: |
| Ledger source rows | 82 |
| Statement source rows | 80 |
| Comparison keys assessed | 83 |
| Matched keys | 72 |
| Exception keys and open reviews | 11 |
| Ledger closing cash | CAD 101,855.00 |
| Statement closing cash | CAD 112,045.00 |
| Ledger less statement | CAD -10,190.00 |
| Gross absolute differences | CAD 15,880.00 |
| Unexplained bridge residual | CAD 0.00 |

Both sources use an illustrative opening cash assumption of CAD 100,000.00. Closing cash adds October postings to that assumption; these are not independently verified external balances.

The match rate is 86.7 percent. Exceptions were deliberately introduced for demonstration, so this is not an operating benchmark. Counts refer to comparison keys, not individual source rows or necessarily distinct root causes. Gross absolute differences sum review-row variances; they are not a measure of confirmed financial loss.

## Cases to inspect

| Review ID | Observation | Required investigation |
| --- | --- | --- |
| R0073 | Ledger fee -125; statement fee -150. | Obtain support for the CAD 25 difference. |
| R0076 | Two ledger debits of 1,250; one statement debit. | Establish whether the duplicate occurred in the extract or the actual posting. |
| R0078 | Ledger debit on October 30; corresponding statement record on November 2. | Obtain posting evidence and review the month-end treatment. |
| R0081 and R0082 | Ledger-only +200 and -200 in different accounts. | Investigate both; an overall zero does not establish that either account is correct. |
| R0080-L and R0080 | A ledger reference is missing; a similar statement item exists. | Retain separate exceptions until source evidence establishes identity. |

For R0078, the later source date is in Statement!D82. Reconciliation!K82 is blank because it displays an in-period statement date only. The all-dates statement count is one, while the October count is zero.

## Review the workbook

1. Start on Overview to see the period, controls, summary and cash difference bridge.
2. On Reconciliation, filter Status to exclude Matched and Outside period.
3. Trace each comparison key to the original source record IDs.
4. Use columns N, O and P for the review stage, evidence reference and reviewer decision.

A stage of Closed alone does not complete review. Evidence and an Approved reviewer decision are also required for the outcome Documented. All 11 exception reviews are open in the delivered example. A zero bridge residual explains the cash difference; it does not resolve the exceptions or book corrections.

## Scope

This is a fixed demonstration, with no automatic import or comparison-key rebuild. New source rows or edited keys require a controlled refresh. It covers cash transactions in one currency and does not establish holdings, valuation, settlement or overall trade completeness. No real client information, employer records or employer procedures are included.

[Companion investment operations workflow guide](../investment-operations-workflow/)

