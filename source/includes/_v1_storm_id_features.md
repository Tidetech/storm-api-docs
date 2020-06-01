# /v1/storm/{id}/features

``` shell
curl --location --request GET https://storm.tidetech.org/v1/storm/202002E/features \
--user "my_api_key:my_api_secret"
```

``` javascript
const axios = require("axios")

const apikey = "my_api_key";
const apisecret = "my_api_secret"
const url = "https://storm.tidetech.org/v1/storm/202002E/features"

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

``` python
from requests import request

apikey = "my_api_key"
apisecret = "my_api_secret"
url = "https://storm.tidetech.org/v1/storm/202002E/features"

response = request("GET", url, auth=(apikey, apisecret))

print(response.json())
```

``` csharp
string apikey = "my_api_key";
string apisecret = "my_api_secret";
string url = "https://storm.tidetech.org/v1/storm/202002E/features";

var client = new RestClient(url);
client.Authenticator = new HttpBasicAuthenticator(apikey, apisecret);
client.Timeout = -1;

var request = new RestRequest(Method.GET);

var response = client.Execute(request);
Console.WriteLine(response.Content);
```

``` go
package main

import (
  "fmt"
  "net/http"
  "io/ioutil"
)

const (
  apikey = "my_api_key"
  apisecret = "my_api_secret"
  url = "https://storm.tidetech.org/v1/storm/202002E/features"
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

**Summary:** Storm GeoJSON representation

**Description:** The /v2/storm/{id}/features endpoint returns the most recent GeoJSON FeatureCollection for that storm.

**Endpoint** `/v1/storm/{id}/features` 

**Method** `GET` 

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | JSON object containing storm metadata |

> The above command returns json structured like this:

``` json
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "geometry": {
        "type": "LineString",
        "coordinates": [
          [
            -91.1,
            12.3
          ],
          [
            -90.6,
            13
          ]
        ]
      },
      "properties": {
        "featureType": "stormTrack-past",
        "id": "202002E",
        "name": "AMANDA",
        "basin": "NEP",
        "intensity": "td",
        "color": "#00ccff",
        "opacity": 221
      }
    },
    {
      "type": "Feature",
      "geometry": {
        "type": "LineString",
        "coordinates": [
          [
            -90.6,
            13
          ],
          [
            -90.4,
            13.8
          ]
        ]
      },
      "properties": {
        "featureType": "stormTrack-past",
        "id": "202002E",
        "name": "AMANDA",
        "basin": "NEP",
        "intensity": "td",
        "color": "#00ccff",
        "opacity": 221
      }
    }
  ],
  ...more storm features
}
```

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path | storm id | Yes | string |
