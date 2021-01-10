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
  -H "api-key: API_KEY"
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
  -H "api-key: API_KEY"
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
  -H "api-key: API_KEY"
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