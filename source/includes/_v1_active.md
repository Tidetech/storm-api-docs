# /v1/active

```shell
curl --location --request GET https://storm.tidetech.org/v1/active \
--user "my_api_key:my_api_secret"
```

```javascript
const axios = require("axios")

const apikey = "my_api_key";
const apisecret = "my_api_secret"
const url = "https://storm.tidetech.org/v1/active"

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
url = "https://storm.tidetech.org/v1/active"

response = request("GET", url, auth=(apikey, apisecret))

print(response.json())
```

```csharp
string apikey = "my_api_key";
string apisecret = "my_api_secret";
string url = "https://storm.tidetech.org/v1/active";

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
  url = "https://storm.tidetech.org/v1/active"
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


**Summary:** Active storms index

**Description:** The active storms endpoint lists all currently active storms in all basins.

**Endpoint** `/v1/active`

**Method** `GET`


**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | JSON object containing active storms array |


> The above command returns json structured like this:

```json
{
  "data": [
    {
      "id": "202002E",
      "name": "AMANDA",
      "details": "https://storm.tidetech.org/v1/storm/202002E"
    }
  ]
}
```