---
layout: default
title: Artist
parent: Definitions
nav_order: 1
---

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

# Artist
{: .d-inline-block }
Object
{: .label .label-yellow }

In [VADB](https://fadb.live/), an Artist is commonly described as a [music producer](https://en.wikipedia.org/wiki/Record_producer).
[VADB](https://fadb.live/) stores [information](#properties) about these artists and also displays information on what rights level creators have in using their music.

Artists also has [usage rights](#) assigned to them by [Admins](#). These rights are used to describe what level creators can use with their music collections.

## Properties

| Field       | Type                           | Description                                                                                                             |
|:-------------|:------------------------------|:------------------------------------------------------------------------------------------------------------------------|
| id           | Number                        | The ID of the artist.                                                                                                   |
| name         | String                        | The name of the artist.                                                                                                 |
| aliases      | String[]                      | Any aliases the artist might have, due to me being a bumbling idiot this is wrapped in a `{ "name": "<name>" }` format. |
| description  | String                        | The description of the artist, generally describes a short history behind the artist.                                   |
| tracks       | Number                        | How many tracks are available for use.                                                                                  |
| genre        | String                        | What genre the artist uses the most.                                                                                    |
| status       | [Status](#status)             | Determines at what state the artist is in. Only viewable for [Admins](#).                                               |
| availability | [Availability](#availability) | How the songs should be used.                                                                                           |
| notes        | String                        | Any notes for the artist. Only viewable for [Admins](#).                                                                |
| usageRights  | [Usage Rights](#usage-rights) | A list of rights a level creator has to follow.                                                                         |
| details      | [Details](#details)           | Any other details about the artist.                                                                                     |

### Status
{: .d-inline-block }
Enum
{: .label .label-blue .mt-2 }

The given status of this artist. Only viewable and managed by [Admins](#). This is used to describe what response the artist gave.

| Type    | Name       | Description                                      |
|:--------|:-----------|:-------------------------------------------------|
| 0       | Completed  | A response from the artist has been given.       |
| 1       | No contact | No response from the artist.                     |
| 2       | Pending    | Awaiting response from the artist.               |
| 3       | Requested  | [An anonymous user has requested the artist.](#) |
| default | -          | Nil.                                             |

### Availability
{: .d-inline-block }
Enum
{: .label .label-blue .mt-2 }

The availability for songs from this artist. This is what level creators are looking for when checking to make sure if songs from this artist are available for use.

| Type    | Name             | Description                                                              |
|:--------|:-----------------|:-------------------------------------------------------------------------|
| 0       | Verified         | All songs from the artist is available for use without any consequences. |
| 1       | Disallowed       | All songs are not allowed for use.                                       |
| 2       | Contact required | A level creator must contact the artist first before using the song.     |
| 3       | Varies           | Song usability may vary. (eventually a song listing will be available).  |
| default | -                | Nil.                                                                     |

### Usage Rights
{: .d-inline-block }
Object[]
{: .label .label-yellow .mt-2 }

A list of rights a level creator has to follow when using songs from this artist.

| Name  | Type    | Description                                    |
|:------|:--------|:-----------------------------------------------|
| Name  | String  | The name of the right. e.g. Access to "album". |
| Value | Boolean | Whether a level creator can use that right.    |

### Details
{: .d-inline-block }
Object
{: .label .label-yellow .mt-2 }

Any other details about the artist. Currently only socials are viewable here.

#### Socials
{: .d-inline-block }
Object[]
{: .label .label-yellow .mt-2 }

| Name | Type    | Description                            |
|:-----|:--------|:---------------------------------------|
| Link | String  | A link provided for the artist.        |
| Type | Service | The type of service this link is from. |


## Example JSON

```json
{
  "id": 5,
  "name": "Aratonati",
  "aliases": [
    {
      "name": "ArolfandToast"
    }
  ],
  "description": "Aratonati is a long time Music Artist and Level Maker within the PA community.\r\n\r\nThe majority of their songs are made in SunVox and then edited in Audacity.",
  "tracks": 31,
  "genre": "Mixed",
  "status": 0,
  "availability": 0,
  "notes": "(Formerly known as ArolfandToast)",
  "usageRights": [
    {
      "name": "All songs with credit",
      "value": true
    }
  ],
  "details": {
    "socials": [
      {
        "link": "https://soundcloud.com/aratonati",
        "type": "soundcloud"
      },
      {
        "link": "https://www.youtube.com/c/Aratonati",
        "type": "youtube"
      },
      {
        "link": "https://twitter.com/ArolfandToast",
        "type": "twitter"
      }
    ]
  }
}
```