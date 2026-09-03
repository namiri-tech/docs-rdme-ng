---
title: API ChangeLog - October 22nd 2025
author: Namiri Tech
hidden: false
published_at: '2025-10-22T15:06:55.721Z'
---
**Improved:&#x20;**`local government` and `state` added to FIRS party address

<br />

## Added support for local government and state to FIRS party address

- There are 2 new resource endpoints to fetch the accepted values for this:`[https://api.digitax.tech/ng/v1/resources/local-governments]`  and `[https://api.digitax.tech/ng/v1/resources/states]`
- `local_government `and `state` have been added to the party address object. They will be required fields when creating a party in the` /parties` endpoint and in the `/detailed-invoices` endpoint. For the detailed invoices' endpoint, in cases where the address is not given, we have a default address, and it includes the local government and state

<br />