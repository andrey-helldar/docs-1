---
editable: false
sourcePath: en/_api-ref/video/v1/api-ref/Episode/batchGet.md
---

# Video API, REST: Episode.BatchGet

Batch get episodes for channel.

## HTTP request

```
POST https://video.{{ api-host }}/video/v1/episodes:batchGet
```

## Body parameters {#yandex.cloud.video.v1.BatchGetEpisodesRequest}

```json
{
  "channelId": "string",
  "episodeIds": [
    "string"
  ]
}
```

#|
||Field | Description ||
|| channelId | **string**

Required field. ID of the channel. ||
|| episodeIds[] | **string**

List of requested episode IDs. ||
|#

## Response {#yandex.cloud.video.v1.BatchGetEpisodesResponse}

**HTTP Code: 200 - OK**

```json
{
  "episodes": [
    {
      "id": "string",
      "streamId": "string",
      "lineId": "string",
      "title": "string",
      "description": "string",
      "thumbnailId": "string",
      "startTime": "string",
      "finishTime": "string",
      "dvrSeconds": "string",
      "visibilityStatus": "string",
      // Includes only one of the fields `publicAccess`, `authSystemAccess`, `signUrlAccess`
      "publicAccess": "object",
      "authSystemAccess": "object",
      "signUrlAccess": "object",
      // end of the list of possible fields
      "createdAt": "string",
      "updatedAt": "string"
    }
  ]
}
```

#|
||Field | Description ||
|| episodes[] | **[Episode](#yandex.cloud.video.v1.Episode)**

List of episodes for specific channel. ||
|#

## Episode {#yandex.cloud.video.v1.Episode}

#|
||Field | Description ||
|| id | **string**

ID of the episode. ||
|| streamId | **string**

ID of the stream. Optional, empty if the episode is linked to the line ||
|| lineId | **string**

ID of the line. Optional, empty if the episode is linked to the stream ||
|| title | **string**

Channel title. ||
|| description | **string**

Channel description. ||
|| thumbnailId | **string**

ID of the thumbnail. ||
|| startTime | **string** (date-time)

Episode start time.

String in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) text format. The range of possible values is from
`0001-01-01T00:00:00Z` to `9999-12-31T23:59:59.999999999Z`, i.e. from 0 to 9 digits for fractions of a second.

To work with values in this field, use the APIs described in the
[Protocol Buffers reference](https://developers.google.com/protocol-buffers/docs/reference/overview).
In some languages, built-in datetime utilities do not support nanosecond precision (9 digits). ||
|| finishTime | **string** (date-time)

Episode finish time.

String in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) text format. The range of possible values is from
`0001-01-01T00:00:00Z` to `9999-12-31T23:59:59.999999999Z`, i.e. from 0 to 9 digits for fractions of a second.

To work with values in this field, use the APIs described in the
[Protocol Buffers reference](https://developers.google.com/protocol-buffers/docs/reference/overview).
In some languages, built-in datetime utilities do not support nanosecond precision (9 digits). ||
|| dvrSeconds | **string** (int64)

Enables episode DVR mode. DVR seconds determines how many last seconds of the stream are available.

possible values:
* `0`: infinite dvr size, the full length of the stream allowed to display
* `>0`: size of dvr window in seconds, the minimum value is 30s ||
|| visibilityStatus | **enum** (VisibilityStatus)

- `VISIBILITY_STATUS_UNSPECIFIED`
- `PUBLISHED`
- `UNPUBLISHED` ||
|| publicAccess | **object**

Episode is available to everyone.

Includes only one of the fields `publicAccess`, `authSystemAccess`, `signUrlAccess`.

Episode access rights. ||
|| authSystemAccess | **object**

Checking access rights using the authorization system.

Includes only one of the fields `publicAccess`, `authSystemAccess`, `signUrlAccess`.

Episode access rights. ||
|| signUrlAccess | **object**

Checking access rights using url's signature.

Includes only one of the fields `publicAccess`, `authSystemAccess`, `signUrlAccess`.

Episode access rights. ||
|| createdAt | **string** (date-time)

Time when episode was created.

String in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) text format. The range of possible values is from
`0001-01-01T00:00:00Z` to `9999-12-31T23:59:59.999999999Z`, i.e. from 0 to 9 digits for fractions of a second.

To work with values in this field, use the APIs described in the
[Protocol Buffers reference](https://developers.google.com/protocol-buffers/docs/reference/overview).
In some languages, built-in datetime utilities do not support nanosecond precision (9 digits). ||
|| updatedAt | **string** (date-time)

Time of last episode update.

String in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) text format. The range of possible values is from
`0001-01-01T00:00:00Z` to `9999-12-31T23:59:59.999999999Z`, i.e. from 0 to 9 digits for fractions of a second.

To work with values in this field, use the APIs described in the
[Protocol Buffers reference](https://developers.google.com/protocol-buffers/docs/reference/overview).
In some languages, built-in datetime utilities do not support nanosecond precision (9 digits). ||
|#