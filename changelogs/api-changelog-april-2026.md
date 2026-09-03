---
title: API ChangeLog - April 2026
author: Namiri Tech
hidden: false
published_at: '2026-04-27T18:12:48.561Z'
---
**Improved**: Invoice and Issue Date Validation Enforcement

***

### Invoice and Issue Date Validation Enforcement

We’ve introduced stricter validation on invoice `issue_date` and `invoice_date` to align with NRS requirements.

#### What Changed

- Invoices can now **only be created with the current date**.
- **Back-dated** and **future-dated** invoices are no longer allowed.

#### Affected Endpoints

- `POST /invoices`
- `POST /detailed-invoices`
- `POST /credit-notes`
- `POST /debit-notes`
- `POST /credit-notes-with-item-codes`
- `POST /debit-notes-with-item-codes`

<br />

#### Error Response

Requests with an invalid `issue_date` will return:

```json
{
  "message": "issue_date NRS does not support back-dating or future-dating of invoices.",
  "code": "400",
  "metadata": {
    "argument": "issue_date"
  }
}
```

<br />

#### Impact

- This is a **breaking change**.
- Any existing integrations that submit invoices with past or future dates will fail.

#### Recommended Action

- Ensure your system always sets `issue_date` and `invoice_date` to the **current date** at the time of invoice creation.
- Review and update any workflows that rely on backdating or scheduling invoices.

<br />