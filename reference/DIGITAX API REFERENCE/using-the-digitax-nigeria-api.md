---
title: DigiTax Nigeria API Introduction
excerpt: An overview of the DigiTax Nigeria API
deprecated: false
hidden: false
metadata:
  robots: index
---
## Introduction

Before you proceed, we encourage you to get an overview of [DigiTax Nigeria and FIRS e-Invoicing](doc:getting-started) and [FIRS and FIRS E-Invoicing System](doc:firs-e-invoicing-system).

> Use **DigiTax Nigeria API** to integrate your system with FIRS E-Invoicing System for automation and to reduce platform-hopping

<Image className="border" border={true} src="https://files.readme.io/962057ae5fb5cf6fd78c5c3a7a5065cc2b42d10a24798169d1ab2852a3b7fffa-DigiTax-TaxAuthoritiesRegulators.png" />

***

<Cards columns={1}>
  <Card title="Prerequisites of using the API" href="https://ng.docs.digitax.tech/reference/prerequisites-of-using-the-api" icon="fa-list" />
</Cards>

<Cards columns={1}>
  <Card title="Explore resources DigiTax Nigeria API endpoints" icon="fa-book">
    Consider endpoints under **resources** as references for data required for other endpoints.
  </Card>

  <Card title="Explore core DigiTax Nigeria API endpoints" icon="fa-plug">
    * [/info](https://ng.docs.digitax.tech/reference/get_info)
    * [/parties](https://ng.docs.digitax.tech/reference/get_parties)
    * [/items](https://ng.docs.digitax.tech/reference/get_items)
    * [/invoices](https://ng.docs.digitax.tech/reference/get_invoices)
    * [/invoice-downloads](https://ng.docs.digitax.tech/reference/get_invoice-downloads)
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
* [Standard HTTP response codes](ref:errors-and-other-http-response-codes) for errors and successful requests

### Using DigiTax API

To use this API, you'll need access to DigiTax Dashboard environment to get an API Key. You can test our solutions (DigiTax Dashboard, DigiTax App and DigiTax API) for free using test businesses.

These are the steps required to get up and running on the API - [Prerequisites of using DigiTax API](https://ng.docs.digitax.tech/update/reference/prerequisites-of-using-the-api)

> ℹ️ You can test our solutions before committing
>
> For commercial conversations, get in touch with <Anchor label="our team" target="_blank" href="mailto:support@namiri.tech">our team</Anchor>

### API endpoint parameters

For some API endpoints like [**Create item**](ref:post_items), body parameters (also called query parameters) are passed along with the GET, POST, PUT and DELETE requests.

{/* TODO: Add item/ invoice attributes and link them here */}

The responses contain attributes related to the passed-in query parameters, which unveil the data model used in the application.

## Guaranteed safety and integrity

We comply with industry and security best practices.

> 👍 DigiTax is built with the best industry practices and to the highest security standards