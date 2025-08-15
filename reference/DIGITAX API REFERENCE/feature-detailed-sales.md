---
title: 'Feature: Detailed Sales'
excerpt: >-
  This endpoint enables integrators to create invoices by including both party
  and item details in a single payload. It’s ideal for clients managing multiple
  parties and items who want a more streamlined approach to handling these
  transactions. 
deprecated: false
hidden: true
icon: fad fa-user-ninja
metadata:
  robots: index
---
# Overview

### Party Details

For B2B transactions, the party’s TIN, name, and email are mandatory. For B2C transactions, the party details are optional, leave the TIN, name, and email fields as empty strings.

### Tax Calculation

The item `unit_price` must be tax exclusive. The tax will be calculated using the `tax_rate` specified in the item object; while factoring in the fee and discount.

More details on, the `document_currency_code`, `tax_category_code`, `invoice_type_code` etc... can be found under the resource section [here](https://ng.docs.digitax.tech/reference/get_resources-countries#/).

### Endpoint:

```json
(https://api.digitax.tech/ng/v1/detailed-invoices)
```

### Payload

```json
{
  "party_tin": "08289985-9145",
  "party_name": "Namiri Technology",
  "party_email": "firs-invoices@namiri.tech",
  "issue_date": "2025-08-15",
  "invoice_type_code": "381",
  "tax_point_date": "2025-08-15",
  "document_currency_code": "NGN",
  "buyer_reference": "#INV-005",
  "due_date": "2025-08-07",
  "notes": "Sample invoice notes",
  "callback_url": "https://example.com/callback",
  "items": [
    {
      "item_code": "20107057",
      "tax_category_code": "STANDARD_VAT",
      "product_category": "Food and Beverage Products",
      "item_name": "Digitax Product 001",
      "hsn_code": "2847.00",
      "item_description": "Sample item description",
      "quantity": 1,
      "unit_price": 10000,
      "discount_rate": 0.05,
      "fee_rate": 0.02,
      "tax_rate": 0.075
    }
  ]
}
```

<br />

### Response

```json
{
  "id": "invoice_01K2PA6VKQRNK79S8DAKABJBFX",
  "created_at": "2025-08-15T07:30:48Z",
  "updated_at": "2025-08-15T07:30:50Z",
  "active": true,
  "party_id": "party_01JXCF3RQXFYCED9SNX55PQ48Y",
  "invoice_date": "2025-08-07",
  "issue_date": "2025-08-07",
  "is_valid": true,
  "transmitted_at": "2025-08-15T07:30:50Z",
  "signed_at": "2025-08-15T07:30:49Z",
  "validated_at": "2025-08-15T07:30:48Z",
  "invoice_type_code": "381",
  "tax_point_date": "2025-08-07",
  "document_currency_code": "NGN",
  "tax_currency_code": "NGN",
  "invoice_number": "INV25-227-073048567-93G8DF",
  "invoice_reference_number": "07304856793G8DF-E3A89069-20250807",
  "buyer_reference": "#INV-005",
  "payment_status": "PENDING",
  "status": "COMPLETED",
  "line_extension_amount": 10000,
  "tax_exclusive_amount": 9700,
  "tax_inclusive_amount": 10427.5,
  "payable_amount": 10427.5,
  "tax_amount": 727.5,
  "billing_reference": [],
  "notes": "Sample invoice notes",
  "qr_code_data": "h40YWkRDHs7FYojTBvI983xy2da+GyQdmrTc9VmLx4Wvzgt5ETiNp3y7fFzMDJJv9RW2Q6cDvhro6KMW539wPUEW+FyMs1dvbkocZQBDXCdizyYSlnqRZXPZNVGOcBjl8fs53LU5AoCbL4Bcg64UChgtJ0zORtqiu4pzYhQSvidUoC9TZ18cZURWmP1kY20AciKFKofrvJQgOeSX3vGoDo3wT/LTBND/FeprUsF0JlV6PqfasyEcXETQ1j6t8o7H0WqjJw7cE/5H4gUxGXr6Hm+yCP1ErQkvVaAs/8mN1IlYkwxIFaDgoM0j8AOY4YuRKOTk406V6DgWFKMPVL7VzA==",
  "taxes": [
    {
      "tax_category_code": "STANDARD_VAT",
      "tax_amount": 727.5,
      "taxable_amount": 9700,
      "tax_percentage": 7.5
    }
  ],
  "items": [
    {
      "id": "invoiceitem_01K2PA6VKQRNK79S8DAPNH5T9K",
      "created_at": "2025-08-15T07:30:48Z",
      "updated_at": "2025-08-15T07:30:48Z",
      "active": true,
      "item_id": "item_01K2PA6FW77HX3E6HTH3DAEVJC",
      "line_extension_amount": 10000,
      "quantity": 1,
      "unit_price": 10000,
      "discount_rate": 0.05,
      "fee_rate": 0.02,
      "discount_amount": 500,
      "fee_amount": 200,
      "tax_rate": 0.075
    }
  ]
}
```

<br />

### Credit and Debit Notes Support

The main difference between detailed credit and debit notes and the original credit and debit notes endpoints is that they use the `item_code` in place of the `item_id` . But the item details and party aren't passed because both were already created when creating the original invoice

Sample Credit Note Request

```
https://api.digitax.tech/ng/v1/credit-notes-with-item-codes
```

```json
{
  "return_date": "2025-08-15",
  "issue_date": "2025-08-15",
  "tax_point_date": "2025-08-15",
  "document_currency_code": "NGN",
  "buyer_reference": "#CN-001",
  "invoice_id": "invoice_01JWR2VH5B3FC4JRXNJDQZCVE6",
  "due_date": "2025-08-15",
  "notes": "Sample credit note notes",
  "callback_url": "https://example.com/callback",
  "items": [
    {
      "item_code": "8000020107057",
      "quantity": 1,
      "unit_price": 10000,
      "discount_rate": 0.05,
      "fee_rate": 0.02,
      "tax_rate": 0.075
    }
  ]
}
```

<br />

### Sample Debit Note Request

```json
https://api.digitax.tech/ng/v1/debit-notes-with-item-codes
```

```json
{
  "debit_date": "2025-08-15",
  "issue_date": "2025-08-15",
  "tax_point_date": "2025-08-15",
  "document_currency_code": "NGN",
  "buyer_reference": "#DN-001",
  "invoice_id": "invoice_01JWR2VH5B3FC4JRXNJDQZCVE6",
  "due_date": "2025-08-15",
  "notes": "Sample debit note notes",
  "callback_url": "https://example.com/callback",
  "items": [
    {
      "item_code": "8000020107057",
      "quantity": 1,
      "unit_price": 10000,
      "discount_rate": 0.05,
      "fee_rate": 0.02,
      "tax_rate": 0.075
    }
  ]
}
```