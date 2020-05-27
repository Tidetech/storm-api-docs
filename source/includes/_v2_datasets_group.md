# /v2/datasets/{group}/

**Summary:** List available datasets within a group

**Description:** The /v2/datasets/{group}/ endpoint lists all the datasets with
current data, with a small amount of metadata, and URLs for the
endpoints that extract data.

**Endpoint** `/v2/datasets/{group}/`

**Method** `GET`


```shell
curl --location --request GET https://api.tidetech.org/v2/datasets/currents/ \
--user 'my_api_key:my_api_secret'
```

```javascript
const https = require('https');

const apikey = 'my_api_key';
const apisecret = 'my_api_secret';

const options = {
  hostname: 'api.tidetech.org',
  port: 443,
  path: '/v2/datasets/currents/',
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

url = "https://api.tidetech.org/v2/datasets/currents/"

response = request("GET", url, auth=('my_api_key', 'my_api_secret'))

print(response.json())
```

```csharp
var apikey = "my_api_key";
var apisecret = "my_api_secret";

var client = new RestClient("https://api.tidetech.org/v2/datasets/currents/");
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

  url := "https://api.tidetech.org/v2/datasets/currents/"
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


**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| group | path | dataset group id | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | JSON object containing list of group datasets |


> The above command returns json structured like this (shortened for brevity):

```json
{
    "data": [
        {
            "type": "dataset",
            "id": "baltic_sea_currents",
            "name": "Baltic Sea Currents",
            "group": "Currents",
            "description": "Baltic Sea ocean currents model",
            "resolution_x": 0.028,
            "resolution_y": -0.0167,
            "timestep_duration": "PT3600.0S",
            "links": {
                "self": "https://api.tidetech.org/v2/datasets/currents/baltic_sea_currents/",
                "points": "https://api.tidetech.org/v2/datasets/currents/baltic_sea_currents/points/",
                "area": "https://api.tidetech.org/v2/datasets/currents/baltic_sea_currents/area/",
                "forecast": "https://api.tidetech.org/v2/datasets/currents/baltic_sea_currents/forecast/"
            }
        },
        ...other datasets within the group
    ]
}
```