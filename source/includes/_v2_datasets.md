# /v2/datasets/

**Summary:** List available dataset groups

**Description:** The /v2/datasets/ endpoint lists all the dataset groups available
to you and their URLS.

**Endpoint** `/v2/datasets/`

**Method** `GET`


```shell
curl --location --request GET https://api.tidetech.org/v2/datasets/ \
--user 'my_api_key:my_api_secret'
```

```javascript
const https = require('https');

const apikey = 'my_api_key';
const apisecret = 'my_api_secret';

const options = {
  hostname: 'api.tidetech.org',
  port: 443,
  path: '/v2/datasets/',
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

url = "https://api.tidetech.org/v2/datasets/"

response = request("GET", url, auth=('my_api_key', 'my_api_secret'))

print(response.json())
```

```csharp
var apikey = "my_api_key";
var apisecret = "my_api_secret";

var client = new RestClient("https://api.tidetech.org/v2/datasets/");
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

  url := "https://api.tidetech.org/v2/datasets/"
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
| 200 | JSON object containing list of group objects |


> The above command returns json structured like this (shortened for brevity):

```json
{
    "data": [
        {
            "type": "group",
            "id": "currents",
            "name": "Currents",
            "description": "Currents",
            "datasets": 10,
            "links": {
                "datasets": "https://api.tidetech.org/v2/datasets/currents/"
            }
        },
        {
            "type": "group",
            "id": "meteorology",
            "name": "Meteorology",
            "description": "Meteorology",
            "datasets": 2,
            "links": {
                "datasets": "https://api.tidetech.org/v2/datasets/meteorology/"
            }
        },
        ...other dataset groups
    ]
}
```
