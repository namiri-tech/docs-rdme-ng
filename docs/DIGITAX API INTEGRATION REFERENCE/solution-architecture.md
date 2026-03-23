---
title: 'Solution Architecture '
excerpt: >-
  DigiTax and NRS Solution Achitecture - System Integrator and Access Point
  Provider flow
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

1. ERP/accounting system **submits an invoice/credit or debit note** to the DigiTax ingestion flow.
2. The **payload schema check** validates the submitted invoice.

   * If the schema check fails, an **error** is returned to the ERP and the flow stops.
3. If the schema check passes, the invoice proceeds into the DigiTax system.
4. DigiTax **generates an IRN (invoice reference number)** and prepares the **QR code data**, then **saves the invoice, IRN and QR code** to the database.
5. DigiTax **submits the invoice to NRS for validation**.
6. NRS **returns a validation response** to DigiTax.
7. If the validation response indicates an error, DigiTax **returns the validation error response** to the ERP.
8. If validation is successful, DigiTax **submits a signing request** to NRS.
9. NRS **returns the signing response** (signed invoice / confirmation) to DigiTax.
10. DigiTax **returns the final response** to the ERP — this includes the invoice data, IRN number and QR code data.

Notes:

* The initial API response (implied earlier) confirms invoice creation on DigiTax, but the QR code is available only after signing/IRN generation.
* Error handling occurs at schema validation and NRS validation stages; success moves the invoice forward to signing and finalization.

<Image align="center" border={false} src="https://files.readme.io/0e0326cd3ea933505172ae03643990993fec334c2a8e058cfd314fc935d778d9-DigiTax_Nigeria_e-Invoicing_Model.drawio.png" />