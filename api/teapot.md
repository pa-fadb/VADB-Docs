---
layout: default
title: Teapot
parent: API Routes
nav_order: 1
---

# Teapot

GET
{: .label .label-green .float-left .mt-4 }
### `{{ site.targetUrl }}/api/teapot`
{: .mb-4}

This endpoint is primarily used as a test endpoint to see if a [API Client](https://en.wikipedia.org/wiki/Postman_(software)) can connect to the server.
This endpoint serves no purpose otherwise.

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Response

The endpoint will give you a constant [418 error](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/418), more commonly known as the "I'm a teapot" error.

| Field    | Type                                                                  | Description                      |
|:---------|:----------------------------------------------------------------------|:---------------------------------|
| code     | [HTTP Code](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) | The status code of the response. |
| message  | String                                                                | I can't brew you coffee either.  |

### Example response

```json
{
    "code": 418,
    "message": "I'm a teapot! I cannot brew you some coffee."
}
```
