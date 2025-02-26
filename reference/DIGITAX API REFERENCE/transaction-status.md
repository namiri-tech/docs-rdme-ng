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
* Get notifications on transaction statuses via [Callback URLs](doc:call-back-urls)
* Throttling traffic between the businesses throughput and the tax authority's system

  This functionality is possible due to the DigiTax Queueing system.

  <br />

  > 📘 You don't run the risk of double-entry
  >
  > Every transaction that interacts with FIRS E-Invoicing System is first off entered into the DigiTax Queueing system to mitigate against possible FIRS:
  >
  > * intermittency and downtime OR
  > * slow response rate OR

## The different transaction statuses and what they mean

Since transactions are first off entered into the DigiTax Queueing system, we give you the following statuses. This is what they mean.

### Transaction statuses

| Status     | Meaning                                                             | Action                                                                                                                     |
| :--------- | :------------------------------------------------------------------ | :------------------------------------------------------------------------------------------------------------------------- |
| queued     | DigiTax Queueing system is **queued** after trying to reach eTIMS   | Check in later. If you set up [Callback URLs](doc:call-back-urls), we'll post to your system when the eTIMS sync is done.  |
| un\_queued | DigiTax Queueing system is **unqueued** after trying to reach eTIMS | Check in later. If you set up [Callback URLs](doc:call-back-urls) , we'll post to your system when the eTIMS sync is done. |

<br />

<br />

| Status       | Meaning                                                                    | Action                                                                                                                     |
| :----------- | :------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------- |
| queued       | DigiTax Queueing system is **queued** after trying to reach eTIMS          | Check in later. If you set up [Callback URLs](doc:call-back-urls), we'll post to your system when the eTIMS sync is done.  |
| un\_queued   | DigiTax Queueing system is **unqueued** after trying to reach eTIMS        | Check in later. If you set up [Callback URLs](doc:call-back-urls) , we'll post to your system when the eTIMS sync is done. |
| in\_progress | DigiTax Queueing system is **in progress** after attempting to reach eTIMS | Check in later                                                                                                             |
| .            |                                                                            |                                                                                                                            |