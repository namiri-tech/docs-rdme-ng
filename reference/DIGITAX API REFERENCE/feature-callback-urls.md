---
title: 'Feature: Callback URLs'
deprecated: false
hidden: false
metadata:
  robots: index
---
## Understanding Callback URLs

When you make a request to DigiTax API, we immediately return a response. The status of that transaction by default is `DRAFT`.

*Below is a snippet of the response to a POST invoice request. The status property reads "DRAFT".*

<Image align="center" className="border" border={true} width="350px" src="https://files.readme.io/a6e9db30b2930a71ed72df2de6cb9f65fc4f2981c619208035e43005591cce35-CleanShot_2025-08-05_at_15.41.22_22x.png" />

We save it into our queuing system to be **signed**. This step changes the status property from `DRAFT` to `COMPLETED`. This is apparent via the DigiTax Dashboard or when you make a **GET** request.

*Below is a snippet of the response of a GET invoice request. The status property reads "COMPLETED".*

<Image align="center" className="border" border={true} width="350px" src="https://files.readme.io/2f38cdc542d8670232c027c758f7263d47d41c330337d25e98f10701112ad275-CleanShot_2025-08-05_at_15.41.412x.png" />

*Below is the invoice above as viewed on the dashboard*

<Image align="center" width="750px" src="https://files.readme.io/59c30d5bd519109170d2c465091f48d5fbba9c3e8cb501a6807a68782d27f96a-CleanShot_2025-08-05_at_15.29.112x.png" />

<br />

The tax authority's system or DigiTax may take some time to sign an invoice, and it is not efficient to have you, as the API caller or consumer, wait for a response. Callback URLs are useful since they inform you as soon as a particular event like a status change happens after data processing on the tax authority's system or DigiTax.

## Where to use Callback URLs

We accept an optional `callback_url` property for the following endpoints:

* [Add invoice](ref:post_invoices)  (**POST**)
* <Anchor label="Add credit note" target="_blank" href="ref:post_credit-notes">Add credit note</Anchor>  (**POST**)
* <Anchor label="Add debit note" target="_blank" href="ref:post_debit-notes">Add debit note</Anchor>  (**POST**)

More details under [Scenarios](#scenarios)  section below.

During testing, we encourage you to use a site like [webhook.site](https://webhook.site)

Our system will POST data to the callback URL when we have new information about the invoice, usually after syncing with the tax authority's system.

## Scenarios

We send a callback when invoice has been signed.

When an invoice, credit note, or debit note has been synced to FIRS (or signed), we also send a POST request to the `callback_url`. The request body contains a `data` object with details about the synced invoice, credit note, or debit note and an `event` property with the value `sale.sync`.

## Structure and example

Example response when an invoice, credit note, or debit note has been synced to FIRS (or has been signed)

```json
{
  "data": {
    "id": "invoice_01K1X2Z26VPAVPTMTA3CGTWCQ8",
    "original_invoice_id": null,
    "created_at": "2025-08-05T12:23:12.351Z",
    "updated_at": "2025-08-05T12:23:13.181Z",
    "active": true,
    "party_id": "party_01K1SMHY16R73ZZA7QYR6R44Y5",
    "invoice_date": "2025-08-05",
    "issue_date": "2025-08-05",
    "is_valid": true,
    "transmitted_at": null,
    "signed_at": "2025-08-05T12:23:13.181Z",
    "validated_at": "2025-08-05T12:23:12.785Z",
    "invoice_type_code": "381",
    "tax_point_date": null,
    "document_currency_code": "NGN",
    "tax_currency_code": "NGN",
    "invoice_number": "INV25-217-122312346-Q42FME",
    "invoice_reference_number": "122312346Q42FME-E3A89069-20250805",
    "buyer_reference": null,
    "payment_status": "PENDING",
    "delivery_date": null,
    "status": "COMPLETED",
    "line_extension_amount": 100,
    "tax_exclusive_amount": 97,
    "tax_inclusive_amount": 104.28,
    "payable_amount": 104.28,
    "tax_amount": 7.28,
    "billing_reference": null,
    "dispatch_document_reference": null,
    "receipt_document_reference": null,
    "originator_document_reference": null,
    "contract_document_reference": null,
    "due_date": null,
    "notes": "Sample invoice notes",
    "qr_code_data": "VoOXpj/c15gM1jriqcKAsr/5nl8bkm1ZkKRc8s2w23x7ldFVvL4ve8wA+GWHCpd/zmBn8K0lDdHW9MKdawtBY4IoisYvqoGCczzfVP6YNamvgCtav39f3e7VGmsOahcPyrYTs+zM7R+v8lmU/oXTwaf8zvpIsYowpGE4Y3sXv+5WqZ4j361CWViPFPuFzCORkdxU5tjCCxGJ2BqDTOBxBGT4ei21e4Fl2V6pdx9m5Crab63KiYjbOAj7SkWYbih7oL93N/4F/AHYsc4GYNvZyWxdzdx8xLy4igBNpNZ/wsU5rmvAnuPZjFpRECcPriZD7Q302kK+j1GhHx6KbftVig==",
    "taxes": [
      {
        "tax_category_code": "STANDARD_GST",
        "tax_amount": 7.28,
        "taxable_amount": 97,
        "tax_percentage": 7.5
      }
    ],
    "items": [
      {
        "id": "invoiceitem_01K1X2Z26VPAVPTMTA3GH8TX1C",
        "created_at": "2025-08-05T12:23:12.351Z",
        "updated_at": "2025-08-05T12:23:12.351Z",
        "active": true,
        "item_id": "item_01K1SMDHV51XTR7MHT3TFFEYKA",
        "line_extension_amount": 100,
        "quantity": 1,
        "price_amount": 100,
        "discount_rate": 0.05,
        "fee_rate": 0.02,
        "discount_amount": 5,
        "fee_amount": 2,
        "tax_rate": 0.075
      }
    ]
  },
  "event": "invoice.signed"
}
```