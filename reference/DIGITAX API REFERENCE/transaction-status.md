---
title: Transaction Status
deprecated: false
hidden: false
metadata:
  robots: index
---
## DigiTax Queueing system

DigiTax provides the following:

* Asynchronous functionality that automatically retries eTIMS
* Get notifications on transaction statuses via [Callback URLs](ref:feature-callback-urls)
* Throttling traffic between the businesses throughput and the tax authority's system

These functionalities are possible due to the DigiTax Queueing system.

> 📘 You don't run the risk of double-entry
>
> Every transaction that interacts with FIRS E-Invoicing System is first off entered into the DigiTax Queueing system to mitigate against possible FIRS:
>
> * intermittency and downtime OR
> * slow response rate

## The different transaction statuses and what they mean

Since transactions are first off entered into the DigiTax Queueing system, we give you the following statuses. This is what they mean.

### Transaction statuses

These are the possible options for the `status` property of a response from the invoices endpoints.

| Status    | Meaning                                                                                 | Action                                                                                                                                                    |
| :-------- | :-------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------- |
| pending   | DigiTax Queueing system is **queued** after attempting to reach FIRS E-Invoicing System | Check in later. If you set up [Callback URLs](ref:feature-callback-urls), DigiTax will post to your system when the FIRS E-Invoicing System sync is done. |
| completed | The completed invoice is signed                                                         | Check in later. If you set up [Callback URLs](ref:feature-callback-urls), DigiTax will post to your system when it is done.                               |
| failed    | FIRS E-Invoicing System rejected the transaction                                        | Please initiate another transaction.                                                                                                                      |

### Invoice Status Details

These are depicted by timestamps both on the DigiTax Nigeria API and Dashboard.

On the API, these are:

* `created_at` property
* `validated_at` property
* `signed_at` property
*  `transmitted_at` property

of a response from the invoices endpoints.

The timestamps above correspond to what you'd see on the Dashboard, under "Invoices" tab, when you click on the arrow icon next to the block under "Invoice Status". These are:

* `Created`
* `Validated`
* `Signed`
* `Transmitted`

<Image align="center" src="https://files.readme.io/485b71a70cbbfb59a9d623c5b7b9d6d811b88fe1a9d0de49890f129c2f9f15a6-CleanShot_2025-09-16_at_15.58.43_22x.png" />
