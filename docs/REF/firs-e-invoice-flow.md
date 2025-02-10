---
title: FIRS e-invoice flow
deprecated: false
hidden: false
metadata:
  robots: index
---
## e-Invoice generation prerequisites

For an invoice to be generated, an item and a party need to be created.

Relevant API endpoints:

1. \[Create Party]\(Create Party)
2. [Create Item](ref:post_items)

## e-Invoice steps

1. [Create Invoice](ref:post_invoices)
2. The IRN is generated on DigiTax system
   1. This marks the invoice as **DRAFT status**
3. Validate invoice request is sent to FIRS e-invoicing system
   * This marks the invoice as **PENDING status**
   1. The **QR code** is generated
4. Submit invoice (called signing) request is sent to FIRS e-invoicing system
   * This marks the invoice as **COMPLETE**
   * Invoice details are download-able from FIRS
5. The **complete** invoice is transmitted to the receiving party (if they have an endpoint registered)
6. The party **accepts** the complete invoice. It's marked accepted when the request is received by the receiving party.
7. Transmission is considered done  :tada:

An invoice is marked **FAILED** if there's an error at step 3.

![](https://files.readme.io/79445835c26f6f1fd85d01b4f717751ba7df8988f762ae3466f1f93fc55e82a2-image.png)

<br />

<br />

\[block:image] &#x20;
\{
&#x20; "images": \[
&#x20;   \{
&#x20;     "image": \[
&#x20;       "https\://files.readme.io/d517b8f45ddc1edc3bf1e83f07575bf27ec7810fc92d23db0c218ce77c1f7d14-image.png",
&#x20;       null,
&#x20;       "E-INVOICE flow steps"
&#x20;     ],
&#x20;     "align": "center",
&#x20;     "border": true,
&#x20;     "caption": "E-INVOICE flow steps"
&#x20;   }
&#x20; ]
}
\[/block]