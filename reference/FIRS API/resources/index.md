---
title: Resources endpoints
excerpt: Resources endpoints consolidate data required for other endpoints
deprecated: false
hidden: false
metadata:
  robots: index
---
Consider the endpoints under resources are references for data required for other endpoints.

They are:

* countries

  Used in:
  * [`POST` request body in parties endpoint](https://ng.docs.digitax.tech/reference/post_parties) - `address.country_code`
* currencies

  Used in:
  * [`POST` request body in items endpoint](https://ng.docs.digitax.tech/reference/post_items) - `currency_code`
* tax-categories

  Used in:
  * [`POST` request body in items endpoint](https://ng.docs.digitax.tech/reference/post_items) - `tax_category_code`
* invoice-types

  Used in:
  * [`POST` request body in invoices endpoint](https://ng.docs.digitax.tech/reference/post_invoices) - `invoice_type_code`
* payment-means