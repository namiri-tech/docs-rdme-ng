---
title: NRS e-invoice flow
excerpt: Steps taken when a NRS e-invoice is generated on DigiTax Nigeria API
deprecated: false
hidden: false
metadata:
  robots: index
---
## e-Invoice generation prerequisites

For an invoice to be generated, an item and a party need to be created.

Relevant API endpoints:

1. [Create Party](ref:post_parties)
2. [Create Item](ref:post_items)

## e-Invoice steps

1. [Create Invoice](ref:post_invoices)
2. The Invoice Reference Number (IRN) is generated on DigiTax
   * This marks the invoice as **DRAFT status**
3. Validate invoice request is sent to NRS E-Invoicing System
   * This marks the invoice as **PENDING status**
   * The **QR code** is generated
4. Submit invoice (called **signing**) request is sent to NRS E-Invoicing System
   * This marks the invoice as **COMPLETE**
   * Invoice details are download-able from NRS
5. The **complete** invoice is transmitted to the receiving party (if they have an endpoint registered)
6. The party **accepts** the complete invoice. It's marked accepted when the request is received by the receiving party.
7. Transmission is considered done  :tada:

An invoice is marked **FAILED** if there's an error at step 3.

<Image align="center" border={true} caption="E-invoice flow steps" src="https://files.readme.io/79445835c26f6f1fd85d01b4f717751ba7df8988f762ae3466f1f93fc55e82a2-image.png" />
