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

| Status    | Meaning                                                                                 | Action                                                                                                                                                    |
| :-------- | :-------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------- |
| pending   | DigiTax Queueing system is **queued** after attempting to reach FIRS E-Invoicing System | Check in later. If you set up [Callback URLs](ref:feature-callback-urls), DigiTax will post to your system when the FIRS E-Invoicing System sync is done. |
| completed | The completed invoice is signed                                                         | Check in later. If you set up [Callback URLs](ref:feature-callback-urls), DigiTax will post to your system when it is done.                               |
| failed    | FIRS E-Invoicing System rejected the transaction                                        | Please initiate another transaction.                                                                                                                      |
