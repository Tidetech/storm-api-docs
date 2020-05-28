# /v2/datasets/{group}/{dataset}/points/

**Summary:** Point data from dataset

**Description:** The /v2/datasets/{group}/{dataset}/points/ endpoint extracts
data from a dataset at one or more points, for one or more
parameters. The endpoint only accepts POST requests. POST
requests must be in JSON format, with the appropriate
Content-Type: application/json headers set.

**Endpoint** `/v2/datasets/{group}/{dataset}/points/`

**Method** `POST`


``` shell
curl --location --request POST https://api.tidetech.org/v2/datasets/waves/global_waves/points/ \
--user "my_api_key:my_api_secret" \
--header "Content-Type: application/json" \
--data-raw '{
    "points": [
        {
            "id": "point",
            "point": {
                "coordinates": [
                    -1.44457,
                    50.0616
                ],
                "type": "Point"
            },
            "timestep": "2020-05-29T18:00:00Z"
        },
        {
            "id": "multipoint",
            "point": {
                "coordinates": [
                	[-8.695, 50.079],
                	[-1.472, 50.1438]
                ],
                "type": "MultiPoint"
            },
            "timestep": "2020-05-27T06:00:00Z",
            "parameters": [
            	"HTSGW",
            	"DIRPW"
            ]
        }
    ]
}'
```

``` javascript
const axios = require("axios")
const apikey = "my_api_key"
const apisecret = "my_api_secret"
const url = "https://api.tidetech.org/v2/datasets/waves/global_waves/points/"
const payload = {
    "points": [
        {
            "id": "point",
            "point": {
                "coordinates": [
                    -1.44457,
                    50.0616
                ],
                "type": "Point"
            },
            "timestep": "2020-05-29T18:00:00Z"
        },
        {
            "id": "multipoint",
            "point": {
                "coordinates": [
                    [-8.695, 50.079],
                    [-1.472, 50.1438]
                ],
                "type": "MultiPoint"
            },
            "timestep": "2020-05-27T06:00:00Z",
            "parameters": [
                "HTSGW",
                "DIRPW"
            ]
        }
    ]
}

axios.post(url, payload, {
    auth: {
        username: apikey,
        password: apisecret,
    }
}).then((response) => {
    console.log(JSON.stringify(response.data))
}).catch((error) => {
    console.log(error);
})
```

``` python
from requests import request

apikey = "my_api_key"
apisecret = "my_api_secret"
url = "https://api.tidetech.org/v2/datasets/waves/global_waves/points/"
payload = {
    "points": [
        {
            "id": "point",
            "point": {
                "coordinates": [
                    -1.44457,
                    50.0616
                ],
                "type": "Point"
            },
            "timestep": "2020-05-29T18:00:00Z"
        },
        {
            "id": "multipoint",
            "point": {
                "coordinates": [
                    [-8.695, 50.079],
                    [-1.472, 50.1438]
                ],
                "type": "MultiPoint"
            },
            "timestep": "2020-05-27T06:00:00Z",
            "parameters": [
                "HTSGW",
                "DIRPW"
            ]
        }
    ]
}

response = request("POST", url, json=payload, auth=(apikey, apisecret))

print(response.json())
```

``` csharp
string apikey = "my_api_key";
string apisecret = "my_api_secret";
string url = "https://api.tidetech.org/v2/datasets/waves/global_waves/points/";
var payload = "{" +
    "\"points\": [" +
        "{" +
            "\"id\": \"point\"," + 
            "\"point\": {" +
                "\"coordinates\": [" +
                    "-1.44457, 50.0616" +
                "]," +
                "\"type\": \"Point\"" +
            "}," +
            "\"timestep\": \"2020-05-29T18:00:00Z\"" +
        "}," +
        "{" +
            "\"id\": \"multipoint\"," +
            "\"point\": {" +
                "\"coordinates\": [" +
                    "[-8.695, 50.079]," +
                    "[-1.472,50.1438]" +
                "]," +
                "\"type\": \"MultiPoint\"" +
            "}," +
            "\"timestep\": \"2020-05-27T06:00:00Z\"," +
            "\"parameters\": [" +
                "\"HTSGW\"," +
                "\"DIRPW\"" +
            "]" +
        "}" +
    "]" +
"}";

var client = new RestClient(url);
client.Authenticator = new HttpBasicAuthenticator(apikey, apisecret);
client.Timeout = -1;

var request = new RestRequest(Method.POST);
request.AddHeader("Content-Type", "application/json");
request.AddJsonBody(payload);

IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

``` go
package main

import (
    "fmt"
    "strings"
    "net/http"
    "io/ioutil"
)

const (
    apikey = "my_api_key"
    apisecret = "my_api_secret"
    url = "https://api.tidetech.org/v2/datasets/waves/global_waves/points/"
)

func main() {

    method := "POST"

    payload := strings.NewReader(`
    {
        "points": [
            {
                "id": "point",
                "point": {
                    "coordinates": [
                        -1.44457,
                        50.0616
                    ],
                    "type": "Point"
                },
                "timestep": "2020-05-29T18:00:00Z"
            },
            {
                "id": "multipoint",
                "point": {
                    "coordinates": [
                        [-8.695, 50.079],
                        [-1.472, 50.1438]
                    ],
                    "type": "MultiPoint"
                },
                "timestep": "2020-05-27T06:00:00Z",
                "parameters": [
                    "HTSGW",
                    "DIRPW"
                ]
            }
        ]
    }
    `)

    client := &http.Client {}
    req, err := http.NewRequest(method, url, payload)

    if err != nil {
        fmt.Println(err)
    }
    req.SetBasicAuth(apikey, apisecret)
    req.Header.Add("Content-Type", "application/json")
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
| dataset | path | dataset id | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | JSON object containing GeoJSON point data |

> The above command returns json containing GeoJSON point data:

``` json
{
    "data": {
        "type": "FeatureCollection",
        "features": [
            {
                "type": "Feature",
                "id": "point",
                "geometry": {
                    "type": "Point",
                    "coordinates": [
                        -1.44457,
                        50.0616
                    ]
                },
                "properties": {
                    "dataset": "global_waves",
                    "timestep": "2020-05-29T18:00:00+00:00",
                    "values": {
                        "HTSGW": 0.949999988079071,
                        "PERPW": 4.659999847412109,
                        "DIRPW": 82.5,
                        "WVHGT": 0.8799999952316284,
                        "WVPER": 3.609999895095825,
                        "WVDIR": 74.01000213623047,
                        "SWELL": 0.1899999976158142,
                        "SWPER": 4.360000133514404,
                        "SWDIR": 31.600004196166992,
                        "LENPW": 33.87022018432617
                    }
                }
            },
            {
                "type": "Feature",
                "id": "multipoint",
                "geometry": {
                    "type": "MultiPoint",
                    "coordinates": [
                        [
                            -8.695,
                            50.079
                        ],
                        [
                            -1.472,
                            50.1438
                        ]
                    ]
                },
                "properties": {
                    "dataset": "global_waves",
                    "timestep": "2020-05-27T06:00:00+00:00",
                    "values": [
                        {
                            "HTSGW": 1.96999990940094,
                            "DIRPW": 277.5
                        },
                        {
                            "HTSGW": 0.7299999594688416,
                            "DIRPW": 262.5
                        }
                    ]
                }
            }
        ]
    }
}
```
