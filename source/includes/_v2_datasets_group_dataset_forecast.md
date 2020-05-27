# /v2/datasets/{group}/{dataset}/forecast/

**Summary:** download a dataset's most recent forecast

**Description:** The /v2/datasets/{group}/{dataset}/area/ endpoint will download the most recent forecast as a NetCDF or GRIB dataset.

**Endpoint** `/v2/datasets/{group}/{dataset}/forecast/`

**Method** `GET`


``` shell
curl --location --request GET https://api.tidetech.org/v2/datasets/currents/solent_currents/forecast/ \
--user 'my_api_key:my_api_secret' \
--output solent_forecast.nc
```

``` javascript
const fs = require('fs')
const axios = require('axios')
const apikey = 'my_api_key'
const apisecret = 'my_api_secret'

axios.get("https://api.tidetech.org/v2/datasets/currents/solent_currents/forecast/", data, {
    responseType: 'stream',
    auth: {
        username: apikey,
        password: apisecret,
    }
}).then((response) => {
    response.data.pipe(fs.createWriteStream("solent_forecast.nc"))
}).catch((error) => {
    console.log(error);
})
```

``` python
from requests import request

url = "https://api.tidetech.org/v2/datasets/currents/solent_currents/forecast/"

response = request("GET", url, auth=("my_api_key", "my_api_secret"), stream=True)

with open('solent_forecast.nc', 'wb') as f:
    for chunk in response.iter_content(chunk_size=1024*1024):
        f.write(chunk)
```

``` csharp
var apikey = "my_api_key";
var apisecret = "my_api_secret";

var client = new RestClient("https://api.tidetech.org/v2/datasets/currents/solent_currents/forecast/");
client.Authenticator = new HttpBasicAuthenticator(apikey, apisecret);
client.Timeout = -1;

var request = new RestRequest(Method.GET);

var response = client.DownloadData(request);
File.WriteAllBytes("solent_forecast.nc", response);
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
)

func main() {

    url := "https://api.tidetech.org/v2/datasets/currents/solent_currents/forecast/"
    method := "GET"

    client := &http.Client {}
    req, err := http.NewRequest(method, url, nil)

    if err != nil {
        fmt.Println(err)
    }
    req.SetBasicAuth(apikey, apisecret)
    res, err := client.Do(req)
    defer res.Body.Close()
    data, _ := ioutil.ReadAll(res.Body)

    ioutil.WriteFile("solent_forecast.nc", data, 0777)
}
```

> Make sure to replace `my_api_key` and `my_api_secret` with your API Key and Secret.


**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| group | path | dataset group id | Yes | string |
| dataset | path | dataset id | Yes | string |
| compress | query | file compression type | No | string |
| format | query | file format | No | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns raster data in GRIB or NetCDF format |

> The above command returns area data in GRIB or NetCDF format
