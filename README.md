# Zazuu API Integration Guide

## Get started

You can consume the APIs directly using your favorite HTTP/REST library. We have a testing environment called sandbox, which you can contact [support@zazuu.co](mailto:support@zazuu.co) to sign up for test API calls without affecting live data.

# Authentication

When you sign up for an account we will send you a secret API key, you can authenticate with the Secret API keys. Unless explicitly stated, all endpoints require authentication using the Secret API Keys.

> All API queries must be made over HTTPS, and plain HTTP will be refused. You must include your `X-API-KEY` headers in all requests.

Example:

```json
{
	"headers" {
		"Content-Type": "application/json",
		"Accept": "application/json",
		"X-API-KEY": "ApiSecretKey"
	}
}
```

# Environment

Zazuu API is available in both Live as well as Test environments. It's important to note that the test environment is limited to testing purposes and deals with mock data while the live environment deals with live integrations and information.

| Environment | Base URL                                            |
| ----------- | --------------------------------------------------- |
| Sandbox     | contact [support@zazuu.co](mailto:support@zazuu.co) |
| Production  | contact [support@zazuu.co](mailto:support@zazuu.co) |

# API Reference

Contact [support@zazuu.co](mailto:support@zazuu.co) to have access to our full API reference

# Steps to initiating a transaction

## Step 1 - Activate a corridor

To activate the corridor you want to support:

- To activate a corridor

```
POST: /corridors/create
```

- Then see the list of corridors you're subscribed to:

```
GET: /corridors
```

> See API reference for API payload and response

## Step 2 - Get Fx Rates

To get the Fx Rates:

```
GET: /rates
```

> **NOTE**: You can add the query param `type=best_rate` to fetch the best Fx rate. This will return a single partner with the best Fx rate.

**_See API reference for API payload and response_**

## Step 3 - Subscribe to web hooks

- To subscribe to a web hook:

```
POST: /webhooks
```

- To see list of web hooks subscribed to:

```
GET: /webhooks
```

### List of events:

- transaction.initiated
- transaction.success
- transaction.failed
- transaction.cancelled
- transaction.processing
- transaction.refunded

> **NOTE**: Please acknowledge all webhooks with a 2xx response. A header property called `x-webhook-key`, containing your specified secret, is sent as part of all requests which you should use to verify the authenticity of the webhook. In cases of failed acknowledgements, Zazuu will resend webhooks on the hour for the next 24 hours (this can be further reduced), after which the webhook will be discarded. For events of type `transaction.failed`, if you have `enableSmartReroute` set to true for a corridor, we add an isFinal property, which can be true or false, to the data payload to let you know when are done rerouting a transaction and will no longer process.

**_See API reference for API payload and response_**

## Step 4 - Initiate a transaction

To activate the corridor you want to support:

- To activate a corridor:

```
POST: /transactions
```

- Then see the list of corridors you're subscribes to

```
GET: /transactions
```

- You can get a single transaction history:

```
GET: /transactions/{transactionId}
```

**_See API reference for API payload and response_**

## Reference data

### See list of available partners

```
GET: /partners/available
```

### Get supported banks by payout partner

```
POST: /payout-banks
```

### Validate mobile wallet

```
GET: /momo/validate
```

### Validate bank account

```
GET: /account/validate
```

**_See API reference for API payload and response_**
