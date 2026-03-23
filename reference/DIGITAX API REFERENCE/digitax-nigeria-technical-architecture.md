---
title: DigiTax Nigeria technical architecture reference
deprecated: false
hidden: true
icon: fad fa-user-ninja
metadata:
  robots: index
---
## DigiTax suite of Products

Namiri Technologies, through our DigiTax Platform, have developed a suite of solutions:

* DigiTax App (Compatible with Android POS),
* DigiTax Dashboard (Web Browser-based Desktop application)
* DigiTax API

Below are diagrams for your attention regarding the infrastructure supporting DigiTax

## High-level data flow

An invoice is created by the taxpayer is saved on DigiTax while being transmitted to the Tax regulator (NRS)

<Image align="center" className="border" border={true} src="https://files.readme.io/bf59304d89ebc9058a45afcd0961893e9249438be1e2e38568598ae73454c51d-image.png" />

## High-level technical architecture

1. Requests from system clients (like DigiTax Dashboard, DigiTax APP and external APIs) are received by DigiTax API
2. Such a request goes through Cloudflare (which mitigates against DDoS - Distributed Denial of Service attacks)
3. The request then moves through our API gateway - a centralized entry point and reverse proxy for managing interactions between clients and microservices. *Request Authentication is also done at this layer.*
4. The request is then received by our Kubernetes cluster for validation\* and compute.
5. The request data is then saved and thus available for retrieval by system clients.

*Validation does not just happen in the Kubernetes cluster. Different validation happens at different layers of the infrastructure.*

Review the diagram below.

<Image align="center" className="border" border={true} src="https://files.readme.io/6b446b991fac8fbc80bcb20c4c4ac95e9134bc9c39b73d8a16e63627d253482e-DigiTax_Architecture_Diagram.drawio_1.png" />