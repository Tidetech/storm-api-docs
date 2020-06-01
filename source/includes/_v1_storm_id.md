# /v1/storm/{id}

```shell
curl --location --request GET https://storm.tidetech.org/v1/storm/202002E \
--user "my_api_key:my_api_secret"
```

```javascript
const axios = require("axios")

const apikey = "my_api_key";
const apisecret = "my_api_secret"
const url = "https://storm.tidetech.org/v1/storm/202002E"

axios.get(url, {
  auth: {
    username: apikey,
    password: apisecret,
  }
}).then((response) => {
  console.log(response.data)
}).catch((error) => {
  console.log(error)
})
```

```python
from requests import request

apikey = "my_api_key"
apisecret = "my_api_secret"
url = "https://storm.tidetech.org/v1/storm/202002E"

response = request("GET", url, auth=(apikey, apisecret))

print(response.json())
```

```csharp
string apikey = "my_api_key";
string apisecret = "my_api_secret";
string url = "https://storm.tidetech.org/v1/storm/202002E";

var client = new RestClient(url);
client.Authenticator = new HttpBasicAuthenticator(apikey, apisecret);
client.Timeout = -1;

var request = new RestRequest(Method.GET);

var response = client.Execute(request);
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
  url = "https://storm.tidetech.org/v1/storm/202002E"
)

func main() {

  method := "GET"

  client := &http.Client {}
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  req.SetBasicAuth(apikey, apisecret)
  res, _ := client.Do(req)
  defer res.Body.Close()
  body, _ := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```

> Make sure to replace `my_api_key` and `my_api_secret` with your API Key and Secret.


**Summary:** Storm metadata

**Description:** The /v2/storm/{id} endpoint returns the most recent metadata for that storm.

**Endpoint** `/v1/storm/{id}`

**Method** `GET`


**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | JSON object containing storm metadata |


> The above command returns json structured like this:

```json
{
  "data": {
    "id": "202002E",
    "advisory": "2020-05-31T15:00:00Z",
    "is_active": true,
    "name": "AMANDA",
    "basin": "NEP",
    "category": "ts",
    "forecast_hours": 72,
    "geojson": "https://storm.tidetech.org/v1/storm/202002E/features",
    "event_number": 2,
    "position": [
      -90.3,
      14.7
    ],
    "movement": {
      "KPH": 17,
      "MPH": 10,
      "KTS": 9,
      "bearing": 6
    },
    "max_observed_category": "ts",
    "max_forecast_category": "ts",
    "name_list": [
      "02E",
      "AMANDA"
    ],
    "advisory_list": [
      "2020-05-31T03:00:00Z",
      "2020-05-31T09:00:00Z",
      "2020-05-31T15:00:00Z"
    ]
  }
}
```

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path | storm id | Yes | string |
