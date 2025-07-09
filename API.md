# API Endpoints

## Base URL

```
https://api.getpayde.com/unipay/v1
```

All API requests must include a Merchant key in the request header:

```jsx
x-merchant: 98f41f81-xxxx-yyyy-zzzz-941882ab1144
```

Contact support to obtain your Merchant key. 

## POST /validate-merchant

Retrieve a list of supported cryptocurrencies and networks.

```json
GET /validate-merchant

Response:
{
    "company_name": "Tesco UK",
    "company_logo": "merchent_logo1",
    "fiat": "EUR",
    "crypto": [
        "USDT_TRX_T",
        "BTC_TEST",
        "ETH_TEST"
    ],
    "assets": [
        ...
        ]
}
```

## POST /estimate-amount

Retrieve an estimated value in a specified crypto currency.

```json
POST /estimate-amount
Request:
{
    "fiat": "EUR",
    "crypto": "ETH_TEST",
    "fiat_amount": 50
}

Response:
{
		"crypto_amount": 0.018
}
```

## POST /pay

Create an invoice (aka transaction) for this payment.

```json
POST /pay
Request:
{
    "fiat": "EUR",
    "crypto": "ETH_TEST",
    "fiat_amount": 50,
    "memo": "coffee",
    "webhook_url": "https://abc.com/server/webhook",
    "success_url": "https://abc.com/success_page.html",
    "failed_url": "https://abc.com/failed_page.html",
    "payer": {
	    "name": "John Paul",
	    "email": "john@yahoo.com",
	    "mobile": "1247862712"
    } 
}

Response:
{
    "inv_id": "8dd94fd9-03bf-4351-90fa-b026bbc648ea",
    "inv_status": "Pending",
    "address": "0x9FEd2b837863fb5CFf7E374Ae252657F8Ef20481",
    "address_tag": "",
    "crypto_amount": 0.0187
}
```

## GET /status/{inv_id}

Check status of an existing invoice.

```json
GET /status/81ae8b55-1c37-412c-bb97-24cad9b44134
Response:
{
    "inv_id": "81ae8b55-1c37-412c-bb97-24cad9b44134",
    "status": "Pending",
    "merchant": {
		    "id": "98f41f81-0048-11ee-8852-941882ab1144",
        "email": "ankit@finrock.io",
        "name": "Tesco UK",
        "logo": "https://s3api.payde.com/kyb/1_1_677e1184-3cbd-45f9-aa02-20a5c19a0943.png?AWSAccessKeyId=L7jSNP8TlTQwJhmcxrDx&Expires=1769157072&Signature=1jfhKyP7qFalyuWyscZfJ5z%2BTxA%3D"
    },
    "fiat": {
        "asset": "EUR",
        "amount": 10.00000000
    },
    "crypto": {
        "asset": "ETH_TEST",
        "ticker": "ETH",
        "blockchain": null,
        "network": "Ethereum (Testnet)",
        "amount": 0.0187,
        "received": 0.00000000,
        "unconfirmed": 0.00000000,    
			  "address": "0x16143fB5174481ACDb2b7cf20da1839aab968C81",
		    "address_tag": "",
    },
    "memo": "cofffee",
    "order_date": "2025-01-23T08:58:24Z",
    "expiry_date": "2025-01-23T09:28:24Z",
    "updated_on": null,
    "payer": {
	    "name": "John Paul",
	    "email": "john@yahoo.com",
	    "mobile": "1247862712"
    },
    "webhook_url": "https://abc.com/server/webhook",
    "success_url": "https://abc.com/success_page.html",
    "failed_url": "https://abc.com/failed_page.html",
}
```

# Example QR Code

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/fb90aa53-51b2-41cf-9244-b191eb4f370b/92ce8ec2-b3a4-40c9-914f-f3869849766b/image.png)

# Webhook Signature Validation

Setting up a Webhook will enable you to get notified of inward payments as they arrive and an invoice is marked as paid. 

```json
{
  "inv_id": "f1f002d9-5513-4583-a970-1656a63e6dac",
  "status": "Paid",
  "order_date": "2025-02-03T09:06:09Z",
  "expiry_date": "2025-02-03T09:36:09Z",
  "updated_on": "2025-02-03T09:11:21Z",
  "merchant": {
    "id": "26be782a-7a1b-4643-bf2c-eaf13fd97fbb",
    "email": "devvicky@mailinator.com",
    "name": "Acme INC.",
    "logo": "https://s3api.bloxeo.io/kyb/1_86_f58f0fa4-d610-49af-9002-dd7f077167a0.png?AWSAccessKeyId=L7jSNP8TlTQwJhmcxrDx&Expires=1770109872&Signature=HvozA5hFcf1PF6vMieS5%2FKnXABk%3D"
  },
  "fiat": {
    "asset": "EUR",
    "amount": 16
  },
  "crypto": {
    "asset": "USDT_SOL_T",
    "ticker": "USDT",
    "blockchain": "SOL",
    "network": "Solana (Devnet)",
    "address": "4k3NYKhCjirkRnRneroC5X9pubukLYkHWy8x7Fbuu1Lg",
    "address_tag": "",
    "amount": 17.96,
    "received": 17.96,
    "unconfirmed": 0,
    "txs": [
      {
        "crypto_amount": 17.96,
        "txn_date": "2025-02-03T09:11:21Z",
        "off_chain": false,
        "txn_hash": "5P9Lbt3VftUAhLLUf5x9w4BtKmL6J69upnar81BJZyVDtamTUMgqSQp72GzXsuq6WLuM3P2oBM9RxXn8pS6AvYm2",
        "explorer_url": "https://explorer.solana.com/tx/5P9Lbt3VftUAhLLUf5x9w4BtKmL6J69upnar81BJZyVDtamTUMgqSQp72GzXsuq6WLuM3P2oBM9RxXn8pS6AvYm2?cluster=devnet",
        "status": "Confirmed"
      }
    ]
  },
  "memo": "GSB5674",
  "payer": {
    "name": null,
    "email": null,
    "mobile": null
  },
  "webhook_url": null,
  "success_url": null,
  "failed_url": null
}
```

A POST request to the provided URL(s) expects a 200 response. If no response is received, we will resend the request at most 5 times with increasing delay between each attempt, the retry attempts will be taken after [30, 60, 90, 120, 180] seconds.

All events will be sent with an `x-signature` header containing an RSA-SHA512 signature of the Webhook payload. Your client application should verify the signature using our WEBHOOK_PUBLIC_KEY, which is appended below.

```jsx
const crypto = require("crypto");

var jsonPayload = 'WEBHOOK_JSON_BODY';
var signature = 'WEBHOOK_HEADER_X-SIGNATURE';
var publicKey = 'WEBHOOK_PUBLIC_KEY';

const isVerified = crypto.verify(
    "SHA512",
    Buffer.from(jsonPayload, "utf8"),
    {
        key: publicKey,
        padding: crypto.constants.RSA_PKCS1_PADDING,
    },
    Buffer.from(signature, "base64")
);

// isVerified should be `true` if the signature is valid
console.log("signature verified: ", isVerified);
```

### WEBHOOK_PUBLIC_KEY

```jsx
-----BEGIN PUBLIC KEY-----
MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDFRK50xuIXs3qeARwayhs8Wszb
Ydn7TldpzldZ7aSGIwCC84vAm1uZdwSn3q/bTC2VjBKp48Bykixa8CNq/DFBfsJA
VTWIt6Y4anFf+00a5xG5lWE1yNsMo/KynXy2aoekq1YtCZHEv1FvIng1rkuEfe6+
51q1Dipzkyx3rs+mdwIDAQAB
-----END PUBLIC KEY-----
```