## Zazuu API Integration Guide

## Get started

Zazuu provides a collection of APIs that enable you to process and manage transfers. Our APIs accept and return JSON in the HTTP body, and return standard HTTP response codes. You can consume the APIs directly using your favorite HTTP/REST library. We have a testing environment called sandbox, which you can contact support@zazuu.co to sign up for test API calls without affecting live data.

# Authentication

When you sign up for an account we will send you a secret API key, you can authenticate with the Secret API keys. Unless explicitly stated, all endpoints require authentication using the Secret API Keys.

> All API queries must be made over HTTPS, and plain HTTP will be refused. You must include your X-API-KEY headers in all requests.

Example:

```curl
curl --location --request POST 'https://..../transactions' \
--header 'Content-Type: application/json' \
--header 'Accept: application/json' \
--header 'X-API-KEY: {{ApiSecretKey}}' \
--data-raw '{
"destination": "ngn"
...
}'
```

# Environment

Zazuu API is available in both Live as well as Test environments. It's important to note that the test environment is limited to testing purposes and deals with mock data while the live environment deals with live integrations and information.

| Environment | Base URL                 |
| ----------- | ------------------------ |
| Sandbox     | contact support@zazuu.co |
| Production  | contact support@zazuu.co |

# API Reference

Contact support@zazuu.co to have access to our full API reference

# Steps to creating a transaction

## Step 1

You need to subscribe to a Payout Partner

1. To see the list of partners we support using: _**GET**_ `/partners/available`
2. Then subscribe to a partner using: _**POST**_ `/partners/subscribe`
3. Then you can see the list of subscribed partners using: _**GET**_ `/partners/list`
