---
title: API ChangeLog - December 22nd 2025
author: Namiri Tech
hidden: false
published_at: '2025-12-22T06:47:49.334Z'
---
**Added**: Support for Cross-Border Transactions

<br />

> Date: 2025-12-22

We have added support for cross-border transactions by enabling the creation of non-Nigerian (non-NG) parties.

Affected Endpoints

`POST /parties`

`POST /detailed-invoices`

**Behavior Changes**

**Party Validation Logic**

- If a TIN is provided and no address is supplied, the party is assumed to be Nigerian.
  - The TIN will be validated as a Nigerian TIN.
  - If validation succeeds, a default Nigerian address will be applied.
- For cross-border transactions, the address is required.
  - The country is derived from the address object.
  - TIN validation is determined based on the country specified in the address.
  - Non-Nigerian parties are supported when a non-NG country is provided.

**Invoice Processing**

- Cross-border invoices are not added to the invoice transmission queue.

**Backward Compatibility**

- This update is non-breaking.
- Existing integrations that omit the address for Nigerian parties will continue to function as before.

<br />