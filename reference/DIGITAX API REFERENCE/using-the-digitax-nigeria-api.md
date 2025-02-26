---
title: DigiTax Nigeria API Introduction
excerpt: An overview of the DigiTax Nigeria API
deprecated: false
hidden: false
metadata:
  robots: index
---
## Introduction

Before you proceed, we encourage you to get an overview of [DigiTax Nigeria and FIRS e-Invoicing](doc:getting-started) and [FIRS and FIRS e-Invoicing System](doc:firs-e-invoicing-system).

> Use **DigiTax Nigeria API** to integrate your system with FIRS e-Invoicing System for automation and to reduce platform-hopping

<Image className="border" border={true} src="https://files.readme.io/962057ae5fb5cf6fd78c5c3a7a5065cc2b42d10a24798169d1ab2852a3b7fffa-DigiTax-TaxAuthoritiesRegulators.png" />

***

\<Cards columns=\{1}>
&#x20; \<Card title="Prerequisites of using the API" href="https\://ng.docs.digitax.tech/reference/prerequisites-of-using-the-api" icon="fa-list" />

&#x20; \<!---
&#x20; \<Card title="DigiTax Nigeria API sections" href="https\://ng.docs.digitax.tech/reference/digitax-nigeria-api-sections" icon="fa-bars" />
&#x9;\-->
\</Cards>

\<Cards columns=\{1}>
&#x20; \<Card title="Explore resources DigiTax Nigeria API endpoints" icon="fa-book">
&#x20;   Consider endpoints under \*\*/resources\*\* as references for data required for other endpoints.

&#x20;   \* \[/resources/countries]\(https\://ng.docs.digitax.tech/reference/get\_resources-countries)
&#x20;   \* \[/resources/currencies]\()
&#x20;   \* \[/resources//tax-categories]\()
&#x20;   \* \[/resources/invoice-types]\()
&#x20;   \* \[/resources/payment-means]\()
&#x20; \</Card>

&#x20; \<Card title="Explore core DigiTax Nigeria API endpoints" icon="fa-plug">
&#x20;   \* \[/info]\(https\://ng.docs.digitax.tech/reference/get\_info)
&#x20;   \* \[/parties]\(https\://ng.docs.digitax.tech/reference/get\_parties)
&#x20;   \* \[/items]\(https\://ng.docs.digitax.tech/reference/get\_items)
&#x20;   \* \[/invoices]\(https\://ng.docs.digitax.tech/reference/get\_invoices)
&#x20; \</Card>
\</Cards>

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

These are the steps required to get up and running - [Prerequisites of using DigiTax API](https://ng.docs.digitax.tech/update/reference/prerequisites-of-using-the-api)

## Guaranteed safety and integrity

We comply with industry and security best practices.

> 👍 DigiTax is built with the best industry practices and to the highest security standards