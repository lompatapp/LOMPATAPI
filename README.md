# LOMPAT Email Validation API Documentation

Welcome to the Email Validation API, a comprehensive tool designed to enhance your email data quality through a series of validations, predictions, and checks. Our API covers a wide range of features from basic format checks to detailed analyses including domain age, provider type, and much more.

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
- **Social Media Checks**: Validates presence on LinkedIn.

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

## Getting Started

1. **Get your API key**: Contact us to receive your unique API key necessary to access the API.
2. **Make a request**: Use the sample JSON requests above as a template. Customize the parameters according to your needs.
3. **Handle the response**: Implement logic in your application to handle and utilize the JSON data returned from the API.

## Need Help?

If you have any questions or need further assistance, please reach out to our support team at jhon@lompat.app.

We look forward to seeing what you'll build with our Email Validation API!
