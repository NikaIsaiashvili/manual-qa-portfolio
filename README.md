# Manual QA Portfolio: Nika Isaiashvili

Manual QA Engineer based in Tbilisi, Georgia. This repository shows my manual testing work: a defect report, a release acceptance assessment, and defect validation records.

All projects here are **practical QA assignments or independent practice**. They are not commercial projects, and I did not develop the applications I tested.

## Projects

| Project | What I did | Result |
|---|---|---|
| **[Mini Remittance: Money Transfer Application Testing](01-mini-remittance/README.md)**<br>Practical assignment · Sep 2026 | Exploratory and negative testing of a money transfer console; defect report and module-level acceptance assessment | 23 reported defects (13 Major, 10 Minor); release **not accepted** |
| **[Online Ordering Web Application: Defect Validation](02-online-ordering/README.md)**<br>Practical assignment · 2026 | Retested 10 resolved Jira issues in a new build and recommended an action for each | 3 fixes confirmed, 1 fix failed (reopen), 1 test blocked |
| **[API and SQL Practice](03-api-and-sql-practice/README.md)**<br>Planned | Plan for REST API and SQL exercises | No results yet |

## Best examples

- **Duplicate transfers.** Double-clicking **Confirm and send** created two Send requests for one transfer. ([Bug #15](01-mini-remittance/defect-report.md#bug-15))
- **Fee mismatch.** For an amount of 1 USD, the calculator showed the minimum fee of 2.00, but the confirmation step charged 0.02. ([Bug #9](01-mini-remittance/defect-report.md#bug-9))
- **Fix that did not work.** A defect resolved as Fixed was still reproducible in the new build, so I recommended reopening it. ([DV #2](02-online-ordering/defect-validation.md#dv-2))
- **Blocked test reported honestly.** A page needed for validation returned 404, so the result was recorded as BLOCKED instead of PASS or FAIL. ([DV #6](02-online-ordering/defect-validation.md#dv-6))

## How to read the results

| Term | Meaning in this portfolio |
|---|---|
| Reported defect | Logged by me during testing and still open. Not yet confirmed or fixed by a developer. |
| Needs requirement clarification | A reported defect whose expected behavior is based on an assumption, because no written requirement existed. |
| Confirmed fix | A resolved issue that I retested and that no longer occurs. |
| Failed fix | A resolved issue that I retested and that still occurs (recommended to reopen). |
| Blocked | A test that could not be run because of another problem. |

## Skills shown

- Exploratory, functional, and negative testing, including boundary and invalid inputs
- Bug reports with preconditions, steps, expected and actual results, and severity
- Module-level acceptance assessment and release recommendation
- Defect validation against Jira resolutions (Fixed, Won't Fix, Cannot Reproduce, Not a Bug)

**Tools used in these projects:** Jira, Google Chrome.
**Also practiced (no published work yet):** Postman, Swagger, SQL, Chrome DevTools, TestRail, Zephyr, Git/GitHub.

## Background

Before moving into QA, I worked as an Acquiring Specialist at Georgian Card (2023–2025). I installed, updated, and configured payment-terminal software and worked with internal teams and partners to resolve technical issues. I also have basic frontend knowledge (HTML, CSS, JavaScript, React).

## Contact

- LinkedIn: [linkedin.com/in/nikaisaiashvili](https://www.linkedin.com/in/nikaisaiashvili)
- GitHub: [github.com/NikaIsaiashvili](https://github.com/NikaIsaiashvili)
