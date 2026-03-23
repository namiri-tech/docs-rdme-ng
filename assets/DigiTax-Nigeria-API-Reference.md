**Table of Contents**

- [DigiTax Nigeria API](#digitax-nigeria-api)
  - [Introduction](#introduction)
  - [DigiTax API](#digitax-api)
    - [DigiTax API Features](#digitax-api-features)
    - [Using DigiTax API](#using-digitax-api)
    - [API endpoint parameters](#api-endpoint-parameters)
  - [Guaranteed safety and integrity](#guaranteed-safety-and-integrity)
- [Prerequisites of using the API](#prerequisites-of-using-the-api)
  - [Generate an API Key](#generate-an-api-key)
    - [License Key](#license-key)
- [Feature: Callback URLs](#feature-callback-urls)
  - [Understanding Callback URLs](#understanding-callback-urls)
  - [Where to use Callback URLs](#where-to-use-callback-urls)
  - [Scenarios](#scenarios)
  - [Structure and example](#structure-and-example)
- [Transaction Status](#transaction-status)
  - [DigiTax Queueing system](#digitax-queueing-system)
  - [The different transaction statuses and what they mean](#the-different-transaction-statuses-and-what-they-mean)
    - [Transaction statuses](#transaction-statuses)
    - [Invoice Status Details](#invoice-status-details)
  - [Successful transmission requirements](#successful-transmission-requirements)
    - [Party details for transmission](#party-details-for-transmission)
- [Errors and other HTTP response codes](#errors-and-other-http-response-codes)
  - [Overview](#overview)
  - [DigiTax API HTTP response status codes](#digitax-api-http-response-status-codes)
  - [Further context and Possible action points](#further-context-and-possible-action-points)
    - [Successful responses](#successful-responses)
    - [Client error responses](#client-error-responses)
- [Reference: HS/ HSN and Service codes - files](#reference-hs-hsn-and-service-codes---files)
  - [Overview](#overview-1)
  - [HS/ HSN Code Files](#hs-hsn-code-files)
  - [Service Code Files](#service-code-files)
- [Feature: Detailed Sales](#feature-detailed-sales)
  - [Overview](#overview-2)
    - [Party Details](#party-details)
    - [Tax Calculation](#tax-calculation)
    - [Endpoint](#endpoint)
    - [Payload](#payload)
    - [Response](#response)
    - [Credit and Debit Notes Support](#credit-and-debit-notes-support)
    - [Sample Debit Note Request](#sample-debit-note-request)
- [API endpoints](#api-endpoints)
  - [Resources API endpoints](#resources-api-endpoints)
  - [Business API endpoints](#business-api-endpoints)
  - [Parties API endpoints](#parties-api-endpoints)
  - [Items API endpoints](#items-api-endpoints)
  - [Invoices API endpoints](#invoices-api-endpoints)
  - [Invoices Downloads API endpoints](#invoices-downloads-api-endpoints)
  - [APP Invoices API endpoints](#app-invoices-api-endpoints)

# DigiTax Nigeria API

[Link to Online documentation](https://ng.docs.digitax.tech/reference/using-the-digitax-nigeria-api)

## Introduction

Before you proceed, we encourage you to get an overview of [DigiTax Nigeria and NRS e-Invoicing](https://ng.docs.digitax.tech/docs/getting-started) and [NRS and NRS E-Invoicing System](https://ng.docs.digitax.tech/docs/firs-e-invoicing-system).

> Use **DigiTax Nigeria API** to integrate your system with NRS E-Invoicing System for automation and to reduce platform-hopping

![](https://files.readme.io/962057ae5fb5cf6fd78c5c3a7a5065cc2b42d10a24798169d1ab2852a3b7fffa-DigiTax-TaxAuthoritiesRegulators.png)

## DigiTax API

Namiri Technologies, through our DigiTax Platform, have developed a suite of solutions:

- DigiTax App (Compatible with Android POS),
- DigiTax Dashboard (Web Browser-based Desktop application)
- DigiTax API

> The first two are powered by the DigiTax API 🎉

### DigiTax API Features

The DigiTax API is built with various industry standards for API platforms in mind. These include:

- RESTful API
- OpenAPI (formerly Swagger): An open-source standard that allows a standardized way to generate, document, and test our APIs.
- Secure authentication with cryptographically signed JWTs (JSON Web Tokens)
- [Standard HTTP response codes](#errors-and-other-http-response-codes) for errors and successful requests

### Using DigiTax API

To use this API, you'll need access to DigiTax Dashboard environment to get an API Key. You can test our solutions (DigiTax Dashboard, DigiTax App and DigiTax API) for free using test businesses.

These are the steps required to get up and running on the API - [Prerequisites of using DigiTax API](#prerequisites-of-using-the-api)

> ℹ️ You can test our solutions before committing.
>
> For commercial conversations, get in touch with our team

### API endpoint parameters

For some API endpoints like [**Create item**](#items-api-endpoints), body parameters (also called query parameters) are passed along with the GET, POST, PUT and DELETE requests.

The responses contain attributes related to the passed-in query parameters, which unveil the data model used in the application.

## Guaranteed safety and integrity

We comply with industry and security best practices.

> 👍 DigiTax is built with the best industry practices and to the highest security standards

# Prerequisites of using the API

[Link to Online documentation](https://ng.docs.digitax.tech/reference/prerequisites-of-using-the-api)

> 📘 You can test the DigiTax API before reaching out to us
>
> We've designed the developer experience to be Hands-off. Meaning you can get started with your first API call without engaging with our team. Should you need our support or want to onboard your business to LIVE, reach out to us.

The following are the steps to creating a sandbox business and getting an X-API-Key (for testing before you go LIVE):

1. [Sign up on DigiTax](https://digitax.tech/)
2. Create a profile.
3. Create a sandbox business.
4. Generate an API Key under the "Integrations" tab. See screenshots below.
5. Use the copied API Key as **X-API-Key** in your header when making API calls through the interactive online API docs [here](https://ng.docs.digitax.tech/reference/get_resources-countries) OR via your integration during testing.

See screenshots below.

## Generate an API Key

In a Sandbox/ LIVE business,

1. Navigate to the "Integrations" menu tab
2. Select "Add API KEY"
	![](https://files.readme.io/a99655fef3da77da85c1f6be4f877e63988e7f34d24d20790ab5f5faa162cd39-AddAPIKey.png)

3. Enter a name and select "Api key"
	![](https://files.readme.io/ecbb1763470858903d07c168a2fc17bc3477999ac27af026ccbc51dd81d74cf6-Api_Key.png)

	Please record the value that you generate for later use, as you will not see it from the dashboard on subsequent visits. Save it securely.

### License Key

In step 3 above, under **API Type**, we have two options:

- Api Key
- License Key

	![](https://files.readme.io/e528f94e1cf702f97ee9fa40649c47a899a556586237c48cb016c5e8e672bfe3-License_Key.png)

The **License Key** is used in some DigiTax Plugins.

# Feature: Callback URLs

[Link to Online documentation](https://ng.docs.digitax.tech/reference/feature-callback-urls)

## Understanding Callback URLs

When you make a request to DigiTax API, we immediately return a response. The status of that transaction by default is `DRAFT`.

_Below is a snippet of the response to a POST invoice request. The status property reads "DRAFT"._

![](https://files.readme.io/a6e9db30b2930a71ed72df2de6cb9f65fc4f2981c619208035e43005591cce35-CleanShot_2025-08-05_at_15.41.22_22x.png)

We save it into our queuing system to be **signed**. This step changes the status property from `DRAFT` to `COMPLETED`. This is apparent via the DigiTax Dashboard or when you make a **GET** request.

_Below is a snippet of the response of a GET invoice request. The status property reads "COMPLETED"._

![](https://files.readme.io/2f38cdc542d8670232c027c758f7263d47d41c330337d25e98f10701112ad275-CleanShot_2025-08-05_at_15.41.412x.png)

_Below is the invoice above as viewed on the dashboard_

![](https://files.readme.io/59c30d5bd519109170d2c465091f48d5fbba9c3e8cb501a6807a68782d27f96a-CleanShot_2025-08-05_at_15.29.112x.png)

The tax authority's system or DigiTax may take some time to sign an invoice, and it is not efficient to have you, as the API caller or consumer, wait for a response.

> Callback URLs are useful since they inform you as soon as a particular event like a status change happens after data processing on the tax authority's system or DigiTax.

## Where to use Callback URLs

We accept an optional `callback_url` property for the following endpoints:

- [Add invoice](#invoices-api-endpoints) (**POST**)
- Add credit note (**POST**)
- Add debit note (**POST**)

More details under [Scenarios](#scenarios) section below.

During testing, we encourage you to use a site like [webhook.site](https://webhook.site/)

Our system will POST data to the callback URL when we have new information about the invoice, usually after syncing with the tax authority's system.

## Scenarios

We send a callback when invoice has been signed.

When an invoice, credit note, or debit note has been synced to NRS (or signed), we also send a POST request to the `callback_url`. The request body contains a `data` object with details about the synced invoice, credit note, or debit note and an `event` property with the value `sale.sync`.

## Structure and example

Example response when an invoice, credit note, or debit note has been synced to NRS (or has been signed)

```json
{
  "data": {
    "id": "invoice_01K1X2Z26VPAVPTMTA3CGTWCQ8",
    "original_invoice_id": null,
    "created_at": "2025-08-05T12:23:12.351Z",
    "updated_at": "2025-08-05T12:23:13.181Z",
    "active": true,
    "party_id": "party_01K1SMHY16R73ZZA7QYR6R44Y5",
    "invoice_date": "2025-08-05",
    "issue_date": "2025-08-05",
    "is_valid": true,
    "transmitted_at": null,
    "signed_at": "2025-08-05T12:23:13.181Z",
    "validated_at": "2025-08-05T12:23:12.785Z",
    "invoice_type_code": "381",
    "tax_point_date": null,
    "document_currency_code": "NGN",
    "tax_currency_code": "NGN",
    "invoice_number": "INV25-217-122312346-Q42FME",
    "invoice_reference_number": "122312346Q42FME-E3A89069-20250805",
    "buyer_reference": null,
    "payment_status": "PENDING",
    "delivery_date": null,
    "status": "COMPLETED",
    "line_extension_amount": 100,
    "tax_exclusive_amount": 97,
    "tax_inclusive_amount": 104.28,
    "payable_amount": 104.28,
    "tax_amount": 7.28,
    "billing_reference": null,
    "dispatch_document_reference": null,
    "receipt_document_reference": null,
    "originator_document_reference": null,
    "contract_document_reference": null,
    "due_date": null,
    "notes": "Sample invoice notes",
    "qr_code_data": "VoOXpj/c15gM1jriqcKAsr/5nl8bkm1ZkKRc8s2w23x7ldFVvL4ve8wA+GWHCpd/zmBn8K0lDdHW9MKdawtBY4IoisYvqoGCczzfVP6YNamvgCtav39f3e7VGmsOahcPyrYTs+zM7R+v8lmU/oXTwaf8zvpIsYowpGE4Y3sXv+5WqZ4j361CWViPFPuFzCORkdxU5tjCCxGJ2BqDTOBxBGT4ei21e4Fl2V6pdx9m5Crab63KiYjbOAj7SkWYbih7oL93N/4F/AHYsc4GYNvZyWxdzdx8xLy4igBNpNZ/wsU5rmvAnuPZjFpRECcPriZD7Q302kK+j1GhHx6KbftVig==",
    "taxes": [
      {
        "tax_category_code": "STANDARD_GST",
        "tax_amount": 7.28,
        "taxable_amount": 97,
        "tax_percentage": 7.5
      }
    ],
    "items": [
      {
        "id": "invoiceitem_01K1X2Z26VPAVPTMTA3GH8TX1C",
        "created_at": "2025-08-05T12:23:12.351Z",
        "updated_at": "2025-08-05T12:23:12.351Z",
        "active": true,
        "item_id": "item_01K1SMDHV51XTR7MHT3TFFEYKA",
        "line_extension_amount": 100,
        "quantity": 1,
        "price_amount": 100,
        "discount_rate": 0.05,
        "fee_rate": 0.02,
        "discount_amount": 5,
        "fee_amount": 2,
        "tax_rate": 0.075
      }
    ]
  },
  "event": "invoice.signed"
}
```

# Transaction Status

[Link to Online documentation](https://ng.docs.digitax.tech/reference/transaction-status)

## DigiTax Queueing system

DigiTax provides the following:

- Asynchronous functionality that automatically retries NRS
- Get notifications on transaction statuses via [Callback URLs](#feature-callback-urls)
- Throttling traffic between the businesses throughput and the tax authority's system

These functionalities are possible due to the DigiTax Queueing system.

> 📘 You don't run the risk of double-entry
>
> Every transaction that interacts with NRS E-Invoicing System is first off entered into the DigiTax Queueing system to mitigate against possible NRS:
>
> - intermittency and downtime OR
> - slow response rate

## The different transaction statuses and what they mean

Since transactions are first off entered into the DigiTax Queueing system, we give you the following statuses. This is what they mean.

### Transaction statuses

These are the possible options for the `status` property of a response from the invoices endpoints.

| Status    | Meaning                                                                                 | Action                                                                                                                                                 |
| --------- | --------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| pending   | DigiTax Queueing system is **queued** after attempting to reach NRS E-Invoicing System | Check in later. If you set up [Callback URLs](#feature-callback-urls), DigiTax will post to your system when the NRS E-Invoicing System sync is done. |
| completed | The completed invoice is signed                                                         | Check in later. If you set up [Callback URLs](#feature-callback-urls), DigiTax will post to your system when it is done.                               |
| failed    | NRS E-Invoicing System rejected the transaction                                        | Please initiate another transaction.                                                                                                                   |

### Invoice Status Details

These are depicted by timestamps both on the DigiTax Nigeria API and Dashboard.

On the API, these are:

- `created_at` property
- `validated_at` property
- `signed_at` property
- `transmitted_at` property

of a response from the invoices endpoints.

The timestamps above correspond to what you'd see on the Dashboard, under "Invoices" tab, when you click on the arrow icon next to the block under "Invoice Status". These are:

- `Created`
- `Validated`
- `Signed`
- `Transmitted`

![](https://files.readme.io/485b71a70cbbfb59a9d623c5b7b9d6d811b88fe1a9d0de49890f129c2f9f15a6-CleanShot_2025-09-16_at_15.58.43_22x.png)

## Successful transmission requirements

For an invoice to be marked as transmitted:

1. A party needs to be added
2. The party needs to be onboarded on NRS.

### Party details for transmission

For testing purposes, please use the following properties:

```
Name: Namiri Technology Nigeria Limited
TIN: 08289985-9145
Email: firs-si@namiri.tech
Phone: +2347724935855
Street address: Broad Street
City: Benin City
Postal code: 111111
```

# Errors and other HTTP response codes

[Link to Online documentation](https://ng.docs.digitax.tech/reference/errors-and-other-http-response-codes)

## Overview

Conventional HTTP response codes are used to indicate the success or failure of an API request.

Responses are grouped in five classes:

- Informational responses (100 - 199)
- Successful responses (200 - 299)
- Redirection messages (300 - 399)
- Client error responses (400 - 499)
- Server error responses (500 - 599)

## DigiTax API HTTP response status codes

For our interactive API, these are the main HTTP response status codes (Client error responses and Server error responses included):

- 200 OK

- 201 Created

- 400 Bad Request

- 401 Unauthorized

- 403 Forbidden

- 404 Not Found

- 409 Conflict

- 412 Precondition Failed

- 429 Too Many Requests

- 500 Internal Server Error

- 501 Not Implemented

- 502 Bad Gateway

- 503 Service Unavailable

> 📘 503 is unlikely for DigiTax
>
> We pride ourselves to provide 99.99% uptime!

Head over to the [MDN reference on HTTP Status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) for details on the entire list of HTTP response status codes.

## Further context and Possible action points

### Successful responses

| HTTP response status codes | Scenario in DigiTax API                           | Action                         |
| -------------------------- | ------------------------------------------------- | ------------------------------ |
| 200 OK                     | Typical for successful **GET** endpoint requests  | Use the API response as needed |
| 201 Created                | Typical for successful **POST** endpoint requests | Use the API response as needed |

### Client error responses

| HTTP response status codes   | Scenario in DigiTax API                    | Further context and Possible action points                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ---------------------------- | ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 400 Bad Request              | Typical for POST endpoint requests         | **Action**: Update the request body, headers, and/or parameters and retry                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| 401 Unauthorized             | Typical for POST and GET endpoint requests | For example, if you use a wrong/ deactivated API Key, you get a 401 error with the response body as:  <br>`{"message": "bad credentials"}`<br><br>**Action**: Check API Key or add one if you hadn't already. The message returned will advise otherwise.                                                                                                                                                                                                                                                                                              |
| 403 Forbidden                | Typical for POST endpoint requests         | The user who generated the API Key is not allowed to perform the action or view the resource.                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| 404 Not Found                | Possible in any endpoint                   | **Action**: Update the endpoint path or route                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| 409 Conflict                 | Typical for POST endpoint requests         | For example, `trader_invoice_number` should be unique across all sales/ credit notes and debit notes. If you repeat the value of an existing invoice in a POST request, the request will fail with this error.<br><br>**Action**: Retry with a different, unique `trader_invoice_number`                                                                                                                                                                                                                                                               |
| 412 Precondition Failed      | Typical for POST endpoint requests         | There are several actions that need Preconditions met. The message accompanying the error will advise.<br><br>Below are examples.<br><br>- (For Credit Notes) `credit note can only be created for signed invoices`<br>- `item amount more than amount in original invoice`<br>- (For Invoices) `items sent are more than those found, check that you haven't duplicated an item` - Which means that you have likely duplicated an item in the request.<br>- (For Items) `tax category not found`<br><br>**Action**: Update the request body and retry |
| 429 Too Many Requests        | Possible in any endpoint                   | Since all endpoints are rate-limited, you have reached the set user quota/ rate limit.<br><br>**Action**: Retry later at a slower cadence                                                                                                                                                                                                                                                                                                                                                                                                              |
| 5XX (501, 502, 503, 504 ...) | Possible in any endpoint                   | **Action**:<br><br>- Confirm that our team has issued an advisory on service interruption.<br>    - If so, retry once a resolution of the issue has been communicated.<br>    - If not, please retry. If a retry still returns a 5XX error, kindly reach out to our support team.                                                                                                                                                                                                                                                                      |

# Reference: HS/ HSN and Service codes - files

## Overview

An HS (Harmonized System) code or HSN (Harmonized System of Nomenclature) code is an internationally standardized numerical code that classifies traded products, used by customs around the world to categorize goods for import and export, developed by the World Customs Organization (WCO).

An HS/HSN code is required when registering an item as a good, while a Service code is required when registering an item as a service. This is applicable in the following endpoints:

- [POST - items endpoint](https://ng.docs.digitax.tech/reference/get_items/)
- [POST - Create invoice with the party and items information](https://ng.docs.digitax.tech/reference/post_detailed-invoices)

## HS/ HSN Code Files

1. The CSV file containing HS codes is accessible here.

    You can download the file programmatically. Below is an example using CURL via terminal:

    ```shell
    curl "https://raw.githubusercontent.com/namiri-tech/docs-rdme-ng/refs/heads/v1.0/assets/hs-codes.csv" > hs-codes.csv
    ```

2. The JSON file containing HS codes is accessible here.

    You can download the file programmatically. Below is an example using CURL via terminal:

    ```shell
    curl "https://raw.githubusercontent.com/namiri-tech/docs-rdme-ng/refs/heads/v1.0/assets/hs-codes.json" > hs-codes.json
    ```

## Service Code Files

1. The CSV file containing Service codes is accessible here.

    You can download the file programmatically. Below is an example using CURL via terminal:

    ```shell
    curl "https://raw.githubusercontent.com/namiri-tech/docs-rdme-ng/refs/heads/v1.0/assets/service-codes.csv" > service-codes.csv
    ```

2. The JSON file containing Service codes is accessible here.

    You can download the file programmatically. Below is an example using CURL via terminal:

    ```shell
    curl "https://raw.githubusercontent.com/namiri-tech/docs-rdme-ng/refs/heads/v1.0/assets/service-codes.json" > service-codes.json
    ```

# Feature: Detailed Sales

## Overview

### Party Details

For B2B transactions, the party's TIN, name, and email are mandatory. For B2C transactions, the party details are optional; leave the fields "party_tin","party_name" and "party_email" as empty strings.

### Tax Calculation

Within the item object, users are required to provide pre-calculated values for `total_amount`, `taxable_amount`, and `tax_amount`.

More details on, the `document_currency_code`, `tax_category_code`, `invoice_type_code` etc... can be found under the resource section [here](#resources-api-endpoints).

### Endpoint

```json
https://api.digitax.tech/ng/v1/detailed-invoices
```

### Payload

```json
{
    "party_tin": "08289985-9145", //The Taxpayer Identification Number (TIN) assigned to the buyer
    "party_name": "Namiri Technology", // The registered name of the buyer receiving the invoice. This is the official business or individual name
    "party_email": "nrs-invoices@namiri.tech", // The buyer's official email address used for communication regarding invoices and tax compliance
    "party_address": { // The buyer address is optional in this endpoint
      "street_name": "123 Main St",
      "city_name": "Lagos",
      "postal_zone": "100001",
      "country_code": "NGA"
    },
    "issue_date": "2025-08-15", //The date on which this invoice was issued in the format YYYY-MM-DD
    "invoice_type_code": "381", // A code that specifies the type of invoice being issued
    "tax_point_date": "2025-08-15", //The actual date when the tax becomes applicable in the format YYYY-MM-DD
    "document_currency_code": "NGN", // A code that specifies the default currency in which the invoice is issued
    "buyer_reference": "#INV-005", //A reference number or code provided by the buyer to track the invoice
    "due_date": "2025-08-07", //The date on which this invoice is due in the format YYYY-MM-DD
    "notes": "Sample invoice notes", // Additional invoice information that is not contained explicitly in other structures
    "callback_url": "https://example.com/callback", // The URL to call when we have new information about the invoice, when the invoice is signed successfully or validation has failed
    "items": [
        {
            "item_code": "20107057", //A unique product code assigned to the item in the user's system. It will be used as the unique product identifier
            "tax_category_code": "STANDARD_VAT", // The code for the tax category the item belongs to. It must be one of the tax categories defined in the resources API
            "product_category": "Food and Beverage Products", // The category the product belongs to. You can use the United Nations Standard Products and Services Code (UNSPSC) as a guide
            "item_name": "Digitax Product 001", //The name of the good or service being sold
            "hsn_code": "2847.00", // The Harmonized System of Nomenclature (HSN) Code for the product
            "item_description": "Sample item description", // A brief description of the item
            "quantity": 1, // The total number of items sold in the invoice line
            "unit_price": 10000, // The unit price of this line item before tax
            "discount_rate": 0.05, //The discount rate applied to the item. It must be a value between 0 and 1, where 0 means no discount and 1 means a 100% discount on the price
            "fee_rate": 0.02, //The rate of any additional fees (e.g. service charge, delivery fee). It must be a value between 0 and 1, where 0 means no fee and 1 means a 100% fee on the price
            "tax_rate": 0.075, // The tax rate applied to the item. It must be a value between 0 and 1. For tax category codes that already have a defined tax rate, this value must match the tax category's tax rate
            "taxable_amount": 9700, // The amount on which tax is calculated. It must be equal to the line extension amount (unit price * quantity) plus fees minus discounts. This value will be ignored unless the business has the permission to calculate tax
            "tax_amount": 727.5 // The tax amount for this line item. It must be equal to the taxable amount multiplied by the tax rate. This value will be ignored unless the business has the permission to calculate tax
        }
    ]
}
```

### Response

```json
{
  "id": "invoice_01K2PA6VKQRNK79S8DAKABJBFX",
  "created_at": "2025-08-15T07:30:48Z",
  "updated_at": "2025-08-15T07:30:50Z",
  "active": true,
  "party_id": "party_01JXCF3RQXFYCED9SNX55PQ48Y",
  "invoice_date": "2025-08-07",
  "issue_date": "2025-08-07",
  "is_valid": true,
  "transmitted_at": "2025-08-15T07:30:50Z",
  "signed_at": "2025-08-15T07:30:49Z",
  "validated_at": "2025-08-15T07:30:48Z",
  "invoice_type_code": "381",
  "tax_point_date": "2025-08-07",
  "document_currency_code": "NGN",
  "tax_currency_code": "NGN",
  "invoice_number": "INV25-227-073048567-93G8DF",
  "invoice_reference_number": "07304856793G8DF-E3A89069-20250807",
  "buyer_reference": "#INV-005",
  "payment_status": "PENDING",
  "status": "COMPLETED",
  "line_extension_amount": 10000,
  "tax_exclusive_amount": 9700,
  "tax_inclusive_amount": 10427.5,
  "payable_amount": 10427.5,
  "tax_amount": 727.5,
  "billing_reference": [],
  "notes": "Sample invoice notes",
  "qr_code_data": "h40YWkRDHs7FYojTBvI983xy2da+GyQdmrTc9VmLx4Wvzgt5ETiNp3y7fFzMDJJv9RW2Q6cDvhro6KMW539wPUEW+FyMs1dvbkocZQBDXCdizyYSlnqRZXPZNVGOcBjl8fs53LU5AoCbL4Bcg64UChgtJ0zORtqiu4pzYhQSvidUoC9TZ18cZURWmP1kY20AciKFKofrvJQgOeSX3vGoDo3wT/LTBND/FeprUsF0JlV6PqfasyEcXETQ1j6t8o7H0WqjJw7cE/5H4gUxGXr6Hm+yCP1ErQkvVaAs/8mN1IlYkwxIFaDgoM0j8AOY4YuRKOTk406V6DgWFKMPVL7VzA==",
  "taxes": [
    {
      "tax_category_code": "STANDARD_VAT",
      "tax_amount": 727.5,
      "taxable_amount": 9700,
      "tax_percentage": 7.5
    }
  ],
  "items": [
    {
      "id": "invoiceitem_01K2PA6VKQRNK79S8DAPNH5T9K",
      "created_at": "2025-08-15T07:30:48Z",
      "updated_at": "2025-08-15T07:30:48Z",
      "active": true,
      "item_id": "item_01K2PA6FW77HX3E6HTH3DAEVJC",
      "line_extension_amount": 10000,
      "quantity": 1,
      "unit_price": 10000,
      "discount_rate": 0.05,
      "fee_rate": 0.02,
      "discount_amount": 500,
      "fee_amount": 200,
      "tax_rate": 0.075
    }
  ]
}
```

### Credit and Debit Notes Support

The main difference between detailed credit and debit notes and the original credit and debit notes endpoints is that they use the `item_code` in place of the `item_id` . But the item details and party aren't passed because both were already created when creating the original invoice

Sample Credit Note Request

```
https://api.digitax.tech/ng/v1/credit-notes-with-item-codes
```

```json
{
  "return_date": "2025-08-15",
  "issue_date": "2025-08-15",
  "tax_point_date": "2025-08-15",
  "document_currency_code": "NGN",
  "buyer_reference": "#CN-001",
  "invoice_id": "invoice_01JWR2VH5B3FC4JRXNJDQZCVE6",
  "due_date": "2025-08-15",
  "notes": "Sample credit note notes",
  "callback_url": "https://example.com/callback",
  "items": [
    {
      "item_code": "8000020107057",
      "quantity": 1,
      "unit_price": 10000,
      "discount_rate": 0.05,
      "fee_rate": 0.02,
      "tax_rate": 0.075,
      "taxable_amount": 9700,
      "tax_amount": 727.5
    }
  ]
}
```

### Sample Debit Note Request

```
https://api.digitax.tech/ng/v1/debit-notes-with-item-codes
```

```json
{
  "debit_date": "2025-08-15",
  "issue_date": "2025-08-15",
  "tax_point_date": "2025-08-15",
  "document_currency_code": "NGN",
  "buyer_reference": "#DN-001",
  "invoice_id": "invoice_01JWR2VH5B3FC4JRXNJDQZCVE6",
  "due_date": "2025-08-15",
  "notes": "Sample debit note notes",
  "callback_url": "https://example.com/callback",
  "items": [
    {
      "item_code": "8000020107057",
      "quantity": 1,
      "unit_price": 10000,
      "discount_rate": 0.05,
      "fee_rate": 0.02,
      "tax_rate": 0.075,
      "taxable_amount": 9700,
      "tax_amount": 727.5
    }
  ]
}
```

# API endpoints

DigiTax Nigeria API endpoints are divided into 7 sections listed below. The OpenAPI spec is available for download [here](https://raw.githubusercontent.com/namiri-tech/docs-rdme-ng/refs/heads/v1.0/reference/openapi.yaml).

- [Resources](https://ng.docs.digitax.tech/reference/get_resources-countries)
- [Business](https://ng.docs.digitax.tech/reference/get_info)
- [Parties](https://ng.docs.digitax.tech/reference/get_parties)
- [Items](https://ng.docs.digitax.tech/reference/get_items)
- [Invoices](https://ng.docs.digitax.tech/reference/get_invoices)
- [Invoice Downloads](https://ng.docs.digitax.tech/reference/get_invoice-downloads)
- [APP Invoices](https://ng.docs.digitax.tech/reference/post_app-invoices)

## Resources API endpoints

- [Get NRS Countries](https://ng.docs.digitax.tech/reference/get_resources-countries)
- [Get NRS Currencies](https://ng.docs.digitax.tech/reference/get_resources-currencies)
- [Get NRS Tax Categories](https://ng.docs.digitax.tech/reference/get_resources-tax-categories)
- [Get NRS Invoice Types](https://ng.docs.digitax.tech/reference/get_resources-invoice-types)
- [Get NRS Payment Means](https://ng.docs.digitax.tech/reference/get_resources-payment-means)
- [Get NRS Local Governments](https://ng.docs.digitax.tech/reference/get_resources-local-governments)
- [Get NRS States](https://ng.docs.digitax.tech/reference/get_resources-states)

## Business API endpoints

- [Get NRS Info](https://ng.docs.digitax.tech/reference/get_info)

## Parties API endpoints

- [Get NRS Parties](https://ng.docs.digitax.tech/reference/get_parties)
- [Create Party](https://ng.docs.digitax.tech/reference/post_parties)
- [Get a business party](https://ng.docs.digitax.tech/reference/get_parties-party-id)

## Items API endpoints

- [Get NRS Items](https://ng.docs.digitax.tech/reference/get_items)
- [Create Item](https://ng.docs.digitax.tech/reference/post_items)
- [Get a business item](https://ng.docs.digitax.tech/reference/get_items-item-id)

## Invoices API endpoints

- [Get NRS Invoices](https://ng.docs.digitax.tech/reference/get_invoices)
- [Create Invoice](https://ng.docs.digitax.tech/reference/post_invoices)
- [Get NRS Credit Notes](https://ng.docs.digitax.tech/reference/get_credit-notes)
- [Create Credit Note](https://ng.docs.digitax.tech/reference/post_credit-notes)
- [Get NRS Debit Notes](https://ng.docs.digitax.tech/reference/get_debit-notes)
- [Create Debit Note](https://ng.docs.digitax.tech/reference/post_debit-notes)
- [Get a business invoice](https://ng.docs.digitax.tech/reference/get_invoices-invoice-id)
- [Update an invoice payment status](https://ng.docs.digitax.tech/reference/put_invoices-invoice-id-payment-status)
- [Get a business invoice by the invoice reference number](https://ng.docs.digitax.tech/reference/get_invoices-irn-invoice-reference-number)
- [Create invoice with the party and items information](https://ng.docs.digitax.tech/reference/post_detailed-invoices)
- [Create credit note with the item code in place of the item ID](https://ng.docs.digitax.tech/reference/post_credit-notes-with-item-codes)
- [Create debit note with the item code in place of the item ID](https://ng.docs.digitax.tech/reference/post_debit-notes-with-item-codes)

## Invoices Downloads API endpoints

- [Get NRS Invoice Downloads](https://ng.docs.digitax.tech/reference/get_invoice-downloads)
- [Get a NRS Invoice Download](https://ng.docs.digitax.tech/reference/get_invoice-downloads-download-id)
- [Get a business invoice download by the invoice reference number](https://ng.docs.digitax.tech/reference/get_invoice-downloads-irn-invoice-reference-number)
- [Confirm a business invoice download's payment status](https://ng.docs.digitax.tech/reference/get_invoice-downloads-download-id-confirm)

## APP Invoices API endpoints

- [Create Invoice by users who are using DigiTax as their Access Point Provider(APP) only](https://ng.docs.digitax.tech/reference/post_app-invoices)
- [Get APP Invoices](https://ng.docs.digitax.tech/reference/get_app-invoices)
- [Get an APP invoice](https://ng.docs.digitax.tech/reference/get_app-invoices-app-invoice-id)
- [Update an APP invoice payment status](https://ng.docs.digitax.tech/reference/put_app-invoices-app-invoice-id-payment-status)
