Welcome to the core-api-doc wiki!

Table of content

# Making a transfer

# Authentication

## Authentication

- Get API Key
- Contact support team support@zazuu.co

```json
  "headers": {
    "Content-Type": "application/json",
    "x-api-key": "<API-KEY>"
  }
```

## Step 2

- See list of partners available => GET /partners/available
- Then subscribe to a partner => GET /partners/subscribe
- Then you can see the list of subscribed partners => GET /partners/list

## Step 3

Activate the corridor you want to support

- /corridors/create
- See list of corridors with => /corridors

## Step 4

View rate with

- GET /rates

## Step 5 - Subscribe to web hooks

The events you can subscribe to are:

- transaction.initiated
- transaction.success
- transaction.failed
- transaction.cancelled
- transaction.processing
- transaction.refunded

> **_NOTE:_** Please acknowledge all webhooks with a 2xx response. A header property called x-webhook-key, containing your specified secret, is sent as part of all requests which you should use to verify the authenticity of the webhook. In cases of failed acknowledgements, Zazuu will resend webhooks on the hour for the next 24 hours (this can be further reduced), after which the webhook will be discarded. For events of type transaction.failed, if you have enableSmartReroute set to true for a corridor, we add an isFinal property, which can be true or false, to the data payload to let you know when are done rerouting a transaction and will no longer process.

## Step 6 - Initiate a transaction

- POST /transactions
- You can get transactions history GET /transactions
- You can get a single transaction history GET /transactions/transactionId

## Others

- Get supported banks by payout partner: POST /payout-banks
- Validate bank: POST /account/validate
- Validate momo: POST /momo/validate
