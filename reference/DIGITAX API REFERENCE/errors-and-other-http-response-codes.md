---
title: Errors and other HTTP response codes
excerpt: >-
  HTTP response codes for troubleshooting: declines, invalid data, network
  problems, and more.
deprecated: false
hidden: false
metadata:
  robots: index
---
## Overview

Conventional HTTP response codes are used to indicate the success or failure of an API request.

Responses are grouped in five classes:

* Informational responses (100 – 199)
* Successful responses (200 – 299)
* Redirection messages (300 – 399)
* Client error responses (400 – 499)
* Server error responses (500 – 599)

## DigiTax API HTTP response status codes

For our interactive API, these are the main HTTP response status codes (Client error responses and Server error responses included):

* 200 OK

* 201 Created

* 400 Bad Request

* 401 Unauthorized

* 403 Forbidden

* 404 Not Found

* 409 Conflict

* 412 Precondition Failed

* 429 Too Many Requests

* 500 Internal Server Error

* 501 Not Implemented

* 502 Bad Gateway

* 503 Service Unavailable

> 📘 503 is unlikely for DigiTax
>
> We pride ourselves to provide 99.99% uptime!

Head over to the [MDN reference on HTTP Status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) for details on the entire list of HTTP response status codes.

## Further context and Possible action points

### Successful responses

| HTTP response status codes | Scenario in DigiTax API                           | Action                         |
| :------------------------- | :------------------------------------------------ | :----------------------------- |
| 200 OK                     | Typical for successful **GET** endpoint requests  | Use the API response as needed |
| 201 Created                | Typical for successful **POST** endpoint requests | Use the API response as needed |

### Client error responses

<Table align={["left","left","left"]}>
  <thead>
    <tr>
      <th>
        HTTP response status codes
      </th>

      <th>
        Scenario in DigiTax API
      </th>

      <th>
        Further context and Possible action points
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        400 Bad Request
      </td>

      <td>
        Typical for POST endpoint requests
      </td>

      <td>
        **Action**: Update the request body, headers, and/or parameters and retry
      </td>
    </tr>

    <tr>
      <td>
        401 Unauthorized
      </td>

      <td>
        Typical for POST and GET endpoint requests
      </td>

      <td>
          
        For example, if you use a wrong/ deactivated API Key, you get a 401 error with the response body as:  
        `{"message": "bad credentials"}`   

        **Action**: Check API Key or add one if you hadn't already. The message returned will advise otherwise.
      </td>
    </tr>

    <tr>
      <td>
        403 Forbidden
      </td>

      <td>
        Typical for POST endpoint requests
      </td>

      <td>
        The user who generated the API Key is not allowed to perform the action or view the resource.
      </td>
    </tr>

    <tr>
      <td>
        404 Not Found
      </td>

      <td>
        Possible in any endpoint
      </td>

      <td>
        **Action**: Update the endpoint path or route
      </td>
    </tr>

    <tr>
      <td>
        409 Conflict
      </td>

      <td>
        Typical for POST endpoint requests
      </td>

      <td>
        For example, `trader_invoice_number` should be unique across all sales/ credit notes and debit notes. If you repeat the value of an existing invoice in a POST request, the request will fail with this error.  

        **Action**: Retry with a different, unique `trader_invoice_number`
      </td>
    </tr>

    <tr>
      <td>
        412 Precondition Failed
      </td>

      <td>
        Typical for POST endpoint requests
      </td>

      <td>
        There are several actions that need Preconditions met. The message accompanying the error will advise.  

        Below are examples.

        * (For Credit Notes) `credit note can only be created for signed invoices`
        * `item amount more than amount in original invoice`
        * (For Invoices) `items sent are more than those found, check that you haven't duplicated an item` - Which means that you have likely duplicated an item in the request.  
        * (For Items) `tax category not found`

        **Action**: Update the request body and retry
      </td>
    </tr>

    <tr>
      <td>
        429 Too Many Requests
      </td>

      <td>
        Possible in any endpoint
      </td>

      <td>
        Since all endpoints are rate-limited, you have reached the set user quota/ rate limit.

        **Action**: Retry later at a slower cadence
      </td>
    </tr>

    <tr>
      <td>
        5XX (501, 502, 503, 504 ...)
      </td>

      <td>
        Possible in any endpoint
      </td>

      <td>
        **Action**:  

        * Confirm that our team has issued an advisory on service interruption.
          * If so, retry once a resolution of the issue has been communicated.
          * If not, please retry. If a retry still returns a 5XX error, kindly reach out to our support team.
      </td>
    </tr>
  </tbody>
</Table>

<br />
