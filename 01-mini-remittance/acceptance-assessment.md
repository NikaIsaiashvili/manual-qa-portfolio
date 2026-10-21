# Mini Remittance: Acceptance Assessment

[← Back to project overview](README.md)

This document records the acceptance status of each application module and the overall release recommendation. It is based on the defects in the [Defect Report](defect-report.md) and should be read together with it. The original was a PDF acceptance sheet; this Markdown version keeps the same content, with light editing for grammar and consistent names.

| Item | Value |
|---|---|
| Application under test | Mini Remittance, Money Transfer Console (local build) |
| Environment | Local environment, Google Chrome 153.0.8010.53 (64-bit), Windows, 1920 × 1080 |
| Test account | Operator role |
| Systems tested | Western Union, MoneyGram |
| Test type | Manual testing |
| Test date | 23 September 2026 |
| Prepared by | Nika Isaiashvili (practical QA assignment) |

## Module status

**Status legend**
- **Pass:** tested and behaves as expected.
- **Fail:** at least one open Major defect.
- **Pass with notes:** works, with open Minor defects only.
- **Not confirmed:** the defect report has no defects for the module, and its execution status still needs to be confirmed. No result is assumed.

| Module | Status | Defects | Notes |
|---|---|---|---|
| Authentication & Session | Pass with notes | [#1](defect-report.md#bug-1) | Login with the operator account works. Minor: a Georgian-alphabet username is accepted. Negative, session, and security cases are not covered by the defect report. |
| Send (Western Union) | **Fail** | [#10](defect-report.md#bug-10), [#13](defect-report.md#bug-13), [#15](defect-report.md#bug-15), [#23](defect-report.md#bug-23) | The send flow completes, but with open Major defects: a different transfer number in the notification, a transfer sent to an unregistered receiver, and duplicate transfers on double-click. No way back from the confirmation modal (Minor). |
| Send (MoneyGram) | **Fail** | [#2](defect-report.md#bug-2) | Send or Receive Money from MoneyGram opens the Western Union window, so the MoneyGram flow cannot be tested or accepted. |
| Sender / Receiver Form Validation & UI | **Fail** | [#3](defect-report.md#bug-3), [#4](defect-report.md#bug-4), [#5](defect-report.md#bug-5), [#6](defect-report.md#bug-6), [#8](defect-report.md#bug-8), [#16](defect-report.md#bug-16) | Document Number accepts any input, and Amount accepts very large values (both Major). Name and Surname accept digits and symbols and have no length limit; Phone accepts non-numeric characters; field hints are swapped (Minor). |
| Fee & Total Calculation | **Fail** | [#9](defect-report.md#bug-9) | The fee at confirmation differs from the calculator. For an amount of 1, the minimum fee of 2.00 is not applied (0.02 USD/EUR and 0.01 GEL charged instead). |
| Balance, Cards & Settings | **Fail** | [#17](defect-report.md#bug-17), [#18](defect-report.md#bug-18), [#19](defect-report.md#bug-19), [#20](defect-report.md#bug-20) | No user balance, no balance check before payment, no card management or top-up, and no Settings for the account. These features need requirement clarification (see the note below). |
| Transfers List & Filters | **Fail** | [#11](defect-report.md#bug-11), [#12](defect-report.md#bug-12), [#21](defect-report.md#bug-21) | Clear Data deletes all history without confirmation (Major). The date filter time cannot be changed, and the From/To calendars overlap (Minor). |
| Receipts / PDF Output | Pass with notes | [#7](defect-report.md#bug-7), [#14](defect-report.md#bug-14) | A PDF is generated for each transfer, but Phone and Document Number are missing, and Georgian characters appear as encoded symbols (both Minor). |
| Corridors & Currency Matrix | **Fail** | [#22](defect-report.md#bug-22) (also [#9](defect-report.md#bug-9)) | Continue to AML check does not respond when Somalia is the destination (Major). The fee inconsistency also appears across USD, EUR, and GEL (see #9). |
| AML Watchlist | Pass | None | Tested; behaves as expected. No defects. |
| Receive & Verify Receiver | Pass | None | Tested; behaves as expected. No defects. Note: MoneyGram Receive is affected by #2. |
| Transfer Status Lifecycle | Pass | None | Tested; behaves as expected. No defects. |
| Data Persistence | Not confirmed | None | No defects for this module, apart from Clear Data (#21), which is recorded under Transfers List & Filters. Execution status still needs to be confirmed. |

**Modules:** 13 in total: 3 Pass, 7 Fail, 2 Pass with notes, 1 Not confirmed.

## Defect summary

| Severity | Count | References |
|---|---|---|
| Major | 13 | #2, #8, #9, #10, #13, #15, #16, #17, #18, #19, #20, #21, #22 |
| Minor | 10 | #1, #3, #4, #5, #6, #7, #11, #12, #14, #23 |
| **Total** | **23** | All open at the time of assessment |

## Overall recommendation

**Not accepted: not ready for release.**

The defect report contains 23 open defects, 13 of them Major. Several affect the correctness and safety of money transfers:

- the minimum fee is not applied at confirmation ([#9](defect-report.md#bug-9));
- very large amounts are accepted ([#16](defect-report.md#bug-16));
- double-clicking **Confirm and send** creates duplicate transfers ([#15](defect-report.md#bug-15));
- the transfer number in the notification differs from the confirmed one ([#10](defect-report.md#bug-10));
- transfers are sent to an unregistered receiver ([#13](defect-report.md#bug-13));
- the Document Number is not validated ([#8](defect-report.md#bug-8));
- no balance exists or is checked before payment ([#17](defect-report.md#bug-17), [#18](defect-report.md#bug-18)).

MoneyGram cannot be accepted because its Send/Receive actions open the Western Union window ([#2](defect-report.md#bug-2)), and Clear Data removes all history without confirmation ([#21](defect-report.md#bug-21)).

> **Note added for this portfolio:** #13 and #17–#20 depend on requirements that were not documented, and need clarification before they are treated as confirmed defects. The recommendation stands without them: the directly observed Major defects (#2, #8, #9, #10, #15, #16, #21, #22) are enough to block release.

## Recommended next steps

1. Fix and retest all 13 Major defects, starting with #9, #15, #16, #10, #13, #8, and #2.
2. Fix the 10 Minor defects and verify them again.
3. Confirm the module marked "Not confirmed" (Data Persistence) and test the remaining corridors and currencies.
4. Issue an updated acceptance assessment after testing and retesting are complete.

---

[← Back to project overview](README.md) · [Defect report](defect-report.md)
