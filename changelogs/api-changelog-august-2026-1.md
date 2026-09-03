---
title: API ChangeLog - August 2026
author: Namiri Tech
hidden: false
published_at: '2026-08-27T06:42:52.837Z'
---
## NRS Invoice Type Code Alignment for Self-Billed Invoices and Debit Notes

We’ve released an update to improve invoice type accuracy and consistency with NRS for self-billed invoice flows.

### What changed

- Invoice type code **394** has been updated to match NRS and now reflects **Self-billed-invoice-Debit note**
- Creating a self-billed invoice with invoice type code **385** now works accurately
- Creating a debit note against a self-billed invoice now correctly uses invoice type code **394**

### Customer impact

- Improved alignment between DigiTax and NRS invoice type handling
- More reliable self-billed invoice and debit note classification
- Reduced risk of mismatched document typing during downstream validation and reconciliation

### Action required

- Re-fetch the latest invoice type codes from:
  - `GET /ng/v1/resources/invoice-types`
  - [https://ng.docs.digitax.tech/reference/get_resources-invoice-types](https://ng.docs.digitax.tech/reference/get_resources-invoice-types)
- If your integration uses hardcoded invoice type mappings, update them to reflect the latest values