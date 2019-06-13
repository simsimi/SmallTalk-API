## SmallTalk API Examples

### nodejs
``` javascript
var request = require('request');

var headers = {
    'Content-Type': 'application/json',
    'x-api-key': '{YOUR-PROJECT-API-KEY}'
};

var dataString = '{
            "utext": "hello there", 
            "lang": "en" 
     }';

var options = {
    url: 'https://wsapi.simsimi.com/190410/talk
',
    method: 'POST',
    headers: headers,
    body: dataString
};

function callback(error, response, body) {
    if (!error && response.statusCode == 200) {
        console.log(body);
    }
}
```
### Python
``` python
import requests

headers = {
    'Content-Type': 'application/json',
    'x-api-key': '{YOUR-PROJECT-API-KEY}',
}

data = '{\n            "utext": "hello there", \n            "lang": "en" \n     }'

response = requests.post('https://wsapi.simsimi.com/190410/talk', headers=headers, data=data)
```

### php
``` php
<?php
include('vendor/rmccue/requests/library/Requests.php');
Requests::register_autoloader();
$headers = array(
    'Content-Type' => 'application/json',
    'x-api-key' => '{YOUR-PROJECT-API-KEY}'
);
$data = '{
            "utext": "hello there", 
            "lang": "en" 
     }';
$response = Requests::post('https://wsapi.simsimi.com/190410/talk
', $headers, $data);
``` 

### R
``` R
require(httr)

headers = c(
  `Content-Type` = 'application/json',
  `x-api-key` = '{YOUR-PROJECT-API-KEY}'
)

data = '{\n            "utext": "hello there", \n            "lang": "en" \n     }'

res <- httr::POST(url = 'https://wsapi.simsimi.com/190410/talk', httr::add_headers(.headers=headers), body = data)
```

### Restlet Client
Save this code as a json file and import to [Restlet Client](https://restlet.com/modules/client?utm_source=DHC).
``` json
{
  "front-version": "2.19.2",
  "version": 3,
  "nodes": [
    {
      "type": "Request",
      "method": {
        "requestBody": true,
        "link": "http://tools.ietf.org/html/rfc7231#section-4.3.3",
        "name": "POST"
      },
      "body": {
        "formBody": {
          "overrideContentType": true,
          "encoding": "application/x-www-form-urlencoded",
          "items": []
        },
        "bodyType": "Text",
        "textBody": "{\n            \"utext\":\"hello there\",\n            \"lang\": \"en\"\n}"
      },
      "uri": {
        "query": {
          "delimiter": "&",
          "items": []
        },
        "scheme": {
          "secure": true,
          "name": "https",
          "version": "V11"
        },
        "host": "wsapi.simsimi.com",
        "path": "/190410/talk"
      },
      "id": "9b253d89-5a93-4092-bbec-6c763c2cb4a3",
      "lastModified": "2019-06-13T12:24:17.287+09:00",
      "name": "smalltalk",
      "headers": [
        {
          "enabled": true,
          "name": "Content-Type",
          "value": "application/json"
        },
        {
          "enabled": true,
          "name": "x-api-key",
          "value": "{YOUR-PROJECT-API-KEY}"
        }
      ],
      "metaInfo": {}
    }
  ]
}
```
### C#
``` c#
using (var httpClient = new HttpClient())
{
    using (var request = new HttpRequestMessage(new HttpMethod("POST"), "https://wsapi.simsimi.com/190410/talk"))
    {
        request.Headers.TryAddWithoutValidation("x-api-key", "PASTE_YOUR_PROJECT_KEY_HERE"); 

        request.Content = new StringContent("{\n            \"utext\": \"hello there\", \n            \"lang\": \"en\" \n     }", Encoding.UTF8, "application/json"); 

        var response = await httpClient.SendAsync(request);
    }
}
```
