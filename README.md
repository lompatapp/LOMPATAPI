# Lompat Email Validation API Documentation

Welcome to the Lompat Email Validation API, a comprehensive tool designed to enhance your email data quality through a series of validations, predictions, and checks. Our API covers a wide range of features from basic format checks to detailed analyses including domain age, provider type, and much more.

## Getting Started

1. **Get your API key**: You can get your unique API key from our site at [https://lompat.app/](https://lompat.app/).
2. **Make a request**: Use the sample JSON requests bellow as a template.
3. **Handle the response**: Implement logic to use the API's JSON data on your app.

## API Base URL

**Base URL**: `https://lompat.app/v/1/`

Use this base URL to make all your API requests.

## Features

Our API offers the following features:

- **Basic Email Validation**: Checks if the email is in a valid format.
- **Educational, Government, and Corporate Email Detection**: Identifies if the email belongs to educational, government, or specific corporate domains like Microsoft.
- **Disposable and Role Email Detection**: Detects disposable addresses and role-based emails like admin@, support@, etc.
- **Free Email Provider Check**: Identifies if the email is from a free provider like Gmail or Yahoo.
- **Spam Trap Detection**: Checks if the email is a known spam trap.
- **Domain Corrections and Predictions**: Offers corrections for common domain misspellings and predicts names from the email username.
- **Domain Information**: Retrieves domain age and MX records.
- **Catch-All Detection**: Determines if the domain has a catch-all policy for emails.
- **Gender Detection**: Predicts the gender based on the first name extracted from the email.
- **Quota**: Detect if the mailbox quota is full
- **Social Media Checks**: Validates presence on Microsoft.

## API Response Format

Here is what the response from the API looks like:

```json
{
    "status": true,
    "reason": "DELIVERABLE",
    "email": "lompat.user@lompat.app",
    "first_name": "Lompat",
    "last_name": "User",
    "gender": "Male",
    "username": "lompat.user",
    "domain": "lompat.app",
    "domain_age": "10 years, 8 months, 3 days",
    "mx_record": "lompat.app.mx.com",
    "score": 10,
    "expire_date": "2027-04-30"
}
```

## Using the API

To use the Email Validation API, send a JSON POST request to our endpoint. Below are examples of how to format your requests.

### Basic Validation Request

```json
{
  "email": "lompat.user@lompat.app",
  "key": "your_api_key"
}
```

### Microsoft Email Check

To verify if the email is valid for Microsoft services:

```json
{
  "email": "lompat.user@lompat.app",
  "microsoft": "true",
  "key": "your_api_key"
}
```

### FREE Email Check

To Seperate Free Email Provider:

```json
{
  "email": "lompat.user@lompat.app",
  "free": "true",
  "key": "your_api_key"
}
```

## Example Implementations

Here are some quick examples on how to use the Email Validation API with different programming languages and frameworks:

### Bash

Using cURL from the command line in Bash:

```bash
#!/bin/bash

# API URL
url="https://lompat.app/v/1/"

# Data payload
data='{
  "email": "lompat.user@lompat.app",
  "key": "your_api_key"
}'

# Send the POST request
response=$(curl -s -X POST "$url" -H "Content-Type: application/json" -d "$data")

# Output the response
echo "Response:"
echo "$response"
```

### PHP

Using cURL to make a POST request:

```php
<?php
$url = 'https://lompat.app/v/1/';
$data = array(
    'email' => 'lompat.user@lompat.app',
    'key' => 'your_api_key'
);

$ch = curl_init($url);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($data));
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Content-Type:application/json'));

$response = curl_exec($ch);
curl_close($ch);

echo $response;
?>
```

### Laravel (PHP Framework)

Using HTTP Client in a controller method:

```php
use Illuminate\Support\Facades\Http;

public function validateEmail()
{
    $response = Http::post('https://lompat.app/v/1/', [
        'email' => 'lompat.user@lompat.app',
        'key' => 'your_api_key'
    ]);

    return $response->json();
}
```

### CodeIgniter (PHP Framework)

Using CodeIgniter's HTTP client in a model:

```php
public function validateEmail()
{
    $client = \Config\Services::curlrequest();
    $response = $client->request('POST', 'https://lompat.app/v/1/', [
        'json' => [
            'email' => 'lompat.user@lompat.app',
            'key' => 'your_api_key'
        ]
    ]);

    return json_decode($response->getBody());
}
```

### Python

Using the `requests` library to send a POST request:

```python
import requests

url = 'https://lompat.app/v/1/'
data = {
    'email': 'lompat.user@lompat.app',
    'key': 'your_api_key'
}

response = requests.post(url, json=data)
print(response.text)
```

### Django (Python Framework)

Using Django views to send a POST request:

```python
from django.http import JsonResponse
import requests

def validate_email(request):
    url = 'https://lompat.app/v/1/'
    data = {
        'email': 'lompat.user@lompat.app',
        'key': 'your_api_key'
    }
    response = requests.post(url, json=data)
    return JsonResponse(response.json())
```

### Golang

Using the `net/http` package to send a POST request:

```go
package main

import (
    "bytes"
    "net/http"
    "io/ioutil"
    "fmt"
)

func main() {
    url := "https://lompat.app/v/1/"
    var jsonData = []byte(`{
        "email": "lompat.user@lompat.app",
        "key": "your_api_key"
    }`)

    req, err := http.NewRequest("POST", url, bytes.NewBuffer(jsonData))
    req.Header.Set("Content-Type", "application/json")

    client := &http.Client{}
    resp, err := client.Do(req)
    if err != nil {
        panic(err)
    }
    defer resp.Body.Close()

    body, _ := ioutil.ReadAll(resp.Body)
    fmt.Println("Response:", string(body))
}
```

### JavaScript

Using the Fetch API to send a POST request from a client-side application:

```javascript
const url = 'https://lompat.app/v/1/';
const data = {
  email: 'lompat.user@lompat.app',
  key: 'your_api_key'
};

fetch(url, {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify(data)
})
.then(response => response.json())
.then(data => console.log('Success:', data))
.catch((error) => console.error('Error:', error));
```

### Java

Using `HttpURLConnection` to send a POST request:

```java
import java.io.OutputStream;
import java.net.HttpURLConnection;
import java.net.URL;
import java.nio.charset.StandardCharsets;

public class Main {
    public static void main(String[] args) {
        String data = "{\"email\":\"lompat.user@lompat.app\", \"key\":\"your_api_key\"}";
        try {
            URL url = new URL("https://lompat.app/v/1/");
            HttpURLConnection con = (HttpURLConnection) url.openConnection();
            con.setRequestMethod("POST");
            con.setRequestProperty("Content-Type", "application/json; utf-8");
            con.setDoOutput(true);

            try(OutputStream os = con.getOutputStream()) {
                byte[] input = data.getBytes(StandardCharsets.UTF_8);
                os.write(input, 0, input.length);
            }

            System.out.println(con.getResponseCode() + " " + con.getResponseMessage());
            con.disconnect();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

### Ruby

Using `net/http` to send a POST request:

```ruby
require 'net/http'
require 'uri'
require 'json'

uri = URI.parse("https://lompat.app/v/1/")
header = {'Content-Type': 'application/json'}
data = {email: 'lompat.user@lompat.app', key: 'your_api_key'}

http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
request = Net::HTTP::Post.new(uri.request_uri, header)
request.body = data.to_json

response = http.request(request)
puts response.body
```

### C#

Using `HttpClient` to send a POST request:

```csharp
using System;
using System.Net.Http;
using System.Text;
using System.Threading.Tasks;

public class Program
{
    public static async Task Main()
    {
        var url = "https://lompat.app/v/1/";
        var data = new StringContent("{\"email\":\"lompat.user@lompat.app\", \"key\":\"your_api_key\"}", Encoding.UTF8, "application/json");

        using (var httpClient = new HttpClient())
        {
            HttpResponseMessage response = await httpClient.PostAsync(url, data);
            string result = await response.Content.ReadAsStringAsync();
            Console.WriteLine(result);
        }
    }
}
```

### C++

Using `CURL` library to send a POST request (Note: Requires libcurl):

```cpp
#include <iostream>
#include <curl/curl.h>
#include <string>

int main() {
    CURL *curl;
    CURLcode res;
    std::string readBuffer;
    std::string data = "{\"email\":\"lompat.user@lompat.app\", \"key\":\"your_api_key\"}";

    curl = curl_easy_init();
    if(curl) {
        curl_easy_setopt(curl, CURLOPT_URL, "https://lompat.app/v/1/");
        curl_easy_setopt(curl, CURLOPT_POSTFIELDS, data.c_str());
        curl_easy_setopt(curl, CURLOPT_POSTFIELDSIZE, (long)data.size());

        res = curl_easy_perform(curl);
        if(res != CURLE_OK)
            fprintf(stderr, "curl_easy_perform() failed: %s\n", curl_easy_strerror(res));

        curl_easy_cleanup(curl);
    }
    return 0;
}
```

These examples provide practical guidance on integrating the Email Validation API into various applications, catering to a broad range of popular programming languages and frameworks.


## Need Help?

If you have any questions or need further assistance, please reach out to our support team at support@lompat.app.

We look forward to seeing what you'll build with our Email Validation API!
