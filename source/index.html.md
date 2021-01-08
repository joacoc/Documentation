---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

# toc_footers:
  # - <a href='#'>Sign Up for a Developer Key</a>
  # - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to the Streaminy API! You can use our API to access Streaminy API endpoints, which can get information on various streams and views.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```ruby
require 'streaminy'

api = Streaminy::APIClient.authorize!('meowmeowmeow')
```

```python
import streaminy

api = streaminy.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://www.streaminy.io/authorization" \
  -H "Authorization: API_KEY"
```

```javascript
const streaminy = require('streaminy');

let api = streaminy.authorize('API_KEY');
```

> Make sure to replace `API_KEY` with your API key.

Streaminy uses API keys to allow access to the API. You can view yours in [your profile](http://streaminy.io/profile).

Streaminy expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: API_KEY`

<aside class="notice">
You must replace <code>API_KEY</code> with your personal API key.
</aside>

# Streams

## Get All Streams

```ruby
require 'streaminy'

api = Streaminy::APIClient.authorize!('API_KEY')
api.streams.get
```

```python
import streaminy

api = streaminy.authorize('API_KEY')
api.streams.get()
```

```shell
curl "http://streaminy.io/api/v1/streams" \
  -H "Authorization: API_KEY"
```

```javascript
const streaminy = require('streaminy');

let api = streaminy.authorize('API_KEY');
let streams = api.streams.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "streamId": "a1511384-0903-473d-ad95-2e93f102406e",
    "name": "Bitcoin price",
    "structure": {
      "bitcoin_value": "number",
      "timestamp": "string"
    },
  },
  {
    "streamId": "fa8b7192-4f43-4151-86b7-749b78121e92",
    "name": "Sell",
    "structure": {
      "category": "string",
      "price": "number"
    },
  },
]
```

This endpoint retrieves all streams.

### HTTP Request

`GET http://streaminy.io/api/v1/streams`

<!-- ### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include streams that have already been adopted.

<aside class="success">
Remember — a happy stream is an authenticated stream!
</aside> -->

## Get a Specific Straem

```ruby
require 'streaminy'

api = Streaminy::APIClient.authorize!('API_KEY')
api.streams.get("a1511384-0903-473d-ad95-2e93f102406e")
```

```python
import streaminy

api = streaminy.authorize('API_KEY')
api.streams.get("a1511384-0903-473d-ad95-2e93f102406e")
```

```shell
curl "http://streaminy.io/api/v1/streams/a1511384-0903-473d-ad95-2e93f102406e" \
  -H "Authorization: API_KEY"
```

```javascript
const streaminy = require('streaminy');

let api = streaminy.authorize('API_KEY');
let max = api.streams.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific stream.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`GET http://example.com/streams/`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the stream to retrieve

## Delete a Specific Stream

```ruby
require 'streaminy'

api = streaminy::APIClient.authorize!('API_KEY')
api.streams.delete('a1511384-0903-473d-ad95-2e93f102406e')
```

```python
import streaminy

api = streaminy.authorize('API_KEY')
api.streams.delete('a1511384-0903-473d-ad95-2e93f102406e')
```

```shell
curl "http://streaminy.io/api/v1/streams/a1511384-0903-473d-ad95-2e93f102406e" \
  -X DELETE \
  -H "Authorization: API_KEY"
```

```javascript
const streaminy = require('streaminy');

let api = streaminy.authorize('API_KEY');
let max = api.streams.delete('a1511384-0903-473d-ad95-2e93f102406e');
```

> The above command returns JSON structured like this:

```json
{
  "streamId": "a1511384-0903-473d-ad95-2e93f102406e",
  "name": "Bitcoin price",
  "structure": {
    "bitcoin_value": "number",
    "timestamp": "string"
  },
}
```

This endpoint deletes a specific stream.

### HTTP Request

`DELETE http://streaminy.io/api/v1/streams/a1511384-0903-473d-ad95-2e93f102406e`

### URL Parameters

Parameter | Description
--------- | -----------
streamId | The ID of the stream to delete


# Views

## Get All Views

```ruby
require 'streaminy'

api = Streaminy::APIClient.authorize!('API_KEY')
api.views.get
```

```python
import streaminy

api = streaminy.authorize('API_KEY')
api.views.get()
```

```shell
curl "http://streaminy.io/api/v1/views" \
  -H "Authorization: API_KEY"
```

```javascript
const streaminy = require('streaminy');

let api = streaminy.authorize('API_KEY');
let views = api.views.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "viewId": "feddab2a-9360-4979-8cae-a731d50401ed",
    "name": "Last bitcoin price",
    "query": "SELECT bitcoint_value from \"stream_a1511384-0903-473d-ad95-2e93f102406e\"",
    "aggregationTime": "1 minute"
  },
  {
    "viewId": "27d9bc77-4e5a-4cd4-9062-ec5f0911ad71",
    "name": "Average sell price in the last minute",
    "query": "SELECT AVG(price) from \"stream_fa8b7192-4f43-4151-86b7-749b78121e92\"",
    "aggregationTime": "1 minute"
  },
]
```

This endpoint retrieves all views.

### HTTP Request

`GET http://streaminy.io/api/v1/views`

<!-- ### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include views that have already been adopted.

<aside class="success">
Remember — a happy stream is an authenticated stream!
</aside> -->

## Get a Specific View

```ruby
require 'streaminy'

api = Streaminy::APIClient.authorize!('API_KEY')
api.views.get("27d9bc77-4e5a-4cd4-9062-ec5f0911ad71")
```

```python
import streaminy

api = streaminy.authorize('API_KEY')
api.views.get("27d9bc77-4e5a-4cd4-9062-ec5f0911ad71")
```

```shell
curl "http://streaminy.io/api/v1/views/27d9bc77-4e5a-4cd4-9062-ec5f0911ad71" \
  -H "Authorization: API_KEY"
```

```javascript
const streaminy = require('streaminy');

let api = streaminy.authorize('API_KEY');
let max = api.views.get("27d9bc77-4e5a-4cd4-9062-ec5f0911ad71");
```

> The above command returns JSON structured like this:

```json
{
  "viewId": "feddab2a-9360-4979-8cae-a731d50401ed",
  "name": "Last bitcoin price",
  "query": "SELECT bitcoint_value from \"stream_a1511384-0903-473d-ad95-2e93f102406e\"",
  "aggregationTime": "1 minute"
}
```

This endpoint retrieves a specific stream.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`GET http://example.com/views/`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the view to retrieve

## Delete a Specific Stream

```ruby
require 'streaminy'

api = streaminy::APIClient.authorize!('API_KEY')
api.views.delete('a1511384-0903-473d-ad95-2e93f102406e')
```

```python
import streaminy

api = streaminy.authorize('API_KEY')
api.views.delete('a1511384-0903-473d-ad95-2e93f102406e')
```

```shell
curl "http://streaminy.io/api/v1/views/a1511384-0903-473d-ad95-2e93f102406e" \
  -X DELETE \
  -H "Authorization: API_KEY"
```

```javascript
const streaminy = require('streaminy');

let api = streaminy.authorize('API_KEY');
let max = api.views.delete('feddab2a-9360-4979-8cae-a731d50401ed');
```

> The above command returns JSON structured like this:

```json
{
  "viewId": "feddab2a-9360-4979-8cae-a731d50401ed",
  "name": "Last bitcoin price",
  "query": "SELECT bitcoint_value from \"stream_a1511384-0903-473d-ad95-2e93f102406e\"",
  "aggregationTime": "1 minute"
}
```

This endpoint deletes a specific stream.

### HTTP Request

`DELETE http://streaminy.io/api/v1/views/feddab2a-9360-4979-8cae-a731d50401ed`

### URL Parameters

Parameter | Description
--------- | -----------
streamId | The ID of the view to delete