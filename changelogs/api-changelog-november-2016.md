---
title: API ChangeLog - November 2016
author: Namiri Tech
hidden: false
published_at: '2026-11-10T07:26:09.536Z'
---
# Update Item Details

### Update Item Details Through the API

Added support for updating existing item details through the API. Businesses can now update an item's name and display name, or add an item code if one has not already been assigned.

**Endpoint:** `PUT /items/{item_id}`

**Supported Updates:**

- **Item Code:** Add an item code to an existing item that does not already have one.
- **Item Name:** Update an item's name.
- **Display Name:** Update the name displayed on the dashboard or invoices.

**Request Body:**

```json
{
  "item_code": "SKU-123",
  "item_name": "Example product",
  "display_name": "Product"
}
```

**Behaviour and Validation:**

- You can submit one or more fields in a single request
- Omitted fields remain unchanged
- Item codes can only be added if the item does not already have one. Existing item codes cannot be modified
- Item names and display names can be updated at any time

**Success Response:** `200 OK` – Returns the updated item object<br /><br />Note: This is not a breaking change.