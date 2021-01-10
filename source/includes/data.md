# Data

## Write a Specific Stream

```ruby
require 'streaminy'

api = Streaminy::APIClient.authorize!('API_KEY')
stream = api.streams.write("a1511384-0903-473d-ad95-2e93f102406e")
stream.send([{
    "bitcoin_value": 345450,
    "timestamp": 1610259366
},
{
    "bitcoin_value": 345455,
    "timestamp": 1610259456
}])
```

```python
import streaminy

api = streaminy.authorize('API_KEY')
stream = api.streams.write("a1511384-0903-473d-ad95-2e93f102406e")
stream.send([{
    "bitcoin_value": 345450,
    "timestamp": 1610259366
},
{
    "bitcoin_value": 345455,
    "timestamp": 1610259456
}])
```

```shell
curl "http://streaminy.io/api/v1/streams/a1511384-0903-473d-ad95-2e93f102406e" \
  -H "api-key: API_KEY"
```

```javascript
const streaminy = require('streaminy');

let api = streaminy.authorize('API_KEY');
let stream = api.streams.write("a1511384-0903-473d-ad95-2e93f102406e");
stream.send([{
    "bitcoin_value": 345450,
    "timestamp": 1610259366
},
{
    "bitcoin_value": 345455,
    "timestamp": 1610259456
}])
```

> The above command returns JSON structured like this:

```json
{
  "streamId": "a1511384-0903-473d-Some-winostr0Rable",
  "error": "Table does not exists."
}
```

## Read a View