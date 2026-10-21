# Mini Remittance: Money Transfer Application Testing

[← Back to portfolio](../README.md)

**Type:** Practical manual QA assignment · **Date:** September 2026 · **Tester:** Nika Isaiashvili

I tested a local build of this application as a practical assignment. I did not develop it, and it is not a production system.

**Result:** 23 reported defects (13 Major, 10 Minor), 13 modules assessed, release recommendation: **not accepted**. All defects were open when reported; no fixes were tested in this assignment.

| Document | Content |
|---|---|
| [Defect report](defect-report.md) | All 23 defects with preconditions, steps to reproduce, expected and actual results, and severity |
| [Acceptance assessment](acceptance-assessment.md) | Status of each of the 13 modules and the release recommendation |

## Application and context

Mini Remittance is a web console for money transfer operators. An operator sends and receives transfers through Western Union and MoneyGram, runs an AML (anti-money laundering) check, views transfer history, and downloads a PDF for each transfer.

- **Environment:** local build, Google Chrome 153 (64-bit), Windows, 1920 × 1080
- **Test account:** Operator role
- **Test date:** 23 September 2026
- **Requirements:** no full written specification was provided. Expected results were based on rules shown in the application (for example, the calculator label *Fee (1.5%, minimum 2.00)*) and on common rules for money transfer systems.

## Scope and approach

- **Approach:** manual exploratory and negative testing, with functional checks of the main transfer flows.
- **Techniques:** invalid and boundary inputs (very large amounts, very long names, digits and symbols in name fields, non-Latin characters), consistency checks between screens (calculator vs. confirmation, confirmation vs. notification), and repeated actions (double-clicking **Confirm and send**).
- **Workflows covered:**
  - Login with the operator account
  - Send Money through Western Union, from the form to confirmation
  - Send and Receive Money through MoneyGram (blocked: both open the Western Union window)
  - Sender and receiver form validation
  - Fee and total calculation in USD, EUR, and GEL
  - Destination countries and the AML check step
  - Transfer History, filters, and Clear Data
  - PDF receipts for completed transfers

## Significant defects

The "Possible impact" column is my own analysis, not a tested outcome.

| # | Defect | Severity | Possible impact |
|---|---|---|---|
| [15](defect-report.md#bug-15) | Double-clicking **Confirm and send** creates two Send requests | Major | The same payment can be sent twice by accident. |
| [9](defect-report.md#bug-9) | For an amount of 1, the confirmation step charges a fee of 0.02 USD/EUR or 0.01 GEL instead of the 2.00 minimum. For USD/EUR, the calculator shows the expected fee. | Major | The customer is charged a different fee from the one shown, and the stated minimum fee is not applied. |
| [16](defect-report.md#bug-16) | An excessively large amount is accepted, displayed in scientific notation (such as `7e+85`), and the transfer is completed | Major | There is no upper limit on the transfer amount. |
| [10](defect-report.md#bug-10) | The notification shows a different transfer number from the confirmation screen | Major | The app tells the operator that the receiver needs this number to collect the money, so a wrong number could block the payout. |
| [2](defect-report.md#bug-2) | Choosing MoneyGram opens the Western Union window | Major | The MoneyGram flow cannot be used or tested. |
| [8](defect-report.md#bug-8) | The Document Number field accepts any value | Major | The sender's identity document is not validated. |
| [22](defect-report.md#bug-22) | **Continue to AML check** does not respond when Somalia is the destination | Major | Transfers to this destination could not be completed in testing. |

<a id="findings-by-type"></a>
### Defects by type

All 23 items were logged as defects and are open. Because there was no full specification, they are not all equally certain. The groups below show which defects were observed directly and which **need requirement clarification** before development can treat them as defects:

| Type | Defects | Notes |
|---|---|---|
| Observed directly: functional and UI | #1, #2, #3, #9, #10, #11, #12, #14, #15, #22 | Wrong or broken behavior observed directly, for example the fee rule shown in the app not being applied at confirmation. |
| Observed directly: missing input validation | #4, #5, #6, #8, #16 | The invalid input was accepted. The exact rules (formats, length limits, maximum amount) still need to be confirmed. |
| Observed directly: destructive action | #21 | Clear Data deletes all history immediately. |
| Needs requirement clarification: missing features | #17, #18, #19, #20 | Logged as Major defects. Balance, balance check, card management, and Settings were expected but not available. The expected scope should be confirmed against the requirements. |
| Needs requirement clarification: business rule | #13 | The rule that a receiver must be registered is assumed from how money transfer systems usually work. |
| Observed directly: receipt and navigation | #7, #23 | Missing fields in the receipt, and no way back from the confirmation step. |

## Results

- **23 reported defects:** 13 Major, 10 Minor, all open.
- **13 modules:** 3 Pass, 7 Fail, 2 Pass with notes, 1 Not confirmed (Data Persistence).
- **Note on the source:** the original acceptance sheet marks "Receive & Verify Receiver" as Pass, while Bug #2 reports that MoneyGram's Receive option opens the Western Union window. The original document does not explain this, so both are shown as recorded.

See the [module status table](acceptance-assessment.md#module-status) for each module's result and defects.

## Release recommendation

**Not accepted: not ready for release.** Several Major defects affect the correctness and safety of money transfers: fees, amount limits, duplicate transfers, transfer numbers, and receiver and document validation. Recommended next steps: fix and retest the Major defects first, then the Minor defects, then confirm the Data Persistence module and the remaining corridors and currencies. See the [full recommendation](acceptance-assessment.md#overall-recommendation).

## Evidence

- [Defect report](defect-report.md): all 23 defects in full
- [Acceptance assessment](acceptance-assessment.md): module status and recommendation
- Screenshots were attached to the original PDF report. They are not published here because they need a privacy review first.

---

[← Back to portfolio](../README.md)
