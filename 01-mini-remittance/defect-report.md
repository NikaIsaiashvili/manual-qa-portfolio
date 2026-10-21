# Mini Remittance: Defect Report

[← Back to project overview](README.md)

This report lists all 23 defects logged during manual testing of the Mini Remittance money transfer console. The original report was a PDF with screenshots. This Markdown version keeps the same content, with these changes:

- Wording was edited for grammar, step numbering, and consistent button and field names.
- A few details that were visible only in the original screenshots were added to the text. They are marked *(from screenshot)*.
- Bug #3: the original expected result contained a typo (both fields were described as showing Name information). It was corrected to the intended meaning.

> **Note:** No full written specification was provided. Some expected results are based on common rules for money transfer systems rather than on a documented requirement (for example, the missing balance and card features). The [project overview](README.md#findings-by-type) shows which defects depend on requirement confirmation.

## Environment

| Item | Value |
|---|---|
| Application | Mini Remittance, Money Transfer Console (local build) |
| Application URL | Local environment (`127.0.0.1`) |
| Browser | Google Chrome 153.0.8010.53 (64-bit) |
| Operating system | Windows |
| Screen resolution | 1920 × 1080 |
| Test account | Operator role |
| Money transfer systems | Western Union, MoneyGram |
| Test date | 23 September 2026 |
| Test type | Manual testing |

## Summary

| # | Summary | Severity |
|---|---|---|
| [1](#bug-1) | Login succeeds when a Georgian-alphabet username is entered in the Username field | Minor |
| [2](#bug-2) | Western Union window opens when Send/Receive Money is selected from MoneyGram | Major |
| [3](#bug-3) | Name and Surname fields show swapped hint text when hovering over "*" | Minor |
| [4](#bug-4) | Name and Surname fields accept numbers, symbols, and special characters | Minor |
| [5](#bug-5) | Name and Surname fields have no length limit | Minor |
| [6](#bug-6) | Phone field accepts non-numeric characters | Minor |
| [7](#bug-7) | Entered phone and Document Number are not displayed after completing a transfer | Minor |
| [8](#bug-8) | Document Number field accepts any input in the Send Money modal | Major |
| [9](#bug-9) | Fee calculation differs between the calculator and the confirmation step | Major |
| [10](#bug-10) | Notification shows a different transfer number after Send Money confirmation | Major |
| [11](#bug-11) | Time cannot be changed in the Transfer History date filter | Minor |
| [12](#bug-12) | Transfer History "From" and "To" calendars overlap when opened together | Minor |
| [13](#bug-13) | Send Money request is sent for an unregistered receiver | Major |
| [14](#bug-14) | Georgian characters are displayed as encoded symbols in the History PDF | Minor |
| [15](#bug-15) | Double-clicking Confirm and send creates duplicate Send requests | Major |
| [16](#bug-16) | Send Money accepts excessively large amounts in the Amount field | Major |
| [17](#bug-17) | User balance is not available in the application | Major |
| [18](#bug-18) | Send Money flow does not validate available balance before payment | Major |
| [19](#bug-19) | Card management and balance top-up functionality are not available | Major |
| [20](#bug-20) | Settings functionality is not available for the user account | Major |
| [21](#bug-21) | Clear Data deletes all Send/Receive history without confirmation | Major |
| [22](#bug-22) | Continue to AML check does not respond when Somalia is selected as destination | Major |
| [23](#bug-23) | Previous step cannot be accessed from the Western Union confirmation flow | Minor |

**Total:** 23 defects: 13 Major, 10 Minor. All were open at the time of reporting.

---

<a id="bug-1"></a>
## Bug #1: Login succeeds when a Georgian-alphabet username is entered

**Severity:** Minor

**Preconditions**
- A user with the username `operator` exists.
- The user is on the Login page.

**Steps to reproduce**
1. Enter `ოპერატორ` (the word "operator" written in Georgian letters) in the Username field.
2. Enter the valid password for the operator account.
3. Click **Sign in**.

**Expected result:** Login fails because `ოპერატორ` does not exactly match the registered username `operator`.

**Actual result:** Login succeeds and the user is logged in to the operator account.

---

<a id="bug-2"></a>
## Bug #2: Western Union window opens when Send/Receive Money is selected from MoneyGram

**Severity:** Major

**Preconditions**
- The user is logged in.
- Both Western Union and MoneyGram options are available.

**Steps to reproduce**
1. Open the Money Transfer section.
2. Select **MoneyGram**.
3. Select **Send Money** or **Receive Money**.
4. Observe the window that opens.

**Expected result:** The MoneyGram Send/Receive Money window opens.

**Actual result:** The Western Union window opens instead of the MoneyGram window.

---

<a id="bug-3"></a>
## Bug #3: Name and Surname fields show swapped hint text

**Severity:** Minor

**Preconditions**
- The user is logged in.

**Steps to reproduce**
1. Open the Send/Receive Money modal.
2. Hover over the `*` icon next to the **Name** field and read the hint.
3. Hover over the `*` icon next to the **Surname** field and read the hint.

**Expected result:** Each field shows its own hint: the Name field shows Name-related information, and the Surname field shows Surname-related information.

**Actual result:** The Name field shows the Surname hint, and the Surname field shows the Name hint.

---

<a id="bug-4"></a>
## Bug #4: Name and Surname fields accept numbers, symbols, and special characters

**Severity:** Minor

**Preconditions**
- The user is logged in.

**Steps to reproduce**
1. Open the Send/Receive Money modal.
2. Enter numbers, symbols, or special characters in the Name field.
3. Enter numbers, symbols, or special characters in the Surname field.

**Expected result:** The Name and Surname fields do not accept numbers, symbols, or special characters.

**Actual result:** Both fields accept numbers, symbols, and special characters.

---

<a id="bug-5"></a>
## Bug #5: Name and Surname fields have no length limit

**Severity:** Minor

**Preconditions**
- The user is logged in.

**Steps to reproduce**
1. Open the Send/Receive Money modal.
2. Enter a long string of characters in the Name field.
3. Enter a long string of characters in the Surname field.
4. Observe the fields.

**Expected result:** The fields enforce a defined minimum and maximum length.

**Actual result:** The fields accept input of any length. The long values are carried through to the review and AML screening step *(from screenshot)*.

---

<a id="bug-6"></a>
## Bug #6: Phone field accepts non-numeric characters

**Severity:** Minor

**Preconditions**
- The user is logged in.

**Steps to reproduce**
1. Open the Send/Receive Money modal.
2. Enter letters or special characters in the Phone field.
3. Complete the money transfer.

**Expected result:** The Phone field accepts only numeric characters in a defined phone number format.

**Actual result:** The Phone field accepts non-numeric characters.

---

<a id="bug-7"></a>
## Bug #7: Entered phone and Document Number are not displayed after completing a transfer

**Severity:** Minor

**Preconditions**
- The user is logged in.

**Steps to reproduce**
1. Open the Send/Receive Money modal.
2. Fill in all fields, including Phone and Document Number.
3. Complete the money transfer.
4. Download the PDF for this transfer.
5. Open the completed transfer details.

**Expected result:** The entered phone and Document Number are shown in the transfer details or the transfer PDF.

**Actual result:** The phone and Document Number are not shown anywhere after the transfer is completed. The PDF contains the transfer number, date, status, sender, receiver, destination, amount, and fee, but not these two fields *(from screenshot)*.

---

<a id="bug-8"></a>
## Bug #8: Document Number field accepts any input

**Severity:** Major

**Preconditions**
- The user is logged in.

**Steps to reproduce**
1. Open the Send Money modal.
2. Enter any value in the Document Number field.
3. Fill in the remaining required fields.
4. Complete the money transfer.

**Expected result:** The Document Number field applies validation rules and blocks the transfer when the value is not valid.

**Actual result:** The transfer is completed regardless of the value entered in the Document Number field.

---

<a id="bug-9"></a>
## Bug #9: Fee calculation differs between the calculator and the confirmation step

**Severity:** Major

**Preconditions**
- The user is logged in.
- The Send Money flow is open.

**Steps to reproduce**
1. Open the Send Money flow.
2. Select a transfer currency.
3. Enter `1` as the transfer amount.
4. Check the fee shown by the calculator. The calculator label reads *Fee (1.5%, minimum 2.00)* *(from screenshot)*.
5. Continue to the confirmation step.
6. Check the fee and total charge before confirming.
7. Repeat with the other available currencies.

**Expected result:** The same fee rule is applied throughout the flow. For an amount of 1, the minimum fee of 2.00 is applied in every currency.

**Actual result:** The confirmation step shows a different fee from the calculator:
- **USD/EUR:** the calculator shows the expected fee, but the confirmation shows a fee of 0.02 and a total charge of 1.02.
- **GEL:** the confirmation shows a fee of 0.01 GEL and a total charge of 1.01 GEL.

---

<a id="bug-10"></a>
## Bug #10: Notification shows a different transfer number after confirmation

**Severity:** Major

**Preconditions**
- The user is logged in.
- The Send Money flow is available.

**Steps to reproduce**
1. Open the Send Money flow.
2. Enter the required transfer details.
3. Confirm the money transfer.
4. Note the Transfer Number shown after confirmation.
5. Look at the notification in the bottom-right corner.
6. Compare the two Transfer Numbers.

**Expected result:** The same Transfer Number is shown after confirmation and in the notification.

**Actual result:** The notification shows a different Transfer Number from the one shown after confirmation.

---

<a id="bug-11"></a>
## Bug #11: Time cannot be changed in the Transfer History date filter

**Severity:** Minor

**Preconditions**
- The user is logged in.
- Transfer History is available.

**Steps to reproduce**
1. Find Transfer History on the main page.
2. Open the date filter.
3. Select a date.
4. Click the dropdown arrow for the time.
5. Try to select a different time.

**Expected result:** The time dropdown opens and a different time can be selected.

**Actual result:** The time dropdown does not respond, and the time cannot be changed.

---

<a id="bug-12"></a>
## Bug #12: "From" and "To" calendars overlap when opened together

**Severity:** Minor

**Preconditions**
- The user is on the Transfers search/filter section.

**Steps to reproduce**
1. Open the **From** calendar.
2. Open the **To** calendar while the From calendar is still open.
3. Observe the position of the calendars.

**Expected result:** The calendars do not overlap, and all calendar elements stay visible and usable.

**Actual result:** The second calendar overlaps and covers part of the first calendar.

---

<a id="bug-13"></a>
## Bug #13: Send Money request is sent for an unregistered receiver

**Severity:** Major

**Preconditions**
- The user is logged in.
- Send Money functionality is available.
- The receiver is not registered in the system.
- The receiver is not on the AML watchlist.

**Steps to reproduce**
1. Open the Send Money modal.
2. Enter the Name and Surname of an unregistered receiver.
3. Enter the remaining required details.
4. Confirm the money transfer.
5. Observe the result.

**Expected result:** The system checks that the receiver is registered before sending the request.

**Actual result:** The request is sent even though the receiver is not registered.

---

<a id="bug-14"></a>
## Bug #14: Georgian characters are displayed as encoded symbols in the History PDF

**Severity:** Minor

**Preconditions**
- The user is logged in.
- A transfer contains Georgian characters in the Sender or Receiver name.
- Transfer History is available.

**Steps to reproduce**
1. Create a transfer with Georgian characters in the Sender or Receiver name.
2. Open Transfer History.
3. Download the PDF for that transfer.
4. Check the Sender/Receiver name in the PDF.

**Expected result:** Georgian characters are displayed correctly and are readable.

**Actual result:** Georgian characters are shown as unreadable encoded symbols.

---

<a id="bug-15"></a>
## Bug #15: Double-clicking Confirm and send creates duplicate Send requests

**Severity:** Major

**Preconditions**
- The user is logged in.
- Send Money functionality is available.
- All required transfer fields are completed.

**Steps to reproduce**
1. Open the Send Money flow.
2. Fill in all required fields.
3. Go to the confirmation step.
4. Click **Confirm and send** twice quickly.
5. Check the created transfers in Transfer History.

**Expected result:** Only one Send request is created, even if the button is clicked several times.

**Actual result:** Two Send requests are created. In Transfer History they have different transfer numbers and the same timestamp *(from screenshot)*.

---

<a id="bug-16"></a>
## Bug #16: Send Money accepts excessively large amounts

**Severity:** Major

**Preconditions**
- The user is logged in.
- Send Money functionality is available.

**Steps to reproduce**
1. Open the Send Money flow.
2. Enter a very large number in the Amount field, for example `666666666666666666666666666666666666666666666666`.
3. Fill in the remaining required fields.
4. Confirm the money transfer.
5. Observe the result.

**Expected result:** The Amount field enforces a maximum amount and blocks the transfer when the amount is above the limit.

**Actual result:** The amount is accepted, shown in scientific notation (for example `7e+85`), and the transfer is completed.

---

<a id="bug-17"></a>
## Bug #17: User balance is not available in the application

**Severity:** Major

**Preconditions**
- The user is logged in.

**Steps to reproduce**
1. Log in to the application.
2. Go through the available sections.
3. Look for the user's current balance.

**Expected result:** The user's current balance is available and displayed.

**Actual result:** No user balance is available or displayed anywhere in the application.

---

<a id="bug-18"></a>
## Bug #18: Send Money flow does not validate available balance before payment

**Severity:** Major

**Preconditions**
- The user is logged in.
- Send Money functionality is available.

**Steps to reproduce**
1. Open the Send Money flow.
2. Enter the required transfer details.
3. Enter any amount.
4. Proceed with the transfer.

**Expected result:** The system checks the available balance before completing the transfer and blocks it when the balance is not enough.

**Actual result:** No balance check is performed before the transfer is completed.

---

<a id="bug-19"></a>
## Bug #19: Card management and balance top-up are not available

**Severity:** Major

**Preconditions**
- The user is logged in.

**Steps to reproduce**
1. Log in to the application.
2. Go through the account and payment sections.
3. Look for options to add or remove a bank card.
4. Look for an option to top up the balance.

**Expected result:** The application allows adding and removing a bank card and topping up the balance.

**Actual result:** There is no option to add or remove a bank card or to top up the balance.

---

<a id="bug-20"></a>
## Bug #20: Settings functionality is not available for the user account

**Severity:** Major

**Preconditions**
- The user is logged in.

**Steps to reproduce**
1. Log in to the application.
2. Open the user/operator account area.
3. Look for a Settings option.

**Expected result:** The user can open account Settings.

**Actual result:** No Settings functionality is available.

---

<a id="bug-21"></a>
## Bug #21: Clear Data deletes all Send/Receive history without confirmation

**Severity:** Major

**Preconditions**
- The user is logged in.
- Send/Receive transfer history exists.

**Steps to reproduce**
1. Open the application.
2. Make sure the Send/Receive history contains transfers.
3. Click **Clear Data**.
4. Observe the result.

**Expected result:** A confirmation dialog is shown before the history is deleted.

**Actual result:** All Send/Receive history and related information are deleted immediately, without a confirmation step.

---

<a id="bug-22"></a>
## Bug #22: Continue to AML check does not respond when Somalia is selected

**Severity:** Major

**Preconditions**
- The user is logged in.
- Send Money functionality is available.
- Somalia is available as a destination country.

**Steps to reproduce**
1. Open the Send Money flow.
2. Select **Somalia** as the destination country.
3. Fill in the required transfer details.
4. Click **Continue to AML check**.
5. Observe the result.

**Expected result:** The flow moves to the AML check step.

**Actual result:** Nothing happens, and the flow does not move to the AML check step.

---

<a id="bug-23"></a>
## Bug #23: Previous step cannot be accessed from the Western Union confirmation flow

**Severity:** Minor

**Preconditions**
- The user is logged in.
- Send Money functionality is available.

**Steps to reproduce**
1. Click **Send**.
2. Fill in all required fields.
3. Click **Continue to AML check**.
4. Observe the confirmation modal.
5. Try to go back to the previous step.

**Expected result:** The user can go back to the previous step and edit the entered information without restarting the transfer.

**Actual result:** There is no option to go back from the confirmation modal.

---

[← Back to project overview](README.md) · [Acceptance assessment →](acceptance-assessment.md)
