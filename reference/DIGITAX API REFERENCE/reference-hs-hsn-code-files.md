---
title: 'Reference: HS/ HSN and Service codes - files'
excerpt: >-
  Find here, CSV and JSON files for Harmonized System (HS) or otherwise named
  Harmonized System of Nomenclature (HSN) Code codes
deprecated: false
hidden: false
metadata:
  robots: index
---
## Overview

An HS (Harmonized System) code or HSN (Harmonized System of Nomenclature) code is an internationally standardized numerical code that classifies traded products, used by customs around the world to categorize goods for import and export, developed by the World Customs Organization (WCO).

An HS/HSN code is required when registering an item as a good, while a Service code is required when registering an item as a service. This is applicable in the following endpoints:

* [POST - items endpoint](https://ng.docs.digitax.tech/reference/get_items/)
* [POST - Create invoice with the party and items information](https://ng.docs.digitax.tech/reference/post_detailed-invoices)

## HS/ HSN Code Files

1. The CSV file containing HS codes is accessible <Anchor label="here" target="_blank" href="https://raw.githubusercontent.com/namiri-tech/docs-rdme-ng/refs/heads/v1.0/assets/hs-codes.csv">here</Anchor>.

   You can download the file programmatically. Below is an example using CURL via terminal:

   ```shell
   curl "https://raw.githubusercontent.com/namiri-tech/docs-rdme-ng/refs/heads/v1.0/assets/hs-codes.csv" > hs-codes.csv
   ```
2. The JSON file containing HS codes is accessible <Anchor label="here" target="_blank" href="https://raw.githubusercontent.com/namiri-tech/docs-rdme-ng/refs/heads/v1.0/assets/hs-codes.json">here</Anchor>.

   You can download the file programmatically. Below is an example using CURL via terminal:

   ```shell
   curl "https://raw.githubusercontent.com/namiri-tech/docs-rdme-ng/refs/heads/v1.0/assets/hs-codes.json" > hs-codes.json
   ```

## Service Code Files

1. The CSV file containing Service codes is accessible <Anchor label="here" target="_blank" href="https://raw.githubusercontent.com/namiri-tech/docs-rdme-ng/refs/heads/v1.0/assets/hs-codes.csv">here</Anchor>.

   You can download the file programmatically. Below is an example using CURL via terminal:

   ```shell
   curl "https://raw.githubusercontent.com/namiri-tech/docs-rdme-ng/refs/heads/v1.0/assets/service-codes.csv" > service-codes.csv
   ```
2. The JSON file containing Service codes is accessible <Anchor label="here" target="_blank" href="https://raw.githubusercontent.com/namiri-tech/docs-rdme-ng/refs/heads/v1.0/assets/hs-codes.json">here</Anchor>.

   You can download the file programmatically. Below is an example using CURL via terminal:

   ```shell
   curl "https://raw.githubusercontent.com/namiri-tech/docs-rdme-ng/refs/heads/v1.0/assets/service-codes.json" > service-codes.json
   ```

<br />
