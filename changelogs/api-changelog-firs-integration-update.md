---
title: API ChangeLog - August 10th 2025
author: Namiri Tech
hidden: false
published_at: '2025-08-10T15:31:00.000Z'
---
Several API enhancements done

<br />

> Date: 2025-08-10

## Overview

This release introduces additional FIRS-specific fields to our API and enhances our ability to distinguish between goods and services. The changes affect the **Invoice**, **Item**, and **bulk upload** functionalities within the FIRS integration.

***

## **1. New Fields Added**

### **Invoice Table**

The following new fields have been added to support FIRS requirements:

* `issue_time`
* `accounting_cost`
* `invoice_delivery_period`
* `additional_document_reference`
* `payee_party`
* `bill_party`
* `ship_party`
* `tax_representative_party`
* `payment_means`
* `payment_terms_note`
* `allowance_charge`

**Notes:**

* These fields are now available on the **invoice creation** and **detailed-invoice creation** endpoints.
* Similar to the `customer_party`, **credit notes** and **debit notes** automatically inherit the other party details (`payee_party`, `bill_party`, `ship_party`, `tax_representative_party`) from the original invoice.
  * Therefore, these fields **are not required** in credit and debit note creation payloads.
* The new party-related fields have also been added to the **invoice bulk upload template**.

***

## **2. Distinguishing Between Goods and Services**

### **New Field: `isService`**

A new field, `isService`, has been added to both the **API** and **GraphQL (GQL)** endpoints.

**Behavior:**

* The `isService` flag indicates whether an item represents a **service** (`true`) or a **good** (`false`).
* This field is included during:
  * Item creation
  * Detailed invoice creation

**Automatic Field Mapping:**

When `isService = true`, we populate the `isic_code` and `service_category` with the `hsn_code` and `product_category`.

* `isic_code` ← `hsn_code`
* `service_category` ← `product_category`

**FIRS Sync Behavior:**

* Both `isic_code` and `service_category` values are now synchronized to FIRS.
* This enhancement allows FIRS to distinguish between goods and services on their end as well.

***

## **Impact Summary**

| Area               | Change Type | Description                              |
| ------------------ | ----------- | ---------------------------------------- |
| Invoice Endpoints  | Enhancement | Added new FIRS-compliant fields          |
| Credit/Debit Notes | Behavior    | Party fields now inherited automatically |
| Bulk Upload        | Enhancement | Template updated with new party fields   |
| Item API           | Enhancement | Introduced `isService` flag              |
| FIRS Sync          | Enhancement | Improved goods vs. services distinction  |

***