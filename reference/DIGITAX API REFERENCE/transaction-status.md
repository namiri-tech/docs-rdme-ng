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

\[block:parameters]\
\{\
"data\[: \{
"h-0"]\(doc:call-back-urls) \[: \{
"h-0"]\(doc:call-back-urls) \[: \{
"h-0"]\(doc:call-back-urls) : "Meaning",
"h-2": "Action",
"0-0": "queued",
"0-1": "DigiTax Queueing system is \*\*queued\*\* after trying to reach eTIMS",
"0-2": "Check in later. If you set up \[Callback URLs]\(doc:call-back-urls), we'll post to your system when the eTIMS sync is done.",
"1-0": "un\_queued",
"1-1": "DigiTax Queueing system is \*\*unqueued\*\* after trying to reach eTIMS",
"1-2": "Check in later. If you set up \[Callback URLs]\(doc:call-back-urls) , we'll post to your system when the eTIMS sync is done.",
"2-0": "in\_progress",
"2-1": "DigiTax Queueing system is \*\*in progress\*\* after attempting to reach eTIMS",
"2-2": "Check in later",
"3-0": "completed",
"3-1": "eTIMS has received and accepted the transaction, and we have the final data",
"3-2": "For ITEM: You can now create a sale with this item  \nFor SALE: You have the \`etims\_url\` hence can generate the QR code.",
"4-0": "failed",
"4-1": "eTIMS rejected the transaction",
"4-2": "Please initiate another transaction.",
"5-0": "paused",
"5-1": "DigiTax Queueing system is \*\*paused\*\* after trying to reach eTIMS. The queue will be unpaused in the background",
"5-2": "Check in later. If you set up \[Callback URLs]\(doc:call-back-urls), we'll post to your system when the eTIMS sync is done",
"6-0": "submitted",
"6-1": "eTIMS has received and accepted the transaction, however we do not have the final data from their system. Though this is unlikely, we have a workaround to get the data.",
"6-2": "If you don't have an \`etims\_url\` kindly initiate a chat with us when this happens."
},
"cols": 3,
"rows": 7,
"align": \[
"left",
"left",
"left"
]
}
\[/block]