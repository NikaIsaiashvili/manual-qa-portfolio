# Manual QA Portfolio: Nika Isaiashvili

Manual QA Engineer based in Tbilisi, Georgia. This repository shows my manual testing work: a defect report, a release acceptance assessment, and defect validation records.

All projects here are **practical QA assignments or independent practice**. They are not commercial projects, and I did not develop the applications I tested.

## Projects

| Project | What I did | Result |
|---|---|---|
| **[Mini Remittance: Money Transfer Application Testing](01-mini-remittance/README.md)**<br>Practical assignment · Sep 2026 | Exploratory and negative testing of a money transfer console; defect report and module-level acceptance assessment | 23 reported defects (13 Major, 10 Minor), 5 of them pending requirement clarification; release **not accepted** |
| **[Online Ordering Web Application: Defect Validation](02-online-ordering/README.md)**<br>Practical assignment · 2026 | Retested 10 resolved Jira issues in a new build and recommended an action for each | 3 fixes confirmed, 1 fix failed (reopen), 1 test blocked |
| **[Additional QA practice](https://github.com/NikaIsaiashvili/qa-practice-portfolio)**<br>Separate repository · in progress | Manual test cases, a Postman API collection, and SQL validation queries | Work in progress; see below |

## Additional QA practice

Independent practice on public practice systems and synthetic data is in a separate repository: **[qa-practice-portfolio](https://github.com/NikaIsaiashvili/qa-practice-portfolio)**.

- **Manual test cases:** 33 test cases and 2 decision tables for the SauceDemo store. Not executed yet.
- **REST API testing:** a Postman collection with 17 requests for the Restful-Booker practice API. 11 requests were run by an AI agent to validate the collection; my own run is pending.
- **SQL validation:** 14 queries on a synthetic SQLite dataset. Executed by an AI agent; my own run is pending.

Those materials were prepared with AI assistance, and the results there are labeled by who executed them. The testing in the two assignment projects above was done by me; the documents here are edited Markdown versions of my original reports.

## Best examples

- **Duplicate transfers.** Double-clicking **Confirm and send** created two Send requests for one transfer. ([Bug #15](01-mini-remittance/defect-report.md#bug-15))
- **Fee mismatch.** For an amount of 1 USD, the calculator showed the minimum fee of 2.00, but the confirmation step charged 0.02. ([Bug #9](01-mini-remittance/defect-report.md#bug-9))
- **Failed fix.** A defect resolved as Fixed was still reproducible in the new build, so I recommended reopening it. ([DV #2](02-online-ordering/defect-validation.md#dv-2))
- **Blocked test.** A page needed for validation returned 404, so the result was recorded as BLOCKED instead of PASS or FAIL. ([DV #6](02-online-ordering/defect-validation.md#dv-6))

## How to read the results

| Term | Meaning in this portfolio |
|---|---|
| Reported defect | Logged by me during testing and open at the time of reporting. Not confirmed or fixed by a developer. |
| Needs requirement clarification | A reported defect whose expected behavior is based on an assumption, because no written requirement existed. |
| Confirmed fix | A resolved issue that I retested and that no longer occurs. |
| Failed fix | A resolved issue that I retested and that still occurs (recommended to reopen). |
| Blocked | A test that could not be run because of another problem. |

## Skills shown

- Exploratory, functional, and negative testing, including boundary and invalid inputs
- Bug reports with preconditions, steps, expected and actual results, and severity
- Module-level acceptance assessment and release recommendation
- Defect validation against Jira resolutions (Fixed, Won't Fix, Cannot Reproduce, FAD (Works as Designed))

- **Tools used in these projects:** Jira, Google Chrome
- **Practice materials:** Postman and SQL (see [qa-practice-portfolio](https://github.com/NikaIsaiashvili/qa-practice-portfolio))
- **Also practiced:** Swagger, Chrome DevTools, TestRail, Zephyr

## Background

Before moving into QA, I worked as an Acquiring Specialist at Georgian Card (2023–2025). I installed, updated, and configured payment-terminal software and worked with internal teams and partners to resolve technical issues. I also have basic frontend knowledge (HTML, CSS, JavaScript, React).

## Contact

- LinkedIn: [linkedin.com/in/nikaisaiashvili](https://www.linkedin.com/in/nikaisaiashvili)
- GitHub: [github.com/NikaIsaiashvili](https://github.com/NikaIsaiashvili)
