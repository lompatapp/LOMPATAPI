# Lompat Email Validation API Documentation

Welcome to the Lompat Email Validation API, a comprehensive tool designed to enhance your email data quality through a series of validations, predictions, and checks. Our API covers a wide range of features from basic format checks to detailed analyses including domain age, provider type, and much more.

## Getting Started

1. **Get your API key**: Contact us to receive your unique API key necessary to access the API.
2. **Make a request**: Use the sample JSON requests above as a template. Customize the parameters according to your needs.
3. **Handle the response**: Implement logic in your application to handle and utilize the JSON data returned from the API.

## Pricing

Our Email Validation API is offered at a flat rate of **$55 per month**. This plan includes unlimited email validations, allowing you to check as many emails as needed without any additional charges. This pricing structure is designed to be simple and predictable, making it easy for businesses of all sizes to budget for their email validation needs.

### What's Included:

- **Unlimited Email Validations**: Validate as many emails as you need each month without worrying about per-email costs.
- **Full Access to All Features**: Enjoy access to all the features listed in our documentation, including basic validations, domain checks, and advanced analytics like domain age and social media presence verifications.
- **No Hidden Fees**: The monthly fee is all-inclusive. There are no setup fees or hidden charges.

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
- **Social Media Checks**: Validates presence on LinkedIn, Microsoft, and Twitter.

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

### LinkedIn Validation Request

To check if the email is associated with a LinkedIn account:

```json
{
  "email": "lompat.user@lompat.app",
  "linkedin": "true",
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

### Twitter Email Check

To verify if the email is valid for Twitter account:

```json
{
  "email": "lompat.user@lompat.app",
  "twitter": "true",
  "key": "your_api_key"
}
```

## Example Implementations

Here are some quick examples on how to use the Email Validation API with different programming languages and frameworks:

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

These examples provide practical guidance on integrating the Email Validation API into various applications, catering to a broad range of popular programming languages and frameworks.


## Need Help?

If you have any questions or need further assistance, please reach out to our support team at jhon@lompat.app.

We look forward to seeing what you'll build with our Email Validation API!
