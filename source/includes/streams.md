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

## Get a Specific Stream

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