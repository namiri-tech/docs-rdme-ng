---
title: 'Feature: Detailed Sales'
excerpt: >-
  This endpoint enables integrators to create invoices by including both party
  and item details in a single payload. It’s ideal for clients managing multiple
  parties and items who want a more streamlined approach to handling these
  transactions. 
deprecated: false
hidden: false
icon: fad fa-user-ninja
metadata:
  robots: index
---
# Overview

### Party Details

For B2B transactions, the party’s TIN, name, and email are mandatory. For B2C transactions, the party details are optional; leave the fields "party_tin","party_name" and "party_email" as empty strings.

### Tax Calculation

Within the item object, users are required to provide pre-calculated values for `total_amount`, `taxable_amount`, and `tax_amount`.

More details on, the `document_currency_code`, `tax_category_code`, `invoice_type_code` etc... can be found under the resource section [here](https://ng.docs.digitax.tech/reference/using-the-digitax-nigeria-api#/).

### Endpoint:

```json
https://api.digitax.tech/ng/v1/detailed-invoices
```

### Payload

```json
{
    "party_tin": "08289985-9145", //The Taxpayer Identification Number (TIN) assigned to the buyer
    "party_name": "Namiri Technology", // The registered name of the buyer receiving the invoice. This is the official business or individual name
    "party_email": "firs-invoices@namiri.tech", // The buyer's official email address used for communication regarding invoices and tax compliance
    "party_address": { // The buyer address is optional in this endpoint
      "street_name": "123 Main St",
      "city_name": "Lagos",
      "postal_zone": "100001",
      "country_code": "NGA"
    },
    "issue_date": "2025-08-15", //The date on which this invoice was issued in the format YYYY-MM-DD
    "invoice_type_code": "381", // A code that specifies the type of invoice being issued
    "tax_point_date": "2025-08-15", //The actual date when the tax becomes applicable in the format YYYY-MM-DD
    "document_currency_code": "NGN", // A code that specifies the default currency in which the invoice is issued
    "buyer_reference": "#INV-005", //A reference number or code provided by the buyer to track the invoice
    "due_date": "2025-08-07", //The date on which this invoice is due in the format YYYY-MM-DD
    "notes": "Sample invoice notes", // Additional invoice information that is not contained explicitly in other structures
    "callback_url": "https://example.com/callback", // The URL to call when we have new information about the invoice, when the invoice is signed successfully or validation has failed
    "items": [
        {
            "item_code": "20107057", //A unique product code assigned to the item in the user's system. It will be used as the unique product identifier
            "tax_category_code": "STANDARD_VAT", // The code for the tax category the item belongs to. It must be one of the tax categories defined in the resources API
            "product_category": "Food and Beverage Products", // The category the product belongs to. You can use the United Nations Standard Products and Services Code (UNSPSC) as a guide
            "item_name": "Digitax Product 001", //The name of the good or service being sold
            "hsn_code": "2847.00", // The Harmonized System of Nomenclature (HSN) Code for the product
            "item_description": "Sample item description", // A brief description of the item
            "quantity": 1, // The total number of items sold in the invoice line
            "unit_price": 10000, // The unit price of this line item before tax
            "discount_rate": 0.05, //The discount rate applied to the item. It must be a value between 0 and 1, where 0 means no discount and 1 means a 100% discount on the price
            "fee_rate": 0.02, //The rate of any additional fees (e.g. service charge, delivery fee). It must be a value between 0 and 1, where 0 means no fee and 1 means a 100% fee on the price
            "tax_rate": 0.075, // The tax rate applied to the item. It must be a value between 0 and 1. For tax category codes that already have a defined tax rate, this value must match the tax category's tax rate
            "taxable_amount": 9700, // The amount on which tax is calculated. It must be equal to the line extension amount (unit price * quantity) plus fees minus discounts. This value will be ignored unless the business has the permission to calculate tax
            "tax_amount": 727.5 // The tax amount for this line item. It must be equal to the taxable amount multiplied by the tax rate. This value will be ignored unless the business has the permission to calculate tax
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
      "tax_rate": 0.075,
      "taxable_amount": 9700, 
      "tax_amount": 727.5
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
      "tax_rate": 0.075,
      "taxable_amount": 9700, 
      "tax_amount": 727.5
    }
  ]
}
```
