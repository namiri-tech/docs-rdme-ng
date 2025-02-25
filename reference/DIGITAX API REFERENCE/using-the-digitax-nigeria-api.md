---
title: DigiTax API Introduction
excerpt: An overview of the DigiTax API
deprecated: false
hidden: false
metadata:
  robots: index
---
## Introduction

Before you proceed, we encourage you to get an overview of [DigiTax Nigeria and FIRS e-Invoicing](doc:getting-started) and [FIRS and FIRS e-Invoicing System](doc:firs-e-invoicing-system).

<Columns layout="auto">
  <Column>
    > Use **DigiTax Nigeria API** to integrate your system with FIRS e-Invoicing System
    > The main utility of the DigiTax API is to integrate your system with FIRS e-Invoicing System for automation and to reduce platform-hopping
  </Column>

  <Column>
    <Image border={true} src="https://files.readme.io/962057ae5fb5cf6fd78c5c3a7a5065cc2b42d10a24798169d1ab2852a3b7fffa-DigiTax-TaxAuthoritiesRegulators.png" />
  </Column>
</Columns>

***

<Cards columns={2}>
  <Card title="Prerequisites of using the API" href="https://ng.docs.digitax.tech/reference/prerequisites-of-using-the-api" icon="fa-list" />

  <Card title="DigiTax Nigeria API sections" href="https://ng.docs.digitax.tech/reference/digitax-nigeria-api-sections" icon="fa-bars" />
</Cards>

<Cards columns={1}>
  <Card title="Explore DigiTax Nigeria API endpoints" icon="fa-plug">
    * [/resources]() (References for data required for other endpoints)
    * /[info]()
    * /parties
    * /items
    * /invoices
  </Card>
</Cards>

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

Below are the steps required to get up and running.

## Guaranteed safety and integrity

We comply with industry and security best practices.

> 👍 DigiTax is built with the best industry practices and to the highest security standards