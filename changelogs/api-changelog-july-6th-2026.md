---
title: API Changelog – July 6th 2026
author: Namiri Tech
hidden: false
published_at: '2026-07-06T18:31:50.325Z'
---
**Breaking change**: `invoice_kind` field is now mandatory for invoice creation.

## Breaking Change: `invoice_kind` Field is Now Mandatory for Invoice Creation

Following the latest NRS guidelines, the `invoice_kind` field is now **mandatory** for all invoice creation requests submitted through the REST API.

### Supported Values

The following values are supported for `invoice_kind`:

- `B2C`
- `B2B`
- `B2G`

### Impacted Endpoints

The following invoice creation endpoints now require the `invoice_kind` field:

- `POST /invoices`
- `POST /app-invoices`
- `POST /detailed-invoices`

### Credit & Debit Notes

Credit notes and debit notes will automatically inherit the `invoice_kind` value from the original invoice. No additional changes are required when creating these document types.

### Validation Rules

The API now enforces the following validation rules:

- `invoice_kind` is **mandatory** for all REST API invoice creation requests.
- When `invoice_kind` is set to `B2B` or `B2G`, **party information is required** in the invoice payload.

> **Note:** The `invoice_kind` field was originally introduced as an **optional** field in the <Anchor target="_blank" href="https://ng.docs.digitax.tech/changelog/api-changelog-february-4th-2025">February API release</Anchor>. This update changes its behavior from optional to mandatory.

### Backward Compatibility

> **Breaking Change**

This change is **not backward compatible**. Existing integrations that create invoices without the `invoice_kind` field will fail validation until they are updated to include a valid value.