# Central Trust Store

This is a Central Trust Store for the Account Aggregator Ecosystem and is a prototype based on current ReBIT API defnition for the Central Trust Store.  

### Add New Entity (AA, FIP, FIU)

Below is the API for adding details on FIP, AA or FIU. 

Note: In case of AA and FIU currently fitypes needs to be provided when adding details, although it would be ignored when used.

HTTP METHOD: `POST`

URL: `//aactsuat.finvu.in/saveEntity/<Entity Type>`

e.g.: https://aactsuat.finvu.in/saveEntity/FIP

e.g.: https://aactsuat.finvu.in/saveEntity/AA

e.g.: https://aactsuat.finvu.in/saveEntity/FIU



Request Body

```
{
  "ver": "1.0",
  "timestamp": "2019-06-16T03:01:53.410Z",
  "txnid": "29ae-11e8-a8d7-0289",
  "requester": {
    "name": "Finvu",
    "id": "AA010001"
  },
  "entityinfo": {
    "name": "Cookiejar Technologies Private Limited",
    "id": "AA010001",
    "code": "CTPL",
    "baseurl": "https://aauat.finvu.in/API/V1",
    "fitypes": [
      "DEPOSIT","EQUITY"
    ],
    "certificate": {"keys":
       [
         {"kty":"EC",
          "crv":"P-256",
          "x":"MKBCTNIcKUSDii11ySs3526iDZ8AiTo7Tu6KPAqv7D4",
          "y":"4Etl6SRW2YiLUrN5vfvVHuhp7x8PxltmWWlbbM4IFyM",
          "use":"enc",
          "kid":"1"},

         {"kty":"RSA",
          "n": "0vx7agoebGcQSuuPiLJXZptN9nndrQmbXEps2aiAFbWhM78LhWx     4cbbfAAtVT86zwu1RK7aPFFxuhDR1L6tSoc_BJECPebWKRXjBZCiFV4n3oknjhMs     tn64tZ_2W-5JsGY4Hc5n9yBXArwl93lqt7_RN5w6Cf0h4QyQ5v-65YGjQR0_FDW2     QvzqY368QQMicAtaSqzs8KJZgnYb9c7d0zgdAZHzu6qMQvRL5hajrn1n91CbOpbI     SD08qNLyrdkt-bFTWhAI4vMQFh6WeZu0fM4lFd2NcRwr3XPksINHaQ-G_xBniIqb     w0Ls1jF44-csFCur-kEgU8awapJzKnqDKgw",
          "e":"AQAB",
          "alg":"RS256",
          "kid":"2011-04-29"}
       ]
     },
    "tokeninfo": {
      "url": "https://aauat.finvu.in/API/V1",
      "maxcalls": 1,
      "desc": "string"
    }
  }
}
```
Response Expected: 
```
Record save successfully with Entity Id AA
```

### Updating Entity (AA, FIP, FIU)

Below is the API for updating details on FIP, AA or FIU. 

HTTP METHOD: `PUT`

URL: `//aactsuat.finvu.in/saveEntity`

Request Body

```
{
  "ver": "1.0",
  "timestamp": "2019-06-16T03:01:53.410Z",
  "txnid": "29ae-11e8-a8d7-0289",
  "requester": {
    "name": "Finvu",
    "id": "AA010001"
  },
  "entityinfo": {
    "name": "Cookiejar Technologies Private Limited",
    "id": "AA010001",
    "code": "CTPL",
    "baseurl": "https://aauat.finvu.in/API/V1",
    "fitypes": [
      "DEPOSIT","EQUITY"
    ],
    "certificate": {"keys":
       [
         {"kty":"EC",
          "crv":"P-256",
          "x":"MKBCTNIcKUSDii11ySs3526iDZ8AiTo7Tu6KPAqv7D4",
          "y":"4Etl6SRW2YiLUrN5vfvVHuhp7x8PxltmWWlbbM4IFyM",
          "use":"enc",
          "kid":"1"},

         {"kty":"RSA",
          "n": "0vx7agoebGcQSuuPiLJXZptN9nndrQmbXEps2aiAFbWhM78LhWx     4cbbfAAtVT86zwu1RK7aPFFxuhDR1L6tSoc_BJECPebWKRXjBZCiFV4n3oknjhMs     tn64tZ_2W-5JsGY4Hc5n9yBXArwl93lqt7_RN5w6Cf0h4QyQ5v-65YGjQR0_FDW2     QvzqY368QQMicAtaSqzs8KJZgnYb9c7d0zgdAZHzu6qMQvRL5hajrn1n91CbOpbI     SD08qNLyrdkt-bFTWhAI4vMQFh6WeZu0fM4lFd2NcRwr3XPksINHaQ-G_xBniIqb     w0Ls1jF44-csFCur-kEgU8awapJzKnqDKgw",
          "e":"AQAB",
          "alg":"RS256",
          "kid":"2011-04-29"}
       ]
     },
    "tokeninfo": {
      "url": "https://aauat.finvu.in/API/V1",
      "maxcalls": 1,
      "desc": "string"
    }
  }
}
```
Response Expected: 
```
Record save successfully Modified with Entity Id :: AA010001
```


### Extracting Entity (AA, FIP, FIU)

HTTP METHOD: `GET`

URL: `//aactsuat.finvu.in/entityInfo/<Entity Type>/<Entity ID>`

e.g.
https://aactsuat.finvu.in/entityInfo/AA/AA010001


Response Expected: 
```
{
    "ver": "1.0",
    "timestamp": "2019-06-17T10:20:56.537+0000",
    "txnid": "ff8b7364-d507-4898-a2c1-66f23e5e9753",
    "requester": null,
    "entityinfo": {
        "name": "Cookiejar Technologies Private Limited",
        "id": "AA010001",
        "code": "CTPL",
        "baseurl": "https://aauat.finvu.in/API/V1",
        "fitypes": [
            "DEPOSIT",
            "EQUITY"
        ],
        "certificate": {
            "keys": [
                "{kty=EC, crv=P-256, x=MKBCTNIcKUSDii11ySs3526iDZ8AiTo7Tu6KPAqv7D4, y=4Etl6SRW2YiLUrN5vfvVHuhp7x8PxltmWWlbbM4IFyM, use=enc, kid=1}",
                "{kty=RSA, n=0vx7agoebGcQSuuPiLJXZptN9nndrQmbXEps2aiAFbWhM78LhWx     4cbbfAAtVT86zwu1RK7aPFFxuhDR1L6tSoc_BJECPebWKRXjBZCiFV4n3oknjhMs     tn64tZ_2W-5JsGY4Hc5n9yBXArwl93lqt7_RN5w6Cf0h4QyQ5v-65YGjQR0_FDW2     QvzqY368QQMicAtaSqzs8KJZgnYb9c7d0zgdAZHzu6qMQvRL5hajrn1n91CbOpbI     SD08qNLyrdkt-bFTWhAI4vMQFh6WeZu0fM4lFd2NcRwr3XPksINHaQ-G_xBniIqb     w0Ls1jF44-csFCur-kEgU8awapJzKnqDKgw, e=AQAB, alg=RS256, kid=2011-04-29}"
            ]
        },
        "tokeninfo": {
            "url": "https://aauat.finvu.in/API/V1",
            "maxcalls": 1,
            "desc": "string"
        }
    }
}
```


### Extracting Entity List (AA, FIP, FIU)

HTTP METHOD: `GET`

URL: `//aactsuat.finvu.in/entityInfo/<Entity Type>`

e.g. https://aactsuat.finvu.in/entityInfo/FIP

e.g. https://aactsuat.finvu.in/entityInfo/AA

e.g. https://aactsuat.finvu.in/entityInfo/FIU


Response Expected: 
```
[
    {
        "name": "Cookiejar Technologies Private Limited",
        "id": "AA010001",
        "code": "FINVUTPL",
        "baseurl": "https://finvu.in/API/V1",
        "fitypes": [
            "DEPOSIT",
            "EQUITY"
        ],
        "certificate": {
            "keys": [
                "{kty=EC, crv=P-256, x=MKBCTNIcKUSDii11ySs3526iDZ8AiTo7Tu6KPAqv7D4, y=4Etl6SRW2YiLUrN5vfvVHuhp7x8PxltmWWlbbM4IFyM, use=enc, kid=1}",
                "{kty=RSA, n=0vx7agoebGcQSuuPiLJXZptN9nndrQmbXEps2aiAFbWhM78LhWx     4cbbfAAtVT86zwu1RK7aPFFxuhDR1L6tSoc_BJECPebWKRXjBZCiFV4n3oknjhMs     tn64tZ_2W-5JsGY4Hc5n9yBXArwl93lqt7_RN5w6Cf0h4QyQ5v-65YGjQR0_FDW2     QvzqY368QQMicAtaSqzs8KJZgnYb9c7d0zgdAZHzu6qMQvRL5hajrn1n91CbOpbI     SD08qNLyrdkt-bFTWhAI4vMQFh6WeZu0fM4lFd2NcRwr3XPksINHaQ-G_xBniIqb     w0Ls1jF44-csFCur-kEgU8awapJzKnqDKgwz, e=AQAB, alg=RS256, kid=2011-04-29}"
            ]
        },
        "tokeninfo": {
            "url": "https://finvu.in/API/V1",
            "maxcalls": 1,
            "desc": "string"
        }
    },
    {
        "name": "Finvu Technologies Private Limited",
        "id": "AA010002",
        "code": "FINVUTPL",
        "baseurl": "https://finvu.in/API/V1",
        "fitypes": [
            "DEPOSIT",
            "EQUITY"
        ],
        "certificate": {
            "keys": [
                "{kty=EC, crv=P-256, x=MKBCTNIcKUSDii11ySs3526iDZ8AiTo7Tu6KPAqv7D4, y=4Etl6SRW2YiLUrN5vfvVHuhp7x8PxltmWWlbbM4IFyM, use=enc, kid=1}",
                "{kty=RSA, n=0vx7agoebGcQSuuPiLJXZptN9nndrQmbXEps2aiAFbWhM78LhWx     4cbbfAAtVT86zwu1RK7aPFFxuhDR1L6tSoc_BJECPebWKRXjBZCiFV4n3oknjhMs     tn64tZ_2W-5JsGY4Hc5n9yBXArwl93lqt7_RN5w6Cf0h4QyQ5v-65YGjQR0_FDW2     QvzqY368QQMicAtaSqzs8KJZgnYb9c7d0zgdAZHzu6qMQvRL5hajrn1n91CbOpbI     SD08qNLyrdkt-bFTWhAI4vMQFh6WeZu0fM4lFd2NcRwr3XPksINHaQ-G_xBniIqb     w0Ls1jF44-csFCur-kEgU8awapJzKnqDKgwz, e=AQAB, alg=RS256, kid=2011-04-29}"
            ]
        },
        "tokeninfo": {
            "url": "https://finvu.in/API/V1",
            "maxcalls": 1,
            "desc": "string"
        }
    }
]
```
