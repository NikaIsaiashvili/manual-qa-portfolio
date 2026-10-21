# Manual QA Portfolio: Nika Isaiashvili

Manual QA Engineer based in Tbilisi, Georgia. This repository contains my testing work: a defect report, a release acceptance assessment, and defect validation records.

All projects here are **practical QA assignments or independent practice**. They are not commercial projects, and I did not develop the applications I tested.

## Projects

| Project | What it shows | Documents |
|---|---|---|
| **[Mini Remittance: Money Transfer Application Testing](01-mini-remittance/README.md)**<br>Practical assignment · Sep 2026 | Exploratory and negative testing of a money transfer console. 23 documented defects (13 Major, 10 Minor), a status for each of 13 modules, and a release recommendation. | [Defect report](01-mini-remittance/defect-report.md) · [Acceptance assessment](01-mini-remittance/acceptance-assessment.md) |
| **[Online Ordering Web Application: Defect Validation](02-online-ordering/README.md)**<br>Practical assignment · 2026 | Retesting 10 resolved Jira issues in a new build: confirmed fixes, a failed fix to reopen, and a test blocked by a 404 error. | [Validation records](02-online-ordering/defect-validation.md) |
| **[API and SQL Practice](03-api-and-sql-practice/README.md)**<br>Planned | Planned exercises for REST API testing and SQL data checks. No results published yet. | None yet |

## Highlights

- **Duplicate transfers:** double-clicking **Confirm and send** created two Send requests. ([Bug #15](01-mini-remittance/defect-report.md#bug-15))
- **Fee inconsistency:** for an amount of 1 USD, the calculator showed the minimum fee of 2.00, but the confirmation step charged 0.02. ([Bug #9](01-mini-remittance/defect-report.md#bug-9))
- **No amount limit:** an excessively large amount was accepted, displayed in scientific notation (such as `7e+85`), and the transfer was completed. ([Bug #16](01-mini-remittance/defect-report.md#bug-16))
- **Fix that did not work:** a defect marked Fixed was still reproducible in the new build and was recommended for reopening. ([DV #2](02-online-ordering/defect-validation.md#dv-2))

## Testing skills shown

- Exploratory, functional, and negative testing
- Input validation and boundary testing (amount limits, field length, allowed characters)
- Bug reports with preconditions, steps to reproduce, expected and actual results, and severity
- Severity classification (Major / Minor)
- Module-level acceptance assessment and release recommendation
- Defect validation against Jira resolutions (Fixed, Won't Fix, Cannot Reproduce, Not a Bug (FAD))
- Recording blocked tests and explaining why they could not be completed

## Tools

- **Used in these projects:** Jira, Google Chrome
- **Also practiced:** Postman, Swagger, SQL, Chrome DevTools, TestRail, Zephyr, Git/GitHub

## Background

Before moving into QA, I worked as an Acquiring Specialist at Georgian Card (2023–2025). I installed, updated, and configured payment-terminal software and helped resolve technical issues. I also have basic frontend knowledge (HTML, CSS, JavaScript, React), which you can see in my other repositories.

## Contact

- LinkedIn: [linkedin.com/in/nikaisaiashvili](https://www.linkedin.com/in/nikaisaiashvili)
- GitHub: [github.com/NikaIsaiashvili](https://github.com/NikaIsaiashvili)
