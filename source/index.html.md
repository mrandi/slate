---
title: Fullstop API

language_tabs:
  - shell

toc_footers:
  - <a href='https://github.com/zalando-stups/fullstop'>Fullstop</a>
  - <a href='https://docs.stups.io/en/latest/components/fullstop.html'>Documentation</a>
  - <a href='https://stups.io/'>STUPS.io</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Fullstop API! You can use our API to access Fullstop API endpoints, which can get information on violations, lifecycle, and useful informations in our database.

We have language bindings in Shell! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This API documentation page was created with [Slate](https://github.com/tripit/slate)
based on [Fullstop](https://github.com/zalando-stups/fullstop-slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: Barer meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your API key.

Fullstop uses Oauth2 tokens to allow access to the API.

Fullstop expects Oauth2 tokens to be included in all API requests to the server in a header that looks like the following:

`Authorization: Barer meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal Oauth2 token.
</aside>

# Fullstop

## Put instance log in S3

```shell
curl "http://example.com/api/instance-logs"
  -H "Authorization: meowmeowmeow"
```
> The above command need a JSON structured body like this:

```json
{
  "accountId": "string",
  "instanceBootTime": "2016-05-10T09:48:34.309Z",
  "instanceId": "string",
  "logData": "string",
  "logType": "USER_DATA",
  "region": "string"
}
```

## Get All violations

```shell
curl "http://example.com/api/violations"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  {
    "accountId": "string",
    "applicationId": "string",
    "applicationVersionId": "string",
    "comment": "string",
    "created": "date-time",
    "createdBy": "string",
    "eventId": "string",
    "id": 0,
    "instanceId": "string",
    "lastModified": "date-time",
    "lastModifiedBy": "string",
    "metaInfo": {},
    "pluginFullyQualifiedClassName": "string",
    "region": "string",
    "ruleID": 0,
    "username": "string",
    "version": 0,
    "violationType": {
      "auditRelevant": true,
      "created": "date-time",
      "createdBy": "string",
      "helpText": "string",
      "id": "string",
      "lastModified": "date-time",
      "lastModifiedBy": "string",
      "priority": 0,
      "title": "string",
      "version": 0,
      "violationSeverity": 0
    }
  }
]
```

This endpoint retrieves all violations.

### HTTP Request

`GET http://example.com/api/violations`

### Query Parameters

Parameter | Type | Default | Description
--------- | ---- | ------- | -----------
accounts | Array[string] | false | Include only violations in these accounts.
from | date-time | false | Include only violations that happened after this point in time
to | date-time | false | Include only violations that happened up to this point in time
last-violation | long | false | Include only violations after the one with this id
checked | boolean | false | Include only violations where checked field equals this value (i.e. resolved violations)
severity | integer | false | Include only violations with a certain severity
priority | integer | false | Include only violations with a certain priority
audit-relevant | boolean | false | Include only violations that are audit relevant
type | string | false | Include only violations with a certain type
types | Array[string] | false | Include only violations with a certain types
application-ids | Array[string] | false | Include only violations with a certain application name
application-version-ids | Array[string] | false | nclude only violations with a certain application version
whitelisted | boolean | false | show also whitelisted vioaltions
pageable | pageable | false | select page

<aside class="success">
Remember — to add always your Oauth2 token!
</aside>

## Get a Specific Violation

```shell
curl "http://example.com/api/violations/2"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "accountId": "string",
  "applicationId": "string",
  "applicationVersionId": "string",
  "comment": "string",
  "created": "date-time",
  "createdBy": "string",
  "eventId": "string",
  "id": 0,
  "instanceId": "string",
  "lastModified": "date-time",
  "lastModifiedBy": "string",
  "metaInfo": {},
  "pluginFullyQualifiedClassName": "string",
  "region": "string",
  "ruleID": 0,
  "username": "string",
  "version": 0,
  "violationType": {
    "auditRelevant": true,
    "created": "date-time",
    "createdBy": "string",
    "helpText": "string",
    "id": "string",
    "lastModified": "date-time",
    "lastModifiedBy": "string",
    "priority": 0,
    "title": "string",
    "version": 0,
    "violationSeverity": 0
  }
}
```

This endpoint retrieves a specific violation.

### HTTP Request

`GET http://example.com/api/violations/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the violation to retrieve
