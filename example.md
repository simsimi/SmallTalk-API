## SmallTalk API Examples

[NodeJS](#nodejs) | [NodeJS (Native)](#nodejs-native) | [NodeJS (Request)](#nodejs-request) | [NodeJS (Unirest)](#nodejs-unirest) | [Python](#python) | [Python (http.client (Python 3))](#python-httpclient-python-3) | [Python (Requests)](#python-requests) | [php](#php) | [PHP (HttpRequest)](#php-httprequest) | [PHP (pecl_http)](#php-pecl_http) | [PHP (cURL)](#php-curl) | [R](#r) | [C#](#c) | [C (LibCurl)](#c-libcurl) | [C# (RestSharp)](#c-restsharp) | [Go](#go) | [Java (OK HTTP)](#java-ok-http) | [Java (Unirest)](#java-unirest) | [Javascript (jQuery ajax)](#javascript-jquery-ajax) | [Javascript (XHR)](#javascript-xhr) | [Objective-c (NSURL)](#objective-c-nsurl) | [Ruby (NET::http)](#ruby-nethttp) | [SWIFT (NSURL)](#swift-nsurl) | [Restlet Client](#restlet-client) 

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
### C (LibCurl)
``` c
CURL *hnd = curl_easy_init();

curl_easy_setopt(hnd, CURLOPT_CUSTOMREQUEST, "POST");
curl_easy_setopt(hnd, CURLOPT_URL, "https://wsapi.simsimi.com/190410/talk/");

struct curl_slist *headers = NULL;
headers = curl_slist_append(headers, "x-api-key: PASTE_YOUR_PROJECT_KEY_HERE");
headers = curl_slist_append(headers, "Content-Type: application/json");
curl_easy_setopt(hnd, CURLOPT_HTTPHEADER, headers);

curl_easy_setopt(hnd, CURLOPT_POSTFIELDS, "{\n\t\"utext\": \"hello there\", \n\t\"lang\": \"en\" \n}");

CURLcode ret = curl_easy_perform(hnd);
```

### C# (RestSharp)
``` c#
var client = new RestClient("https://wsapi.simsimi.com/190410/talk/");
var request = new RestRequest(Method.POST);
request.AddHeader("x-api-key", "PASTE_YOUR_PROJECT_KEY_HERE");
request.AddHeader("Content-Type", "application/json");
request.AddParameter("undefined", "{\n\t\"utext\": \"hello there\", \n\t\"lang\": \"en\" \n}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

### Go
``` go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://wsapi.simsimi.com/190410/talk/"

	payload := strings.NewReader("{\n\t\"utext\": \"hello there\", \n\t\"lang\": \"en\" \n}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("Content-Type", "application/json")
	req.Header.Add("x-api-key", "PASTE_YOUR_PROJECT_KEY_HERE")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

### Java (OK HTTP)
``` java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\n\t\"utext\": \"hello there\", \n\t\"lang\": \"en\" \n}");
Request request = new Request.Builder()
  .url("https://wsapi.simsimi.com/190410/talk/")
  .post(body)
  .addHeader("Content-Type", "application/json")
  .addHeader("x-api-key", "PASTE_YOUR_PROJECT_KEY_HERE")
  .build();

Response response = client.newCall(request).execute();
```

### Java (Unirest)
``` java
HttpResponse<String> response = Unirest.post("https://wsapi.simsimi.com/190410/talk/")
  .header("Content-Type", "application/json")
  .header("x-api-key", "PASTE_YOUR_PROJECT_KEY_HERE")
  .body("{\n\t\"utext\": \"hello there\", \n\t\"lang\": \"en\" \n}")
  .asString();
```

### Javascript (jQuery ajax)
``` javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://wsapi.simsimi.com/190410/talk/",
  "method": "POST",
  "headers": {
    "Content-Type": "application/json",
    "x-api-key": "PASTE_YOUR_PROJECT_KEY_HERE"
  },
  "processData": false,
  "data": "{\n\t\"utext\": \"hello there\", \n\t\"lang\": \"en\" \n}"
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

### Javascript (XHR)
``` javascript
var data = JSON.stringify({
  "utext": "hello there",
  "lang": "en"
});

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://wsapi.simsimi.com/190410/talk/");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("x-api-key", "PASTE_YOUR_PROJECT_KEY_HERE");

xhr.send(data);
```

### NodeJS (Native)
``` javascript
var http = require("https");

var options = {
  "method": "POST",
  "hostname": [
    "wsapi",
    "simsimi",
    "com"
  ],
  "path": [
    "190410",
    "talk",
    ""
  ],
  "headers": {
    "Content-Type": "application/json",
    "x-api-key": "PASTE_YOUR_PROJECT_KEY_HERE"
  }
};

var req = http.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function () {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });
});

req.write(JSON.stringify({ utext: 'hello there', lang: 'en' }));
req.end();
```


### NodeJS (Request)
``` javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://wsapi.simsimi.com/190410/talk/',
  headers: 
   { 'x-api-key': 'PASTE_YOUR_PROJECT_KEY_HERE',
     'Content-Type': 'application/json' },
  body: { utext: 'hello there', lang: 'en' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```


### NodeJS (Unirest)
``` javascript
var unirest = require("unirest");

var req = unirest("POST", "https://wsapi.simsimi.com/190410/talk/");

req.headers({
  "x-api-key": "PASTE_YOUR_PROJECT_KEY_HERE",
  "Content-Type": "application/json"
});

req.type("json");
req.send({
  "utext": "hello there",
  "lang": "en"
});

req.end(function (res) {
  if (res.error) throw new Error(res.error);

  console.log(res.body);
});

```

### Objective-c (NSURL)
``` objective-c
#import <Foundation/Foundation.h>

NSDictionary *headers = @{ @"Content-Type": @"application/json",
                           @"x-api-key": @"PASTE_YOUR_PROJECT_KEY_HERE" };
NSDictionary *parameters = @{ @"utext": @"hello there",
                              @"lang": @"en" };

NSData *postData = [NSJSONSerialization dataWithJSONObject:parameters options:0 error:nil];

NSMutableURLRequest *request = [NSMutableURLRequest requestWithURL:[NSURL URLWithString:@"https://wsapi.simsimi.com/190410/talk/"]
                                                       cachePolicy:NSURLRequestUseProtocolCachePolicy
                                                   timeoutInterval:10.0];
[request setHTTPMethod:@"POST"];
[request setAllHTTPHeaderFields:headers];
[request setHTTPBody:postData];

NSURLSession *session = [NSURLSession sharedSession];
NSURLSessionDataTask *dataTask = [session dataTaskWithRequest:request
                                            completionHandler:^(NSData *data, NSURLResponse *response, NSError *error) {
                                                if (error) {
                                                    NSLog(@"%@", error);
                                                } else {
                                                    NSHTTPURLResponse *httpResponse = (NSHTTPURLResponse *) response;
                                                    NSLog(@"%@", httpResponse);
                                                }
                                            }];
[dataTask resume];
```


### PHP (HttpRequest)
``` php
<?php

$request = new HttpRequest();
$request->setUrl('https://wsapi.simsimi.com/190410/talk/');
$request->setMethod(HTTP_METH_POST);

$request->setHeaders(array(
  'x-api-key' => 'PASTE_YOUR_PROJECT_KEY_HERE',
  'Content-Type' => 'application/json'
));

$request->setBody('{
	"utext": "hello there", 
	"lang": "en" 
}');

try {
  $response = $request->send();

  echo $response->getBody();
} catch (HttpException $ex) {
  echo $ex;
}
```

### PHP (pecl_http)
``` php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{
	"utext": "hello there", 
	"lang": "en" 
}');

$request->setRequestUrl('https://wsapi.simsimi.com/190410/talk/');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'x-api-key' => 'PASTE_YOUR_PROJECT_KEY_HERE',
  'Content-Type' => 'application/json'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

### PHP (cURL)
``` php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://wsapi.simsimi.com/190410/talk/",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\n\t\"utext\": \"hello there\", \n\t\"lang\": \"en\" \n}",
  CURLOPT_HTTPHEADER => array(
    "Content-Type: application/json",
    "x-api-key: PASTE_YOUR_PROJECT_KEY_HERE"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

### Python (http.client (Python 3))
``` python
import http.client

conn = http.client.HTTPConnection("wsapi,simsimi,com")

payload = "{\n\t\"utext\": \"hello there\", \n\t\"lang\": \"en\" \n}"

headers = {
    'Content-Type': "application/json",
    'x-api-key': "PASTE_YOUR_PROJECT_KEY_HERE"
    }

conn.request("POST", "190410,talk,", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

### Python (Requests)
``` python
import requests

url = "https://wsapi.simsimi.com/190410/talk/"

payload = "{\n\t\"utext\": \"hello there\", \n\t\"lang\": \"en\" \n}"
headers = {
    'Content-Type': "application/json",
    'x-api-key': "PASTE_YOUR_PROJECT_KEY_HERE"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

### Ruby (NET::http)
``` ruby
require 'uri'
require 'net/http'

url = URI("https://wsapi.simsimi.com/190410/talk/")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["Content-Type"] = 'application/json'
request["x-api-key"] = 'PASTE_YOUR_PROJECT_KEY_HERE'
request.body = "{\n\t\"utext\": \"hello there\", \n\t\"lang\": \"en\" \n}"

response = http.request(request)
puts response.read_body
```

### SWIFT (NSURL)
``` swift
import Foundation

let headers = [
  "Content-Type": "application/json",
  "x-api-key": "PASTE_YOUR_PROJECT_KEY_HERE"
]
let parameters = [
  "utext": "hello there",
  "lang": "en"
] as [String : Any]

let postData = JSONSerialization.data(withJSONObject: parameters, options: [])

let request = NSMutableURLRequest(url: NSURL(string: "https://wsapi.simsimi.com/190410/talk/")! as URL,
                                        cachePolicy: .useProtocolCachePolicy,
                                    timeoutInterval: 10.0)
request.httpMethod = "POST"
request.allHTTPHeaderFields = headers
request.httpBody = postData as Data

let session = URLSession.shared
let dataTask = session.dataTask(with: request as URLRequest, completionHandler: { (data, response, error) -> Void in
  if (error != nil) {
    print(error)
  } else {
    let httpResponse = response as? HTTPURLResponse
    print(httpResponse)
  }
})

dataTask.resume()
``` 
