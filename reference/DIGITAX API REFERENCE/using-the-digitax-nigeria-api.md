---
title: DigiTax API Setup
excerpt: All you need to start using the API
deprecated: false
hidden: false
metadata:
  robots: index
---
## Introduction

Before you proceed, we encourage you to get an overview of [DigiTax Nigeria and FIRS e-Invoicing](doc:getting-started) and [FIRS and FIRS e-Invoicing System](doc:firs-e-invoicing-system).

Briefly, **DigiTax** is a solution that sits between you; the taxpayer, and the systems of regional tax authorities/ regulators. For Nigeria, that is, the FIRS e-Invoicing System.

> **DigiTax Nigeria** integrates you with FIRS e-Invoicing System

<Image align="center" border={true} caption="DigiTax - Tax authorities/ regulators" src="https://files.readme.io/962057ae5fb5cf6fd78c5c3a7a5065cc2b42d10a24798169d1ab2852a3b7fffa-DigiTax-TaxAuthoritiesRegulators.png" />

## DigiTax API

Namiri Technologies, through our DigiTax Platform, have developed a suite of solutions:

* DigiTax App (Compatible with Android POS),
* DigiTax Dashboard (Web Browser-based Desktop application)
* DigiTax API

> The first two are powered by the DigiTax API :tada:

### DigiTax API Features

The DigiTax API is built with various industry standards for API platforms in mind. These include:

* RESTful API
* OpenAPI (formerly Swagger): An open-source standard that allows a standardized way to generate, document, and test our APIs.
* Secure authentication with cryptographically signed JWTs (JSON Web Tokens)

To use this API, you'll need access to DigiTax Dashboard environment to get an X-API-Key. Get in touch with [our team](mailto:support@namiri.tech).

Below are the steps required to get up and running

## Prerequisites of using the API

The following are the steps to getting a sandbox business (for testing before you go LIVE)

1. [Sign up on DigiTax](https://digitax.tech/sign-up)
2. Create an organization.
3. Email [support@namiri.tech](mailto:support@namiri.tech) requesting access to a SANDBOX business
4. Once you have access to a sandbox business, you can now transact on the dashboard
5. We'll also share an API Key.

Use the **X-API-Key** in your header when making API calls through the interactive API docs [here](/reference) OR via your integration during testing.

<br />

Once signed up on DigiTax, you can generate an e-invoice via:

* the DigiTax Dashboard
  * the DigiTax API
    * the DigiTax App
      <br />
      Below are the details on an e-invoice when downloaded via the Dashboard.
      <br />

## e-invoice sections

<br />

\[block:image]\
\{\
"images": \[
\{
"image": \[
"[https://files.readme.io/beb06a39e60ef12a080e0a12971be349f904c923c022190afbfcbb57a4a01922-CleanShot\_2025-02-01\_at\_12.05.23\_22x.png](https://files.readme.io/beb06a39e60ef12a080e0a12971be349f904c923c022190afbfcbb57a4a01922-CleanShot_2025-02-01_at_12.05.23_22x.png)",
"",
"e-invoice with key sections highlighted"
],
"align": "center",
"border": true,
"caption": "e-invoice with key sections highlighted"
}
]
}
\[/block]

<br />

An e-invoice has three key components: (They are highlighted above)

<br />

1. A QR code\
   2\. The tax breakdown of that invoice
   3\. e-invoice metadata that includes:
   * Date and Time of transaction
     * Invoice number
       * Signature
         * Internal Data

* DigiTax Dashboard (Web Browser-based Desktop application for e-invoicing) and
  * DigiTax API (for system-to-system integration without the issue of platform hopping).

\[block:image]\
\{
"images": \[
\{
"image": \[
"[https://files.readme.io/503b6f0-small-Full\_Logo\_Slogan\_Colour.png](https://files.readme.io/503b6f0-small-Full_Logo_Slogan_Colour.png)",
null,
""
],
"align": "center",
"sizing": "300px"
}
]
}
\[/block]

Here, at the DigiTax API hub, we cover guides, recipes and API reference to get you ready to integrate with the DigiTax API. Consider reviewing the [digitax.tech](https://digitax.tech)  webpage for more on the **DigiTax Dashboard** and **DigiTax app**.

## What can DigiTax help me with?

Our DigiTax Dashboard and DigiTax app use the **DigiTax API** in the background. The API is designed to optimize smart invoicing, tracking purchases and inventory management among other ZRA Smart Invoice functionalities in the following ways:

* Asynchronous functionality that automatically retries ZRA Smart Invoice System (or any other tax agency system).\
  This mitigates against duplication of invoices and associated tax obligations
  * Guarantee that the same invoice won't be submitted more than once
    * Recording of purchases in addition to sales to ensure all ZRA Smart Invoice-related data is accessible in a single place
      * Throttling between your business' throughput and ZRA Smart Invoice System.\
        A business only needs to send an invoice once, and DigiTax will process the information thereafter based on ZRA Smart Invoice System capacity at that particular point in time
        * Real-time notifications
          * Priority support
            * Simple integration.\
              We’ve streamlined integration reducing the work required by 70%. To start with you can interact with the API endpoints [here](/reference)
              * Code samples in 19 different integration programming languages to choose from when using the interactive API reference. This reduces the likelihood of errors during the development workflow
                * 99.99% uptime
                  * Queuing and scaling (allowing us to support any amount of volume)
                    * Get notifications on transaction statuses via [Callback URLs](doc:call-back-urls)
                      * Intuitive DigiTax dashboard for you and your stakeholders\
                        It serves for redundancy and e-invoicing

## Guaranteed safety and integrity

We comply with best industry and security practices.

> 👍 DigiTax is built with the best industry practices and to the highest security standards

### Overall

The DigiTax App and Dashboard users securely sign up and log in via social media credentials (Google and Microsoft) or email address, one-time pin/password, and secure email links.

> The dashboard is where you sign up and set up profiles and businesses outrightly as a product user or before integration.
>
> All activity is logged for audit trail and compliance checks and all information is encrypted and transmitted for\
> maximum protection

### API

The API is built with various industry standards for API platforms in mind, but some of the most common ones include:

1. RESTful API\
   2\. OpenAPI (formerly Swagger): An open-source standard that allows a standardised way to generate, document, and test our APIs.
   3\. Secure authentication with cryptographically signed JWTs (JSON Web Tokens)

To use this API, you'll need access to DigiTax Dashboard environments. Get in touch with our Sales team.