---
layout: default
title: Search
parent: API Routes
nav_order: 2
---

# Search

GET
{: .label .label-green .float-left .mt-4 }
### `{{ site.targetUrl }}/api/search/` `:query`
{: .mb-4}

<br>

This endpoint will search for [artists](/definitions/artist#artist) matching the search query and return a list of matching [artists](/definitions/artist#artist).
If the query is `*`, it will return all [artists](/definitions/artist#artist).
Below is a list of parameters that can be used in the query.

| Field    | Type                | Description                                                    |
|:---------|:--------------------|:---------------------------------------------------------------|
| sort     | [Sorting](#sorting) | The search term to find [artists](/definitions/artist#artist). |

### Sorting
{: .d-inline-block }
Enum
{: .label .label-blue .mt-2 }

This enum is used to sort the results of the search. The default sorting is `Recent`.

| Type    | Name      | Description                                                                      |
|:--------|:----------|:---------------------------------------------------------------------------------|
| 0       | Recent    | Sort by when the [artist](/definitions/artist#artist) was added to the database. |
| 1       | Name      | Sort by the [artist](/definitions/artist#artist)'s name.                         |
| 2       | Tracks    | Sort by how many songs are available for use.                                    |
| 3       | Status    | Sort by the availability of the [artist](/definitions/artist#artist).            |
| 4       | Genre     | Sort by the genre alphabetically.                                                |

## Response

The endpoint will give you a list of [artists](/definitions/artist#artist) matching the search query, sorted by the [sort](#sorting) parameter.
If the server fails to find any [artists](/definitions/artist#artist) matching the query, it will return a [404 not found](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/404) error.

### Successful response data

| Field    | Type                                                                  | Description                                                                      |
|:---------|:----------------------------------------------------------------------|:---------------------------------------------------------------------------------|
| code     | [HTTP Code](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) | The status code of the response.                                                 |
| data     | [Artist](/definitions/artist#artist)[]                                | An array of [artists](/definitions/artist#artist) that follows the search query. |

### Error response data

| Field    | Type                                                                  | Description                                          |
|:---------|:----------------------------------------------------------------------|:-----------------------------------------------------|
| code     | [HTTP Code](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) | The status code of the response.                     |
| message  | String (optional)                                                     | The message sent back describing on what went wrong. |

### Example response

```json
{
  "code": 200,
  "data": [
    // Type: Artist
    {
      "id": 103,
      "name": "DXL44",
      // ...
    },
    // Type: Artist
    {
      "id": 18,
      "name": "TheFatRat",
      // ...
    }
  ]
}
```
