---
title: API ChangeLog - January 28th 2026
author: Namiri Tech
hidden: false
published_at: '2026-01-28T13:00:40.996Z'
---
**Added:** Support for Updating Party Details

<br />

> Date: 2026-01-28

### Added

#### Support for Updating Party Details

- **New Endpoint (Optional)**
  `PUT /ng/v1/parties/{party_id}`
  Enables updating existing party details.

- **Enhanced Functionality**
  Added support for using a **Company Incorporation Number** in place of a **TIN** for Nigerian parties that do not yet have a TIN.

### Affected Endpoints

- `POST /parties`
- `POST /detailed-invoices`

### Validation Requirements

When using a Company Incorporation Number, it must follow this format:

- Prefix: `RC` (uppercase)
- Separator: `-` (hyphen)
- Suffix: 6–7 digits

**Example:** `RC-123456` or `RC-1234567`

### Backward Compatibility

- This change is **non-breaking** and does not affect existing integrations.

<br />