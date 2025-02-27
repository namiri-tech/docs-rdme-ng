---
title: How to use this site
excerpt: If you're new to here, learn how to navigate these DigiTax API Hub pages below
deprecated: false
hidden: false
metadata:
  robots: index
---
## 📖 Guides

This is the overview page of the Guides section.

Explore the guides as outlined on the left-hand menu.

### Guide page features

* **Table of contents** on the right-hand side (Only on Desktop)
* **Hover to view Glossary definitions (mouseover)**: We don't want to get lost in the jargon. Words (acronyms) listed in the Glossary appear on a page as underlined with a dotted line.

  Like <Glossary>API</Glossary>, hover (or click - *On Mobile*) to view the definition.

## 🚦 Interactive API Docs

For a great developer experience, the endpoints in the [DigiTax Nigeria API reference](/reference) are interactive.

Once you're set up in the DigiTax Dashboard, you can generate a sandbox or LIVE **X-API-Key** for authorization. Read more on the [API prerequisites](ref:prerequisites-of-using-the-api)  and how to [Get Enabled for FIRS E-Invoicing with DigiTax](doc:get-enabled-for-firs-e-invoicing-with-digitax).

Explore the API endpoints [here](/reference).

### Code samples

You can make use of up to 19 programming language code samples for requests to get you started, regardless of the language you're using.

<Image align="center" width="360px" src="https://files.readme.io/18fab9d0ba74fe79ca356fbda311e278e6b92caa26dab89ba40e56e52d985db2-CleanShot_2025-02-27_at_12.19.552x.png" />

### Pagination

We support **cursor-based pagination requests** for endpoints whose **GET** requests return a list of objects.

#### Parameters for paginated requests

The following are optional query parameters for paginated requests like [GET FIRS Invoices](ref:get_invoices).

| Parameter  | Explanation                                                              |
| :--------- | :----------------------------------------------------------------------- |
| before     | When paginating results, a pointer to an ID before which we want results |
| after      | When paginating results, a pointer to an ID after which we want results  |
| page\_size | The maximum number of items to return per page, defaults to 20           |

These are also explained on the API endpoint page(s).

### Requests

<Image align="center" width="360px" src="https://files.readme.io/17102ca17357bbe74dc763eec7c4288fd9dcd8e09e8b7173339166f7b69305da-CleanShot_2025-02-27_at_12.31.522x.png" />

### Parameters

Parameters (or Params) come in two types in the DigiTax API - Query Params and Body Params. Below are examples:

* Query Params

  An example is seen in [GET FIRS Invoices](ref:get_invoices)

<Image align="center" width="360px" src="https://files.readme.io/d10de438c8359cc9dd67cfc7b87340a4e6a84abe03aadd17b7b2196be4ea5041-CleanShot_2025-02-27_at_12.49.29_22x.png" />

* Body Params

  An example is seen in [CREATE Party](ref:post_parties)

  <Image align="center" width="360px" src="https://files.readme.io/cba45b39e32c9188f6331b5dffe3a86ab1950936b7c0a5407181d3406aa8aa5f-CleanShot_2025-02-27_at_12.55.032x.png" />

## 💬 We're here to help

If you get stuck, [email us](mailto:info@namiri.tech)  or use the **DigiTax chat** on the bottom right of any page.

We're excited you're here! 💚