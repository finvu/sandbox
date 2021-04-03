# FIU API (Simulator)

This is a simulator implementation of the FIU API and can be used for testing the Account Aggregator flows as part of the ecosystem. 

## API Request

The API URL to be used is `<Root API Endpoint>/<FIP API>` as per ReBIT FIP API Specs.

### Consent Notification

HTTP METHOD: `POST`

URL: `http://api.finvu.in/ConnectHub/FIU/API/V1/Consent/Notification`

Request Body

```
{
  "ver": "1.0",
  "timestamp": "2018-12-06T11:39:57.153Z",
  "txnid": "0b811819-9044-4856-b0ee-8c88035f8858",
  "Notifier": {
    "type": "AA",
    "id": "cookiejar-aa@devfinvu.in"
  },
  "ConsentStatusNotification": {
    "consentId": "dd186b2a-e838-441c-a72a-3d2b3c023120",
    "ConsentStatus": "READY"
  }
}
```
Response Expected: 
```
200 OK
```

### FI Notification


HTTP METHOD: `POST`

URL: `http://api.finvu.in/ConnectHub/FIU/API/V1/FI/Notification`

Request Body


```
{
  "ver": "1.0",
  "timestamp": "2018-12-06T11:39:57.153Z",
  "txnid": "0b811819-9044-4856-b0ee-8c88035f8858",
  "Notifier": {
    "type": "AA",
    "id": "cookiejar-aa@finvu.in"
  },
  "FIStatusNotification": {
    "sessionId": "XXXX0-XXXX-XXXX",
    "sessionStatus": "ACTIVE",
    "FIStatusResponse": [
      {
        "fipID": "FIP-1",
        "Accounts": [
          {
            "linkRefNumber": "XXXX-XXXX-XXXX",
            "FIStatus": "READY",
            "description": "ACTIVE"
          }
        ]
      }
    ]
  }
}
```
Response Expected: 
```
200 OK
```
