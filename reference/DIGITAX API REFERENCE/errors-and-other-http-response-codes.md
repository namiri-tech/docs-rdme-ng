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
Conventional HTTP response codes are used to indicate the success or failure of an API request.

Responses are grouped in five classes:

* Informational responses (100 – 199)
* Successful responses (200 – 299)
* Redirection messages (300 – 399)
* Client error responses (400 – 499)
* Server error responses (500 – 599)

For our interactive API, these are the main HTTP response status codes:

* 200 OK

* 201 Created

* 400 Bad Request

* 401 Unauthorized

* 409 Conflict

* 500 Internal Server Error

* 501 Not Implemented

* 503 Service Unavailable

> 📘 503 is unlikely for DigiTax
>
> We pride ourselves to provide 99.99% uptime!

Head over to the [MDN reference on HTTP Status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) for details on the entire list of HTTP response status codes.
