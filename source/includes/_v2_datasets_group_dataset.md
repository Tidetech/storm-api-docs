# /v2/datasets/{group}/{dataset}/

**Summary:** Dataset metadata

**Description:** The /v2/datasets/{group}/{dataset}/ endpoint returns all the
available metadata for that dataset.

**Endpoint** `/v2/datasets/{group}/{dataset}/`

**Method** `GET`

<aside class="notice">
See the <a href='#metadata'>Metadata</a> section for more details.
</aside>

```shell
curl --location --request GET https://api.tidetech.org/v2/datasets/currents/baltic_sea_currents/ \
--user 'my_api_key:my_api_secret'
```

```javascript
const https = require('https');

const apikey = 'my_api_key';
const apisecret = 'my_api_secret';

const options = {
  hostname: 'api.tidetech.org',
  port: 443,
  path: '/v2/datasets/currents/baltic_sea_currents/',
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

url = "https://api.tidetech.org/v2/datasets/currents/baltic_sea_currents/"

response = request("GET", url, auth=('my_api_key', 'my_api_secret'))

print(response.json())
```

```csharp
var apikey = "my_api_key";
var apisecret = "my_api_secret";

var client = new RestClient("https://api.tidetech.org/v2/datasets/currents/baltic_sea_currents/");
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

  url := "https://api.tidetech.org/v2/datasets/currents/baltic_sea_currents/"
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


**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| group | path | dataset group id | Yes | string |
| dataset | path | dataset id | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | JSON object containing dataset metadata |


> The above command returns json structured like this:


```json
{
    "data": {
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
        },
        "parameters": [
            {
                "id": "UOGRD",
                "long_name": null,
                "description": "u-component of current",
                "grib_code": 49,
                "var_code": 49,
                "units": "m/s",
                "unit_long": "Metres per second",
                "fill_value": -9999
            },
            {
                "id": "VOGRD",
                "long_name": null,
                "description": "v-component of current",
                "grib_code": 50,
                "var_code": 50,
                "units": "m/s",
                "unit_long": "Metres per second",
                "fill_value": -9999
            }
        ],
        "start_timestep": "2019-05-26T12:00:00+00:00",
        "end_timestep": "2020-05-30T23:00:00+00:00",
        "forecast_timestep": "2020-05-26T00:00:00+00:00",
        "dataset_bounds": {
            "lon_min": 9.023,
            "lon_max": 30.499,
            "lat_min": 52.9909,
            "lat_max": 65.9
        }
    }
}
```
