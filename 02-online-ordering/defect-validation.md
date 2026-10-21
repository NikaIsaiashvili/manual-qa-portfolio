# Online Ordering Web Application: Defect Validation Records

[← Back to project overview](README.md)

**Build tested:** 2.0 · **Test type:** Defect validation (DV) · **Tester:** Nika Isaiashvili · **Year:** 2026

The original records were in a PDF document with links to the Jira tickets. This Markdown version keeps the validation steps and results, with light editing for grammar. Jira links, ticket IDs, the application URL, and the names of training staff were removed. Each issue's resolution comes from the Jira ticket screenshot in the original document.

**Not a Bug (FAD)** is the resolution used in the tickets for issues closed as "not a defect".

## Decision rules

Each issue already had a resolution in Jira. The goal of validation was to check whether that resolution was still correct in build 2.0. The original document defined these rules; the four marked in bold are used below.

| Resolution | What validation checks | PASS | FAIL |
|---|---|---|---|
| **Fixed** | The original problem no longer occurs | Resolution confirmed | Reopen the defect |
| **Won't Fix** | The behavior is still present and the Won't Fix decision still applies | Decision confirmed | Escalate for reconsideration |
| **Cannot Reproduce** | Following the original steps gives the expected result | Cannot Reproduce confirmed | Reopen with new evidence |
| Duplicate | The same defect already exists | Duplicate confirmed | Reopen as a unique defect |
| **Not a Bug (FAD)** | The described behavior is correct by design | Behavior confirmed as designed | Reopen as a valid defect |
| Fixed indirectly | Fixed as a side effect of another change | Indirect fix confirmed | Reopen the defect |

## Results summary

| # | Issue | Resolution | DV result | Defect action |
|---|---|---|---|---|
| [1](#dv-1) | Website is accessible over unsecured HTTP instead of HTTPS | Not a Bug (FAD) | PASS | Close (decision confirmed) |
| [2](#dv-2) | Pizza size options are not selectable | Fixed | **FAIL** | **Reopen** |
| [3](#dv-3) | Classic Chicken Shawarma image is not animated | Not a Bug (FAD) | PASS | Close (PM confirmation required) |
| [4](#dv-4) | Weight Loss Calculator uses a 1414 kcal deficit instead of 1000 kcal | Fixed | PASS | Close (remains resolved) |
| [5](#dv-5) | Beef Noodles displays a burger image | Won't Fix | PASS | Close (remains resolved) |
| [6](#dv-6) | Garlic Aioli product image is missing | Cannot Reproduce | **BLOCKED** | Do not close |
| [7](#dv-7) | Original price is not displayed for discounted combos | Won't Fix | PASS (conditional) | Close, if the PM confirms Won't Fix |
| [8](#dv-8) | Combo menu items are missing the calorie badge | Not a Bug (FAD) | PASS | Close (remains resolved) |
| [9](#dv-9) | About Us footer is missing | Fixed | PASS | Close (remains resolved) |
| [10](#dv-10) | Cart item count is not centered in the badge | Fixed | PASS | Close (remains resolved) |

**Totals:** 10 issues: 7 PASS, 1 conditional PASS, 1 FAIL, 1 BLOCKED.

---

<a id="dv-1"></a>
## 1. [Security] Website is accessible over unsecured HTTP instead of HTTPS

**Resolution:** Not a Bug (FAD). The training center decided that the current behavior is not a defect, and the ticket was closed.

**Validation steps**
1. Open the website using the `http://` protocol.
2. Check the URL in the browser address bar.
3. Compare the behavior with the original description and actual result in the ticket.
4. Check whether the website stays on HTTP instead of redirecting to HTTPS.
5. Review the ticket comment that records the decision.
6. Record the result and attach a screenshot as evidence.

**Expected result:** The original behavior is still present (the site stays on HTTP, with no redirect to HTTPS). Validation should confirm that it is unchanged in build 2.0 and that the decision still applies.

**Actual result:** The behavior is unchanged from the original description.

**DV result:** PASS · **Defect action:** Close (decision confirmed by the training center).

---

<a id="dv-2"></a>
## 2. [Menu] Pizza size options are not selectable in the Pizza section

**Resolution:** Fixed

**Validation steps**
1. Open the website.
2. Open the Pizza section.
3. Try to select the Small, Medium, and Large sizes on a pizza item.
4. Check whether the selection works (for example, whether the price changes).
5. Repeat on at least one other pizza item to rule out an item-specific problem.
6. Record the result.

**Expected result:** The Small, Medium, and Large options can be selected.

**Actual result:** The size options still cannot be selected, the same behavior as originally reported. The fix does not appear to be in build 2.0.

**DV result:** FAIL · **Defect action:** Reopen, so that development can investigate again before the 2.0 release sign-off.

---

<a id="dv-3"></a>
## 3. [Menu] Classic Chicken Shawarma card image is not animated in the Shawarma section

**Resolution:** Not a Bug (FAD)

**Validation steps**
1. Open the website.
2. Open the Shawarma section.
3. Look at the images on the shawarma product cards.
4. Compare the Classic Chicken Shawarma image with the other card images.
5. Compare with the original description in the ticket.
6. Record the result.

**Expected result:** The Classic Chicken Shawarma image stays static while the other cards stay animated, as described in the ticket.

**Actual result:** The Classic Chicken Shawarma image is static, and the other shawarma cards are animated. The behavior matches the original ticket.

**DV result:** PASS · **Defect action:** Close (PM confirmation required).

---

<a id="dv-4"></a>
## 4. [Menu Planner] Weight Loss Calculator uses a 1414 kcal deficit instead of 1000 kcal

**Resolution:** Fixed

**Original problem:** With the test data below, the ticket recorded a 1414 kcal deficit for both the Sedentary and Extra Active activity levels.

**Validation steps**
1. Open the website and go to the Menu Planner section.
2. Enter: weight 100 kg, target 80 kg, height 191 cm, age 20, male, speed 1 kg/week.
3. With activity level **Sedentary**, record Maintenance Calories and Weight Loss Calories.
4. Repeat with activity level **Extra Active**.
5. Compare both deficits with the expected 1000 kcal.

**Expected result:** The calculator applies a 1000 kcal deficit for every activity level.

**Actual result**

| Activity level | Maintenance | Weight loss | Deficit |
|---|---|---|---|
| Sedentary | 2677 kcal | 1677 kcal | 1000 kcal |
| Extra Active | 4239 kcal | 3239 kcal | 1000 kcal |

Both deficits match the expected 1000 kcal.

**DV result:** PASS · **Defect action:** Close (remains resolved). The fix is confirmed.

---

<a id="dv-5"></a>
## 5. [Menu] Beef Noodles displays a burger image in the Wok section

**Resolution:** Won't Fix

**Validation steps**
1. Open the website.
2. Open the Wok section.
3. Find the Beef Noodles product card and look at its image.
4. Compare with the original description in the ticket.
5. Check the ticket for the reason behind the Won't Fix decision.

**Expected result:** The original behavior may still be present. Validation should confirm that it is still present and that the Won't Fix decision still applies.

**Actual result:** The Beef Noodles card still shows a burger image instead of a Beef Noodles image. The original issue is still reproducible in build 2.0.

**DV result:** PASS · **Defect action:** Close (remains resolved as Won't Fix).

---

<a id="dv-6"></a>
## 6. [Menu] Garlic Aioli product image is missing in the Sauces section

**Resolution:** Cannot Reproduce

**Validation steps**
1. Open the website.
2. Open the Sauces section.
3. Find the Garlic Aioli product card.
4. Check whether its product image is displayed.
5. Compare with the original description in the ticket.

**Expected result:** The Sauces section opens and the Garlic Aioli image is displayed (the issue does not reproduce).

**Actual result:** The Sauces section redirects to a 404 Not Found page. The Garlic Aioli card cannot be reached, so the original issue cannot be validated.

**DV result:** BLOCKED / NOT TESTABLE · **Defect action:** Do not close based on this result. Recommendation: retest after the Sauces section is available.

---

<a id="dv-7"></a>
## 7. [Menu] Original price is not displayed for discounted combo items

**Resolution:** Won't Fix

**Validation steps**
1. Open the website.
2. Open the Combos menu.
3. Find a discounted combo, for example Classic Combo.
4. Look at the price information on the card.
5. Check whether the current price and savings amount are shown.
6. Check whether the original price is shown.

**Expected result:** The original behavior may still be present. Validation should confirm that it is still present and that the Won't Fix decision still applies.

**Actual result:** The Classic Combo shows the current discounted price and the savings amount, but not the original price. The original behavior is still reproducible in build 2.0.

**DV result:** PASS, only if the PM/customer decision confirms Won't Fix · **Defect action:** Close (remains resolved).

---

<a id="dv-8"></a>
## 8. [Menu] Combo menu items are missing the calorie badge

**Resolution:** Not a Bug (FAD)

**Validation steps**
1. Open the website.
2. Open the Combo menu.
3. Compare the combo item cards with other menu item cards.
4. Check whether calorie badges are shown on combo items.
5. Compare with the original description in the ticket.
6. Check the ticket for the reason it was marked Not a Bug.

**Expected result:** The behavior matches the product design: combo items without calorie badges are intentional.

**Actual result:** Combo items do not show calorie badges, which matches the documented product decision.

**DV result:** PASS · **Defect action:** Close (remains resolved). The Not a Bug resolution is confirmed.

---

<a id="dv-9"></a>
## 9. [About Us] Section footer is missing

**Resolution:** Fixed

**Validation steps**
1. Open the website.
2. Go to the About Us section.
3. Scroll to the bottom of the page.
4. Check whether the footer is displayed.
5. Compare with the original description in the ticket.
6. Check that the footer has the expected content and navigation links.

**Expected result:** The footer is shown at the bottom of the About Us section with the expected content and navigation.

**Actual result:** The footer is displayed correctly with the expected content and navigation. The original issue is no longer reproducible.

**DV result:** PASS · **Defect action:** Close (remains resolved). The fix is confirmed.

---

<a id="dv-10"></a>
## 10. [Cart] Item count number is not centered within the cart badge

**Resolution:** Fixed

**Validation steps**
1. Open the website.
2. Find the cart icon and look at the item count in the circular badge.
3. Add one item to the cart and check the count.
4. Add more items and check the count again.
5. Check that the number is centered vertically and horizontally in the badge.
6. Compare with the original description in the ticket.

**Expected result:** The item count is centered vertically and horizontally in the circular badge.

**Actual result:** The item count is correctly centered for the tested cart quantities. The original alignment issue is no longer reproducible.

**DV result:** PASS · **Defect action:** Close (remains resolved). The fix is confirmed.

---

[← Back to project overview](README.md)
