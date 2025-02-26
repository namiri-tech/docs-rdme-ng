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
  > 📘 You don't run the risk of double-entry> Every transaction that interacts with eTIMS is first off entered into the DigiTax Queueing system to **mitigate against possible eTIMS intermittency and downtime** or slow response rate.
  >
  >
  <br />

## The different transaction statuses and what they mean

Since transactions are first off entered into the DigiTax Queueing system, we give you the following statuses. This is what they mean.

### Transaction statuses

\[block:parameters] &#x20;
\{
&#x20; "data\[: \{
&#x20;   "h-0"]\(doc:call-back-urls) \[: \{
&#x20;   "h-0"]\(doc:call-back-urls) \[: \{
&#x20;   "h-0"]\(doc:call-back-urls) : "Meaning",
&#x20;   "h-2": "Action",
&#x20;   "0-0": "queued",
&#x20;   "0-1": "DigiTax Queueing system is \*\*queued\*\* after trying to reach eTIMS",
&#x20;   "0-2": "Check in later. If you set up \[Callback URLs]\(doc:call-back-urls), we'll post to your system when the eTIMS sync is done.",
&#x20;   "1-0": "un\_queued",
&#x20;   "1-1": "DigiTax Queueing system is \*\*unqueued\*\* after trying to reach eTIMS",
&#x20;   "1-2": "Check in later. If you set up \[Callback URLs]\(doc:call-back-urls) , we'll post to your system when the eTIMS sync is done.",
&#x20;   "2-0": "in\_progress",
&#x20;   "2-1": "DigiTax Queueing system is \*\*in progress\*\* after attempting to reach eTIMS",
&#x20;   "2-2": "Check in later",
&#x20;   "3-0": "completed",
&#x20;   "3-1": "eTIMS has received and accepted the transaction, and we have the final data",
&#x20;   "3-2": "For ITEM: You can now create a sale with this item  \nFor SALE: You have the \`etims\_url\` hence can generate the QR code.",
&#x20;   "4-0": "failed",
&#x20;   "4-1": "eTIMS rejected the transaction",
&#x20;   "4-2": "Please initiate another transaction.",
&#x20;   "5-0": "paused",
&#x20;   "5-1": "DigiTax Queueing system is \*\*paused\*\* after trying to reach eTIMS. The queue will be unpaused in the background",
&#x20;   "5-2": "Check in later. If you set up \[Callback URLs]\(doc:call-back-urls), we'll post to your system when the eTIMS sync is done",
&#x20;   "6-0": "submitted",
&#x20;   "6-1": "eTIMS has received and accepted the transaction, however we do not have the final data from their system. Though this is unlikely, we have a workaround to get the data.",
&#x20;   "6-2": "If you don't have an \`etims\_url\` kindly initiate a chat with us when this happens."
&#x20; },
&#x20; "cols": 3,
&#x20; "rows": 7,
&#x20; "align": \[
&#x20;   "left",
&#x20;   "left",
&#x20;   "left"
&#x20; ]
}
\[/block]