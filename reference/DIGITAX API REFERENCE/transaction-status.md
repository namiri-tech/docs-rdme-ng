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

<Table align={["left","left","left"]}>
  <thead>
    <tr>
      <th>
        Status
      </th>

      <th>
        Meaning
      </th>

      <th>
        Action
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        pending
      </td>

      <td>
        DigiTax Queueing system is **queued** after attempting to reach FIRS E-Invoicing System
      </td>

      <td>
        Check in later. If you set up [Callback URLs](ref:feature-callback-urls), DigiTax will post to your system when the FIRS E-Invoicing System sync is done.
      </td>
    </tr>

    <tr>
      <td>
        in\_progress
      </td>

      <td>
        DigiTax Queueing system is **in progress** when DigiTax has reached FIRS E-Invoicing System
      </td>

      <td>
        Check in later. If you set up [Callback URLs](ref:feature-callback-urls), DigiTax will post to your system when the FIRS E-Invoicing System sync is done.
      </td>
    </tr>

    <tr>
      <td>
        confirmed
      </td>

      <td>
        DigiTax Queueing system is **confirmed** when FIRS E-Invoicing System has received and accepted the transaction, and we have the final data
      </td>

      <td>
        For ITEM: You can now create a sale with this item\\
        For INVOICE: You have the `qr_code_data` hence can generate the QR code.
      </td>
    </tr>

    <tr>
      <td>
        failed
      </td>

      <td>
        FIRS E-Invoicing System rejected the transaction
      </td>

      <td>
        Please initiate another transaction.
      </td>
    </tr>

    <tr>
      <td>
        completed
      </td>

      <td>
        The confirmed invoice is transmitted to the receiving party
      </td>

      <td>
        Check in later. If you set up [Callback URLs](ref:feature-callback-urls), DigiTax will post to your system when it is done.
      </td>
    </tr>
  </tbody>
</Table>