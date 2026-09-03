---
title: API ChangeLog — August 2026
author: Namiri Tech
hidden: false
published_at: '2026-08-11T08:45:59.434Z'
---
## 1. Price Unit Quantity Codes

### What's Changed

We have added support for **Price Unit Quantity Codes** through the `price_unit` field.

The `price_unit` field is currently **optional for a one-month transition period**. After this period, it will become **mandatory**.

Please update your systems to pass a valid `price_unit` to ensure continued compatibility.

> **Breaking Change:** Once `price_unit` becomes mandatory, requests that do not include this field will be rejected.

### Affected Endpoints

**Invoices & Credit and Debit Notes**

- `POST /ng/v1/invoices`
- `POST /ng/v1/credit-notes`
- `POST /ng/v1/detailed-invoices`
- `POST /ng/v1/credit-notes-with-item-codes`
- `POST /ng/v1/debit-notes-with-item-codes`

**App Invoices**

- `POST /ng/v1/app-invoices`

### Example — Invoice Item

```json
{
  "items": [
    {
      "item_id": "item_01JWBBCVSHK3ZQAVNPW2MPSQXS",
      "quantity": 1,
      "unit_price": 10000,
      "discount_rate": 0.05,
      "fee_rate": 0.02,
      "tax_rate": 0.075,
      "item_description": "Sample item description",
      "price_unit": "H87"
    }
  ]
}
```

### Example — App Invoice

```json
{
  "price": {
    "price_amount": 10,
    "base_quantity": 1,
    "price_unit": "H87"
  }
}
```

A valid **Price Unit Quantity Code** must be provided. Please refer to the Price Unit Quantity Code list for the supported values <Anchor target="_blank" href="https://ng.docs.digitax.tech/reference/get_resources-invoice-quantity-codes">here</Anchor>

### Action Required

Integrators should update their systems to include `price_unit` in all applicable requests before the end of the one-month transition period.

***

## 2. Partial Payments on Update Payment Status

### What's Changed

Support has been added for recording **partial payments** when updating an invoice's payment status.

When setting an invoice's `payment_status` to `PARTIAL`, the `amount` of the payment must be provided.

### Affected Endpoint

`POST /ng/v1/invoices/{invoice_id}`

### Example Request

```json
{
  "payment_status": "PARTIAL",
  "reference": "PY012001",
  "amount": 10
}
```

### Important

Partial payments cannot be specified when **creating an invoice**, as NRS does not support an initial `PARTIAL` payment status.

Attempting to create an invoice with `payment_status: PARTIAL` will return a validation error:

```json
{
  "code": 400,
  "data": null,
  "message": "error has occurred",
  "error": {
    "id": "ddf072e5-c3c6-4803-84fe-a313723ed94c",
    "handler": "invoice_actions",
    "details": "initial invoice payment status cannot be PARTIAL or REJECTED",
    "public_message": "validation failed: we are unable to process your request. also confirm this is not a duplicate request"
  }
}
```

### Integration Flow

1. Create the invoice without a `PENDING` payment status.
2. Set `payment_status` to `PARTIAL`.
3. Include the payment `amount` and `reference(optional)`.