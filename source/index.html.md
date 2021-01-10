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
  -H "api-key: API_KEY"
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