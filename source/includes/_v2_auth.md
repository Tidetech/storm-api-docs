# /v2/auth/

**Summary:** Check authentication status

**Description:** Check that you have successfully authenticated using the `/v2/auth/` endpoint. See the <a href='#authentication'>Authentication</a> section for more details.

**Endpoint** `/v2/auth/`

**Method** `GET`


```shell
curl --location --request GET https://api.tidetech.org/v2/auth/ \
--user 'my_api_key:my_api_secret'
```

```javascript
const https = require('https');

const apikey = 'my_api_key';
const apisecret = 'my_api_secret';

const options = {
  hostname: 'api.tidetech.org',
  port: 443,
  path: '/v2/auth/',
  headers: {
    'Authorization': `Basic ${Buffer.from(`${apikey}:${apisecret}`).toString('base64')}`,
  },
};

https.get(options, (res) => {
  let data = '';

  res.on("data", (chunk) => {
    data += chunk;
  });

  res.on("end", () => {
    console.log(data);
  });

  res.on("error", (error) => {
    console.error(error);
  });
});
```

```python
from requests import request

url = "https://api.tidetech.org/v2/auth/"

response = request("GET", url, auth=('my_api_key', 'my_api_secret'))

print(response.json())
```

```csharp
var apikey = "my_api_key";
var apisecret = "my_api_secret";

var client = new RestClient("https://api.tidetech.org/v2/auth/");
client.Authenticator = new HttpBasicAuthenticator(apikey, apisecret);
client.Timeout = -1;

var request = new RestRequest(Method.GET);

IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```go
package main

import (
  "fmt"
  "net/http"
  "io/ioutil"
)

const (
  apikey = "my_api_key"
  apisecret = "my_api_secret"
)

func main() {

  url := "https://api.tidetech.org/v2/auth/"
  method := "GET"

  client := &http.Client {}
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  req.SetBasicAuth(apikey, apisecret)
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```

> Make sure to replace `my_api_key` and `my_api_secret` with your API Key and Secret.

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | JSON object containing authenticated entity |
| 401 | Unauthorized |


> The above command returns json structured like this:

```json
{
  "authenticated_as": {
    "type": "api-key",
    "id": "my_api_key",
    "organisation": "Test organisation"
  }
}
```
