# http [![GoDoc](https://godoc.org/github.com/vadv/gopher-lua-libs/http?status.svg)](https://godoc.org/github.com/vadv/gopher-lua-libs/http)

## Usage

```lua
local http = require("http")
local client = http.client()

-- GET
local request = http.request("GET", "http://hostname.com")
local result, err = client:do_request(request)
if err then error(err) end
if not(result.code == 200) then error("code") end
if not(result.body == "xxx.xxx.xxx.xxx") then error("body") end

-- GET: with auth basic
local request = http.request("GET", "http://hostname.com")
request:set_basic_auth("admin", "123456")


-- POST: with headers
local client = http.client()
local request = http.request("POST", "http://hostname.com/api.json", "{}")
request:header_set("Content-Type", "application/json")
```