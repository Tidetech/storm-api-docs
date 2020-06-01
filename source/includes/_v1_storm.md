# /v1/

```shell
curl --location --request GET https://storm.tidetech.org/v1/ \
--user "my_api_key:my_api_secret"
```

```javascript
const axios = require("axios")

const apikey = "my_api_key";
const apisecret = "my_api_secret"
const url = "https://storm.tidetech.org/v1/"

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
url = "https://storm.tidetech.org/v1/"

response = request("GET", url, auth=(apikey, apisecret))

print(response.json())
```

```csharp
string apikey = "my_api_key";
string apisecret = "my_api_secret";
string url = "https://storm.tidetech.org/v1/";

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
  url = "https://storm.tidetech.org/v1/"
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


**Summary:** API index

**Description:** The index endpoint lists the available API endpoints.

**Endpoint** `/v1/`

**Method** `GET`


**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | JSON object containing API index |


> The above command returns json structured like this:

```json
{
  "links": {
    "active": "https://storm.tidetech.org/v1/active"
  }
}
```