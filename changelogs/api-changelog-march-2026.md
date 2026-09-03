---
title: API ChangeLog - March 2026
author: Namiri Tech
hidden: false
published_at: '2026-04-16T12:22:33.754Z'
---
Additions and Improvements:<br />**Added**:<br />- payment status on invoice creation,<br />- Restriction on updating payment status<br />- Downloads (Purchases) callback support<br />**Improved**:<br />- HSN & ISIC Code Validation<br />- Registration Number Validation

***

## Additions

### 1. Payment Status on Invoice Creation

You can now optionally include a `payment_status` field when creating an invoice.

```json
{
  "payment_status": "PAID"
}
```

- Field is optional
- Supported values depend on existing payment status enums `["PAID", "REJECTED", "PENDING"]`

### 2. Restriction on Updating Payment Status

Payment status can **only be updated for signed invoices**.

If attempted on unsigned invoices, the API returns:

```json
{
  "message": "can only update payment status of invoices that have been signed",
  "code": "412"
}
```

***

### 3. Downloads (Purchases) Callback Support

A callback event is now triggered when a download (purchase invoice) is fetched from NRS.

**How it works:**

- Callback URLs are configured at the **business level**
- Setup is handled by the internal support team
- Users must provide a publicly accessible URL via:

  - Email/Slack/Teams/other communication channels
- The endpoint:

  - Must **not require authentication**
  - Should be able to receive a download (purchase) event payloads

***

### 4. New Tax Categories

The `/resources/tax-categories` endpoint now includes additional tax categories:

```json
[
  {
    "code": "WITHHOLDING_TAX",
    "name": "Withholding Tax",
    "tax_rate": null,
    "has_rate": false
  },
  {
    "code": "EXEMPTED",
    "name": "Tax Exemption",
    "tax_rate": null,
    "has_rate": false
  },
  {
    "code": "STAMP_DUTY",
    "name": "Stamp Duty",
    "tax_rate": null,
    "has_rate": false
  }
]
```

***

## Improvements

### 1. HSN & ISIC Code Validation

Validation has been introduced for `hsn_code` and `isic_code` against NRS resources.

**Applies to:**

- `POST /ng/v1/items` (item creation)
- `POST /ng/v1/detailed-invoices` (detailed invoice creation)
- Item bulk uploads

**Sample Request:**

```json
{
  "tax_category_code": "STANDARD_VAT",
  "product_category": "Food and Beverage Products",
  "item_name": "Digitax Product 001",
  "hsn_code": "2847",
  "description": "Sample item description",
  "display_name": "Digitax Product 001",
  "price_unit": "NGN per 1",
  "item_code": "820057",
  "is_service": true
}
```

**Validation Error Example:**

```json
{
  "message": "hsn_code invalid ISIC code for service",
  "code": "400",
  "metadata": {
    "argument": "hsn_code"
  }
}
```

***

### 2. Registration Number Validation Update

The API now accepts **5-digit registration numbers** in addition to existing formats.

**Newly supported format:**

- `RC-12345`

**Previously supported:**

- 6-digit and 7-digit formats

**Backward Compatibility**
This change is non-breaking and does not impact existing integrations.