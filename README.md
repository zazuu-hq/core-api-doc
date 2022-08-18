## Zazuu API Reference

## Get started

Zazuu provides a collection of APIs that enable you to process and manage transfers. Our APIs accept and return JSON in the HTTP body, and return standard HTTP response codes. You can consume the APIs directly using your favorite HTTP/REST library. We have a testing environment called sandbox, which you can contact support@zazuu.co to sign up for test API calls without affecting live data.

# Authentication

When you sign up for an account we will send you a secret API key, you can authenticate with the Secret API keys. Unless explicitly stated, all endpoints require authentication using the Secret API Keys.

## ApiSecretKey

```json
"headers": {
	"Content-Type": "application/json",
	"x-api-key": "ApiSecretKey"
}
```

# Environment

Zazuu API is available in both Live as well as Test environments. It's important to note that the test environment is limited to testing purposes and deals with mock data while the live environment deals with live integrations and information.

| Environment | Base URL                 |
| ----------- | ------------------------ |
| Sandbox     | contact support@zazuu.co |
| Production  | contact support@zazuu.co |
