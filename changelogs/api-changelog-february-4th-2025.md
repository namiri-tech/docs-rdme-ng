---
title: API ChangeLog - February 5th 2026
author: Namiri Tech
hidden: false
published_at: '2026-02-05T07:43:01.899Z'
---
**Added**: support for `invoice_kind` field and `invoice-level discounts and fees`

<br />

> Date: 2026-02-05

### 1. Introduced `invoice_kind` Field in Invoice Payload

A new `invoice_kind` field has been added to invoice creation payload.

**Supported values**

- `B2C`
- `B2B`

#### Impacted Flows

**Bulk Upload**

- Added `invoice_kind` as a **required** field in the invoice bulk upload template
- Previous bulk upload templates have been **disabled** . Download the new template from the dashboard

**REST API**

- Added `invoice_kind` to invoice creation payloads:

  - `POST /invoices`
  - `POST /app-invoices`
  - `POST /detailed-invoices`

- Credit and debit notes will automatically inherit the `invoice_kind` of the original invoice

- Added `invoice_kind` to invoice download responses

#### Validation Rules

- `invoice_kind` is currently:

  - **Mandatory** for bulk uploads
  - **Optional** for REST invoice creation

  This field will become **mandatory for all flows by end of February**

- A `party` will be required when `invoice_kind = B2B`

#### Backward Compatibility

This update is **non-breaking** for now, but will become mandatory at the end of February.

***

### 2. Added Support for Invoice-Level Discounts and Fees

Invoice-level discounts and fees are now supported in addition to existing item-level discounts.

- The `allowance_charge` field is used to represent invoice-level allowances (discounts) and charges (fees)

#### Sample Payload

```json
"allowance_charge": [
  {
    "charge_indicator": true,
    "amount": 100
  },
  {
    "charge_indicator": false,
    "amount": 50
  }
]
```

#### Additional Enhancements

- Added the following fields for visibility into applied totals:

  - `charge_total_amount` (total fees)
  - `allowance_total_amount` (total discounts)

- Updated invoice amount calculations so that allowances and charges are included in:

  - `tax_exclusive_amount`
  - `tax_inclusive_amount`
  - `payable_amount`

#### Impacted Endpoints

- `POST /invoices`
- `POST /app-invoices`
- `POST /detailed-invoices`

#### Backward Compatibility

This change is **non-breaking** and does not impact existing integrations.

<br />