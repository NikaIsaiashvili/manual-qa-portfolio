# Online Ordering Web Application: Defect Validation

[← Back to portfolio](../README.md)

**Type:** Practical manual QA assignment · **Date:** 2026 · **Build tested:** 2.0 · **Tester:** Nika Isaiashvili

I validated issues that had already been reported and resolved in Jira for a food-ordering website used for QA training. I did not develop this application.

**Result:** 10 issues validated: 7 PASS, 1 conditional PASS, 1 FAIL (reopen), 1 BLOCKED.

| Document | Content |
|---|---|
| [Defect validation records](defect-validation.md) | Validation steps, expected and actual results, and the decision for all 10 issues |

## What was tested

I validated ten issues in the website's menu sections, a calorie calculator, the About Us page, the cart badge, and HTTP/HTTPS access. Each issue already had a resolution in Jira: Fixed, Won't Fix, Cannot Reproduce, or Not a Bug (FAD).

## Why defect validation was needed

Before the 2.0 release, each resolution had to be checked in the new build:

- **Fixed:** the original problem should no longer occur.
- **Won't Fix** and **Not a Bug (FAD):** the behavior should be unchanged, and the decision should still apply.
- **Cannot Reproduce:** the original steps should now give the expected result.

## How expected and actual behavior were compared

1. Read the original ticket: steps to reproduce, actual result, expected result, and resolution.
2. Followed validation steps based on the original steps, with extra checks where useful (for example, a second pizza item, or several cart quantities).
3. Set the expected result according to the resolution. For a Fixed issue, the problem should be gone; for a Won't Fix or Not a Bug issue, the original behavior should still be present.
4. Ran the steps in build 2.0 and recorded the actual result.

## How results were recorded

In the original document, each issue had five fields: Actual Result, DV Result, Evidence, Defect Action, and Comment. Evidence was a screenshot or a link to the Jira ticket. This portfolio shows the expected result, actual result, DV result, and defect action; evidence and Jira links are not published.

## Results summary

| # | Issue | Resolution | DV result |
|---|---|---|---|
| 1 | Website is accessible over unsecured HTTP instead of HTTPS | Not a Bug (FAD) | PASS |
| 2 | Pizza size options are not selectable | Fixed | **FAIL: reopen** |
| 3 | Classic Chicken Shawarma image is not animated | Not a Bug (FAD) | PASS |
| 4 | Weight Loss Calculator uses a 1414 kcal deficit instead of 1000 kcal | Fixed | PASS |
| 5 | Beef Noodles displays a burger image | Won't Fix | PASS |
| 6 | Garlic Aioli product image is missing | Cannot Reproduce | **BLOCKED** |
| 7 | Original price is not displayed for discounted combos | Won't Fix | PASS (conditional) |
| 8 | Combo menu items are missing the calorie badge | Not a Bug (FAD) | PASS |
| 9 | About Us footer is missing | Fixed | PASS |
| 10 | Cart item count is not centered in the badge | Fixed | PASS |

Full steps, expected and actual results, and defect actions are in the [validation records](defect-validation.md).

## Examples

**Confirmed fix: calorie calculator ([#4](defect-validation.md#dv-4)).** The ticket reported a 1414 kcal deficit instead of 1000 kcal. With the same test data, build 2.0 gave 2677 − 1677 = 1000 kcal (Sedentary) and 4239 − 3239 = 1000 kcal (Extra Active). Both match the expected 1000 kcal, so the fix is confirmed.

**Unresolved issue: pizza sizes ([#2](defect-validation.md#dv-2)).** The ticket was resolved as Fixed, but the Small, Medium, and Large options still could not be selected, the same behavior as originally reported. Result: FAIL, with a recommendation to reopen the defect before the 2.0 release sign-off.

**Blocked test: Garlic Aioli image ([#6](defect-validation.md#dv-6)).** The ticket was resolved as Cannot Reproduce. The Sauces section redirected to a 404 Not Found page, so the product card could not be reached. The result was recorded as BLOCKED, and the issue should not be closed based on this validation.

**Decision confirmed, not a fix: Beef Noodles image ([#5](defect-validation.md#dv-5)).** The wrong image is still shown. The issue was resolved as Won't Fix, so validation confirms that the decision still applies instead of marking it as a failure.

## Notes

- Of the 4 issues resolved as Fixed, 3 fixes were confirmed and 1 failed.
- A PASS on a Won't Fix or Not a Bug issue means the documented decision still applies. It does not mean the behavior is ideal.

---

[← Back to portfolio](../README.md)
