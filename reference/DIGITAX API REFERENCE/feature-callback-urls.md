---
title: 'Feature: Callback URLs'
deprecated: false
hidden: true
metadata:
  robots: index
---
## Understanding Callback URLs

When you make a request to DigiTax API, we immediately return a response. The status of that transaction by default is `pending` because we save it into our queuing system to be relayed to the tax authority's system. Eventually, the status moves from `pending` to `complete`, and this is apparent via the DigiTax dashboard or when you make a **GET** request.

The tax authority's system or DigiTax may take some time to process a request, and it is not efficient to have you as the caller wait for a response. Callback URLs are useful since they inform you as soon as a particular event like a status change happens after data processing on the tax authority's system or DigiTax.

## Where to use Callback URLs

We accept an optional `callback_url` property for both [Add business item](ref:post_items)  (**POST**) and [Add invoice](ref:post_invoices)  (**POST**) endpoints. More details under [Scenarios](#scenarios)  section below.

During testing, we encourage you to use a site like [webhook.site](https://webhook.site)

Our system will POST data to the callback URL when we have new information about the item or sale, usually after syncing with the tax authority's system.

## Scenarios

We send the following callbacks:

* When an item has been synced to eTIMS, we send a POST request to the provided `callback_url`. The request body contains a `data` object with details about the synced item, and an `event` property with the value `item.sync`.
* When a sale/ credit note has been synced to eTIMS, we also send a POST request to the `callback_url`. The request body contains a `data` object with details about the synced sale, and an `event` property with the value `sale.sync`.

## Structure and examples

* When an item has been synced to eTIMS

```json
  {
    "data": {
      "item_class_code": "70101500",
      "item_type_code": "1",
      "item_name": "Water bottle",
      "origin_nation_code": "UG",
      "package_unit_code": "BA",
      "quantity_unit_code": "BG",
      "tax_type_code": "B",
      "default_unit_price": 900,
      "id": "<ITEM_ID>",
      "etims_item_code": "<eTIMS_ID>",
      "is_stock_item": true,
      "running_balance": 0
    },
    "event": "item.sync"
  }
```

* When a sale/ credit note has been synced to eTIMS

```json
  {
    "data": {
      "date": "01/02/2024",
      "time": "07:45:34 pm",
      "trader_invoice_number": "ACC-SINV-2022-00015",
      "original_invoice_number": "720001",
      "digitax_id": "<SALE_ID>",
      "serial_number": "<SERIAL_NUMBER>",
      "receipt_number": "17",
      "internal_data": "<INTERNAL_DATA>",
      "receipt_signature": "FGUWWXNHSOSKVDCI",
      "etims_url": "https://etims-sbx.kra.go.ke/common/link/etims/receipt/indexEtimsReceiptData?Data=P000000001G02FGUWWXNHSOSKVDCI",
      "sale_detail_url": "http://localhost:8080/sales/cls3g6np300028cegs6o8qw98",
      "customer_pin": "A123456789Z",
      "customer_name": "Test Customer",
      "queue_status": "completed",
      "invoice_number": "720005",
      "sales_tax_summary": {
        "taxable_amount_a": 0,
        "taxable_amount_b": -4655.17,
        "taxable_amount_c": 0,
        "taxable_amount_d": 0,
        "taxable_amount_e": 0,
        "tax_rate_a": 0,
        "tax_rate_b": -16,
        "tax_rate_c": 0,
        "tax_rate_d": 0,
        "tax_rate_e": -8,
        "tax_amount_a": 0,
        "tax_amount_b": -744.83,
        "tax_amount_c": 0,
        "tax_amount_d": 0,
        "tax_amount_e": 0
      }
    },
    "event": "sale.sync"
  }
```