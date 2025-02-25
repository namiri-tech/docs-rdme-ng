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

Below are the steps required to get up and running.

## Prerequisites of using the API

The following are the steps to getting a sandbox business (for testing before you go LIVE)

1. [Sign up on DigiTax](https://digitax.tech)
2. Create a profile.
3. Create a sandbox business.
4. Generate an API Key under "Integrations" tab. See screenshots below:

Navigate to the "Integrations" menu.\
Then select "Add API KEY"

\[block:image]\
\{\
"images": \[
\{
"image": \[
"[https://files.readme.io/f129eaf-Screenshot\_2024-08-17\_at\_12.11.35.png](https://files.readme.io/f129eaf-Screenshot_2024-08-17_at_12.11.35.png)",
"",
""
],
"align": "center"
}
]
}
\[/block]

Enter a name and select "API key" OR "License key"

\[block:image]\
\{\
"images": \[
\{
"image": \[
"[https://files.readme.io/5b8acb6-Api\_Key.png](https://files.readme.io/5b8acb6-Api_Key.png)",
"",
""
],
"align": "center",
"sizing": "350px",
"border": true
}
]
}
\[/block]

\[block:image]\
\{
"images": \[
\{
"image": \[
"[https://files.readme.io/56c4160-License\_Key.png](https://files.readme.io/56c4160-License_Key.png)",
"",
""
],
"align": "center",
"sizing": "350px",
"border": true
}
]
}
\[/block]

Please record the value that you generate for later use, as you will not see it from the dashboard on subsequent visits. Save it securely.

Use the **X-API-Key** in your header when making API calls through the interactive API docs [here](/reference) OR via your integration during testing.

## Guaranteed safety and integrity

We comply with industry and security best practices.

> 👍 DigiTax is built with the best industry practices and to the highest security standards