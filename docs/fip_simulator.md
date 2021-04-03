# FIP API

This is a simulator implementation of the FIP API and can be used for testing the Account Aggregator flows as part of the ecosystem. 

## API Request

The API URL to be used is `<Root API Endpoint>/<FIP API>` as per ReBIT FIP API Specs.

### Account Discover

HTTP METHOD: `POST`

URL: `http://api.finvu.in/ConnectHub/V1/Accounts/discover`

## Request headers

Below `http` headers need to be set as part of each request

  |  Key          |   Value       |
  | ------------- |:-------------:|
  | `content-Type` | `application/json` |
  | `Accept` | `application/json` |
  | `aa_api_key`   | ```eyJraWQiOiJrZXlJZDEiLCJhbGciOiJSUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbG9jYWxob3N0OjgwODAvb3BlbmlkLWNvbm5lY3Qtc2VydmVyLXdlYmFwcC8iLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjkwOTAvQ29ubmVjdEh1Yi9WMS8iLCJleHAiOjE2MTMxMjM0NDAsImp0aSI6Ii11NmVNQXMxZGxpWGtPeWVYZGd3cmciLCJpYXQiOjE1ODE1ODc0NDAsIm5iZiI6MTU4MTU4NzM4MCwic3ViIjoibWFub2pAZmludnUuaW4ifQ.NlBDFmCh8SsX9T9eFZoiilfIkYObFpe57JQiSV-yc4Svt6AaHQFq3IT_0Z3I4880HixSvfcFCAUcP_meYguYk6Qp7YpTBMQ-S9j3ekcMnL-whDkR2dmChrgGI-ZaXtz-zlQXmfUNJiPKKJm8Ca68Bxi7lzvgF5YMxgz99m8Hj0ia1Ax3a468mo8JtvxelOrjYT-yVZDlH22Qo4INrdl3kIO_jDRB-AGQuq3095xjRciX-_zDK-a7_q_UyKRKjDnUjXkpiMzGfeilzfqMh-4PFfIXdQTF612QrSk7oZwF0XvqmjzQJYaGfPqdXtPcT3G7WDuS_YAdAQW5vIjAW96pXQ```      |
  | `x-jws-signature`   | ```eyJhbGciOiJSUzI1NiIsImtpZCI6ImY2NzZiNjg4LTA3YTItNDUwYi1hYmI1LTU3ZmJiOThlY2FiZSIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il19..jQMoIsNMjEd8cNKk2Fsktr3-RYT8D6elSGt-_hSxKjTkXNyIVh-Y0tPIZCi1Cs43dKs5apTKIwUZO4Gmpa7vFkfn0Idhv63B-lcaDY85Q4cZLcH34mIeu3M9j6Pi1wU3rS76kjJJfDu91QZLfFpxgRDg4PTw8CfVyt4doxcuV3bqIUfbAJo3y38li3VSW4HDK4uA8Pnt0oQmmUSL-vpI49NYC627VbSAcl4VY-QpGmmHRbYHwMs3XXbSeRGtAXkjIPEr9A6n2olPHwFRX_lVFLQqx8iiZAHjJVXg4-6llErpklx2ydrkTQJaYtecEv88BPur6mOFgo55pEa6bZnrmg```      |


Request Body


```
    {
      "ver": "1.0",
      "timestamp": "2019-04-29T04:04:44.955Z",
      "txnid": "8399263c-4a15-11e8-bcd1-0277a9fbfedc",
      "Customer": {
        "id": "jay@finvu",
        "Identifiers": [
          {
      "category": "STRONG",
      "type": "MOBILE",
      "value": "8600045504"
          }
        ]
      },
       "FITypes": [
        "DEPOSIT"
      ]
    }
```
Response Expected: 
```
    {
        "ver": "1.0",
        "timestamp": "2020-04-07T06:27:11.243+0000",
        "txnid": "8399263c-4a15-11e8-bcd1-0277a9fbfedc",
        "DiscoveredAccounts": [
      {
          "FIType": "RECURRING_DEPOSIT",
          "accType": "DEFAULT",
          "accRefNumber": "00001222",
          "maskedAccNumber": "XXXXXXXX3833"
      },
      {
          "FIType": "TERM-DEPOSIT",
          "accType": "DEFAULT",
          "accRefNumber": "03948856668067",
          "maskedAccNumber": "XXXXXXXXX8067"
      },
      {
          "FIType": "DEPOSIT",
          "accType": "CURRENT",
          "accRefNumber": "03948856668800",
          "maskedAccNumber": "XXXXXXXXX8000"
      },
      {
          "FIType": "DEPOSIT",
          "accType": "SAVINGS",
          "accRefNumber": "REF0009090",
          "maskedAccNumber": "XXXXXX9090"
      }
        ]
    }
```

### Account Linking

For simulation purpose, the customer account authentication is TOKEN based and an OTP is sent to the mobile no of the account holder. 

HTTP METHOD: `POST`

URL: `http://api.finvu.in/ConnectHub/V1/Accounts/link`

## Request headers

Below `http` headers need to be set as part of each request

  |  Key          |   Value       |
  | ------------- |:-------------:|
  | `content-Type` | `application/json` |
  | `Accept` | `application/json` |
  | `aa_api_key`   | ```eyJraWQiOiJrZXlJZDEiLCJhbGciOiJSUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbG9jYWxob3N0OjgwODAvb3BlbmlkLWNvbm5lY3Qtc2VydmVyLXdlYmFwcC8iLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjkwOTAvQ29ubmVjdEh1Yi9WMS8iLCJleHAiOjE2MTMxMjM0NDAsImp0aSI6Ii11NmVNQXMxZGxpWGtPeWVYZGd3cmciLCJpYXQiOjE1ODE1ODc0NDAsIm5iZiI6MTU4MTU4NzM4MCwic3ViIjoibWFub2pAZmludnUuaW4ifQ.NlBDFmCh8SsX9T9eFZoiilfIkYObFpe57JQiSV-yc4Svt6AaHQFq3IT_0Z3I4880HixSvfcFCAUcP_meYguYk6Qp7YpTBMQ-S9j3ekcMnL-whDkR2dmChrgGI-ZaXtz-zlQXmfUNJiPKKJm8Ca68Bxi7lzvgF5YMxgz99m8Hj0ia1Ax3a468mo8JtvxelOrjYT-yVZDlH22Qo4INrdl3kIO_jDRB-AGQuq3095xjRciX-_zDK-a7_q_UyKRKjDnUjXkpiMzGfeilzfqMh-4PFfIXdQTF612QrSk7oZwF0XvqmjzQJYaGfPqdXtPcT3G7WDuS_YAdAQW5vIjAW96pXQ```      |
  | `x-jws-signature`   | ```eyJhbGciOiJSUzI1NiIsImtpZCI6ImY2NzZiNjg4LTA3YTItNDUwYi1hYmI1LTU3ZmJiOThlY2FiZSIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il19..M2PpsHVPtxD07C93NR_8yzYBCO2REO-7YHbdEoDlsIDE36-6J6DkYKiC-2o86ykn7oGls8g8FYKPVMU7NdcIos0eAdK-Z4uAhnGcGB5XpleMCLJL7KJFpXbCeo2Nn2zRAO07p0jjr4vQNaVqXo4rKNQzHdtjhvVAeV5M7fUYHPVai3ghTrbuSChh4G12xDXq6pAexDnxWKiDdqamiqyRj9856h1aCkbKy6d3rm3xweqPjkUR3tMzQZzCNzlYTO1DFGn6xo6nIH_OlbUMYumqzkc6xJu7gTWriDh_gplsvrhN8TnzM7r3SK0nSyFHwuALCxShCOIZPw8_ep7plRjRtA```      |

Request Body


```
    {
      "ver": "1.0",
      "timestamp": "2018-05-09T17:51:18.412Z",
      "txnid": "f35761ac-4a18-11e8-96ff-0277a9fbfedc",
      "Customer": {
        "id": "jay@finvu",
        "Accounts": [
    
           {
          "FIType": "DEPOSIT",
          "accType": "CURRENT",
          "accRefNumber": "03948856668800",
          "maskedAccNumber": "XXXXXXXXX8000"
      }
        ]
      }
    }
```
Response Expected: 
```
    {
        "ver": "1.0",
        "timestamp": "2020-04-07T06:29:53.676+0000",
        "txnid": "f35761ac-4a18-11e8-96ff-0277a9fbfedc",
        "AuthenticatorType": "TOKEN",
        "RefNumber": "f455409f-6d06-4c8a-ac5a-34c6d78d467a"
    }
```

### Account Unlinking

For simulation purpose, The method is used to delete a previously established account linkage to the user’s profile. 

HTTP METHOD: `DELETE`

URL: `http://api.finvu.in/ConnectHub/V1/Accounts/link`

## Request headers

Below `http` headers need to be set as part of each request

  |  Key          |   Value       |
  | ------------- |:-------------:|
  | `content-Type` | `application/json` |
  | `Accept` | `application/json` |
  | `aa_api_key`   | ```eyJraWQiOiJrZXlJZDEiLCJhbGciOiJSUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbG9jYWxob3N0OjgwODAvb3BlbmlkLWNvbm5lY3Qtc2VydmVyLXdlYmFwcC8iLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjkwOTAvQ29ubmVjdEh1Yi9WMS8iLCJleHAiOjE2MTMxMjM0NDAsImp0aSI6Ii11NmVNQXMxZGxpWGtPeWVYZGd3cmciLCJpYXQiOjE1ODE1ODc0NDAsIm5iZiI6MTU4MTU4NzM4MCwic3ViIjoibWFub2pAZmludnUuaW4ifQ.NlBDFmCh8SsX9T9eFZoiilfIkYObFpe57JQiSV-yc4Svt6AaHQFq3IT_0Z3I4880HixSvfcFCAUcP_meYguYk6Qp7YpTBMQ-S9j3ekcMnL-whDkR2dmChrgGI-ZaXtz-zlQXmfUNJiPKKJm8Ca68Bxi7lzvgF5YMxgz99m8Hj0ia1Ax3a468mo8JtvxelOrjYT-yVZDlH22Qo4INrdl3kIO_jDRB-AGQuq3095xjRciX-_zDK-a7_q_UyKRKjDnUjXkpiMzGfeilzfqMh-4PFfIXdQTF612QrSk7oZwF0XvqmjzQJYaGfPqdXtPcT3G7WDuS_YAdAQW5vIjAW96pXQ```      |
  | `x-jws-signature`   | ```eyJhbGciOiJSUzI1NiIsImtpZCI6ImY2NzZiNjg4LTA3YTItNDUwYi1hYmI1LTU3ZmJiOThlY2FiZSIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il19..VWuBoCL0FUiq5_p_v12jP63n6VPFH7qnjOEO7wPa--Ft9n6GhDaQlP-gU7zutLiY7xYQC_WzSrYo0Ev77xoQ7gz9VCLS9pSebJImBtSH0NvWis7Q9aazB85cVekf9pfgmm0Y2o6ZNcVnNDj9mawQzU_eDKDDONaiNwg_abK9K3_dJ4bqfCWUCRTF9Sf0wRNPxafwhXZzz1GL56Asubk1O1vL5wL_DMqij377F8rGf1S4EBgfiQ8SM6dWwdRP-XB4lYymFFdKM6lbYn-cUD7ztHJAtqAhT0EDkqQs4cbLayWDFVo8uGyJ4dO6hTAx8eSfA9-Xcn4YSZFRa1onnBMOtg```      |

Request Body

```
      {
          "ver": "1.0",
          "timestamp": "2020-04-08T04:32:48.875+0000",
          "txnid": "39081877-b011-4c79-9255-f1d41bbb7f55",
          "Account": {
        "customerAddress": "jay@finvu",
        "linkRefNumber": "03948856668800"
          }
      }
```
Response Expected: 
```
    {
        "ver": "1.0",
        "timestamp": "2020-04-08T04:32:48.875+0000",
        "txnid": "39081877-b011-4c79-9255-f1d41bbb7f55",
        "AccLinkDetails": {
      "customerAddress": "jay@finvu",
      "linkRefNumber": "03948856668800",
      "status": "DELINKED"
        }
    }
```


### Account Confirm Token

HTTP METHOD: `GET`

URL: `http://api.finvu.in/ConnectHub/V1/Accounts/link/{RefNumber}/{Token}`

e.g. : http://api.finvu.in/ConnectHub/V1/Accounts/link/f455409f-6d06-4c8a-ac5a-34c6d78d467a/939504

## Request headers

Below `http` headers need to be set as part of each request

  |  Key          |   Value       |
  | ------------- |:-------------:|
  | `content-Type` | `application/json` |
  | `Accept` | `application/json` |
  | `aa_api_key`   | ```eyJraWQiOiJrZXlJZDEiLCJhbGciOiJSUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbG9jYWxob3N0OjgwODAvb3BlbmlkLWNvbm5lY3Qtc2VydmVyLXdlYmFwcC8iLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjkwOTAvQ29ubmVjdEh1Yi9WMS8iLCJleHAiOjE2MTMxMjM0NDAsImp0aSI6Ii11NmVNQXMxZGxpWGtPeWVYZGd3cmciLCJpYXQiOjE1ODE1ODc0NDAsIm5iZiI6MTU4MTU4NzM4MCwic3ViIjoibWFub2pAZmludnUuaW4ifQ.NlBDFmCh8SsX9T9eFZoiilfIkYObFpe57JQiSV-yc4Svt6AaHQFq3IT_0Z3I4880HixSvfcFCAUcP_meYguYk6Qp7YpTBMQ-S9j3ekcMnL-whDkR2dmChrgGI-ZaXtz-zlQXmfUNJiPKKJm8Ca68Bxi7lzvgF5YMxgz99m8Hj0ia1Ax3a468mo8JtvxelOrjYT-yVZDlH22Qo4INrdl3kIO_jDRB-AGQuq3095xjRciX-_zDK-a7_q_UyKRKjDnUjXkpiMzGfeilzfqMh-4PFfIXdQTF612QrSk7oZwF0XvqmjzQJYaGfPqdXtPcT3G7WDuS_YAdAQW5vIjAW96pXQ```      |
  | `x-jws-signature`   | ```eyJhbGciOiJSUzI1NiIsImtpZCI6ImY2NzZiNjg4LTA3YTItNDUwYi1hYmI1LTU3ZmJiOThlY2FiZSIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il19..Ql48ozk3SHTLSFJd445BDo4CcWr9V_V3zcaTJxaBh9kPAtKq-EgyDsECDdG8hlKFU-tzTILBJQ4XWgk4Oqw6zcFO5O8CUueagsXZfBLc9CXfc_YCVm3Zl09afrw7-joYRAjDoyDa5iLKJ-zikuzjkpXPP3V8IIFt3ez1OEDKQkGO1HyBtismuHd__myGZizx1wmeLOtPZfYZ-7gMHW_ImDNa-I9vl0Gf7XQYi2MDF9zvWDnv68mDH1e03pHl4OtoAZCDAAdm7nHtTgxVimGxxY_WtcwcSQ0i9NMU0xPeZ6Tnljo7eb4zrqRHkaF0kIVdK6kOS8MiolH4liuL39l92w```      |

Request Body
  
Put the SMS received on mobile in <token>{OTP sms}</token>
 

```
e.g.
http://api.finvu.in/ConnectHub/V1/Accounts/link/9d4dd3b3-7510-401a-b148-a79f03ac01d9/689612
```
Response Expected: 
```
    {
        "ver": "1.0",
        "timestamp": "2020-04-07T06:54:40.480+0000",
        "txnid": "f35761ac-4a18-11e8-96ff-0277a9fbfedc",
        "AccLinkDetails": [
      {
          "customerAddress": "jay@finvu",
          "linkRefNumber": "03948856668800",
          "accRefNumber": "03948856668800",
          "status": "LINKED"
      }
        ]
    }
```

### FI request

HTTP METHOD: `POST`

URL: `http://api.finvu.in/ConnectHub/V1/FI/request`

## Request headers

Below `http` headers need to be set as part of each request

  |  Key          |   Value       |
  | ------------- |:-------------:|
  | `content-Type` | `application/json` |
  | `Accept` | `application/json` |
  | `aa_api_key`   | ```eyJraWQiOiJrZXlJZDEiLCJhbGciOiJSUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbG9jYWxob3N0OjgwODAvb3BlbmlkLWNvbm5lY3Qtc2VydmVyLXdlYmFwcC8iLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjkwOTAvQ29ubmVjdEh1Yi9WMS8iLCJleHAiOjE2MTMxMjM0NDAsImp0aSI6Ii11NmVNQXMxZGxpWGtPeWVYZGd3cmciLCJpYXQiOjE1ODE1ODc0NDAsIm5iZiI6MTU4MTU4NzM4MCwic3ViIjoibWFub2pAZmludnUuaW4ifQ.NlBDFmCh8SsX9T9eFZoiilfIkYObFpe57JQiSV-yc4Svt6AaHQFq3IT_0Z3I4880HixSvfcFCAUcP_meYguYk6Qp7YpTBMQ-S9j3ekcMnL-whDkR2dmChrgGI-ZaXtz-zlQXmfUNJiPKKJm8Ca68Bxi7lzvgF5YMxgz99m8Hj0ia1Ax3a468mo8JtvxelOrjYT-yVZDlH22Qo4INrdl3kIO_jDRB-AGQuq3095xjRciX-_zDK-a7_q_UyKRKjDnUjXkpiMzGfeilzfqMh-4PFfIXdQTF612QrSk7oZwF0XvqmjzQJYaGfPqdXtPcT3G7WDuS_YAdAQW5vIjAW96pXQ```      |
  | `x-jws-signature`   | ```eyJhbGciOiJSUzI1NiIsImtpZCI6ImY2NzZiNjg4LTA3YTItNDUwYi1hYmI1LTU3ZmJiOThlY2FiZSIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il19..oS6xL_CyLpxbETG5fz19CzAOYMWqswInpfzHpByh5vzGUcnLzVt649rjw_hH0af_KdnDrSaDHVns1ljZyrXGYac9aAuF06fzjR4vTTdWmVdhOZUBmeNSw5vbYqSeVoE5I7q3NnE22BT3x1De5UahCdqhDVkJbE7JZb5mnUxVAlnbu2MPfNGQcotVL3_Awv83h5Q_4pf0qtioBhCSKBZOKjUKyP1ty3owY50xUdSmcIlwkWuKesUJujl1NQW8BplO4ZMnOHwLjlezJwOlSZUgSXA9dN2_z5Ftm0CsWdt6HTFRmvFoukndQAfBu__q3BGMaD--R6aXyCiuknCcW6Kk3g```      |

Request Body
 

```
    {
        "ver": "1.0",
        "timestamp": "2020-04-07T07:14:37.217+0000",
        "txnid": "50aabff2-0278-4840-b338-845e9f4d9955",
        "FIDataRange": {
      "from": "2020-04-07T07:14:37.183+0000",
      "to": "2021-04-06T07:14:16.676+0000"
        },
        "Consent": {
      "id": "2503a18c-c7f2-4112-9830-44cc63e91252",
      "digitalSignature": "d8umo2BKiMtRSceTPqsQW0VTzyeysjw0Czn5V89QMVTu1M9XF1VQ7OX8DSfC9NQC_Ktuf4R3I5qubozsGS161xsh0YuT-uFRktj4fM1eAHq0xGWN2ubn1yXZclyd8hEGSGqI8xybZfyZvqt3E7L_JlrCbwkqgt8QWgQWhen00syxVgdTZdAEUN3rabmi5Po4qRFPzHR7uYVrcJPwpHVq7hHsosUMjp-zGii0uNKKwLgu22p0LgqHYyte8hEDpm2RsJci3sXy56XRtgfERuBpkKTBcPB9LR6bA0t0LfPAChhWjw3-_kfEokLo-2LEGjSIUBevBb485ENYXKCGbw_5jg"
        },
        "KeyMaterial": {
      "cryptoAlg": "ECDH",
      "curve": "Curve25519",
      "params": "params",
      "DHPublicKey": {
          "expiry": "2021-04-06T07:14:16.676+0000",
          "Parameters": "params",
          "KeyValue": "-----BEGIN PUBLIC KEY-----MIIBMTCB6gYHKoZIzj0CATCB3gIBATArBgcqhkjOPQEBAiB/////////////////////////////////////////7TBEBCAqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqYSRShRAQge0Je0Je0Je0Je0Je0Je0Je0Je0Je0Je0JgtenHcQyGQEQQQqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqq0kWiCuGaG4oIa04B7dLHdI0UySPU1+bXxhsinpxaJ+ztPZAiAQAAAAAAAAAAAAAAAAAAAAFN753qL3nNZYEmMaXPXT7QIBCANCAAQehfHbuun4dqgOlSB6lrWPwVQnncfOaAMR/kKyeDobDkILMYJmfMBA4L2fj/uFA7IU+4HmwL/QjhiT2bmMw6Ht-----END PUBLIC KEY-----"
      },
      "Nonce": "UzU4ashLJj3FAYKVeb3wmMoHqn+eo98uS1tUq10RNrs="
        }
    }
```
Response Expected: 

```
  {
      "ver": "1.0",
      "timestamp": "2020-04-07T07:17:16.579+0000",
      "txnid": "50aabff2-0278-4840-b338-845e9f4d9955",
      "consentId": "2503a18c-c7f2-4112-9830-44cc63e91252",
      "sessionId": "931d1d33-e332-4ee2-b780-020d43ba69fd"
  }
```

### FI Fetch

HTTP METHOD: `GET`

URL: `http://api.finvu.in/ConnectHub/V1/FI/fetch/{SessionID}`
e.g. : http://api.finvu.in/ConnectHub/V1/FI/fetch/931d1d33-e332-4ee2-b780-020d43ba69fd

## Request headers

Below `http` headers need to be set as part of each request

  |  Key          |   Value       |
  | ------------- |:-------------:|
  | `content-Type` | `application/json` |
  | `Accept` | `application/json` |
  | `aa_api_key`   | ```eyJraWQiOiJrZXlJZDEiLCJhbGciOiJSUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbG9jYWxob3N0OjgwODAvb3BlbmlkLWNvbm5lY3Qtc2VydmVyLXdlYmFwcC8iLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjkwOTAvQ29ubmVjdEh1Yi9WMS8iLCJleHAiOjE2MTMxMjM0NDAsImp0aSI6Ii11NmVNQXMxZGxpWGtPeWVYZGd3cmciLCJpYXQiOjE1ODE1ODc0NDAsIm5iZiI6MTU4MTU4NzM4MCwic3ViIjoibWFub2pAZmludnUuaW4ifQ.NlBDFmCh8SsX9T9eFZoiilfIkYObFpe57JQiSV-yc4Svt6AaHQFq3IT_0Z3I4880HixSvfcFCAUcP_meYguYk6Qp7YpTBMQ-S9j3ekcMnL-whDkR2dmChrgGI-ZaXtz-zlQXmfUNJiPKKJm8Ca68Bxi7lzvgF5YMxgz99m8Hj0ia1Ax3a468mo8JtvxelOrjYT-yVZDlH22Qo4INrdl3kIO_jDRB-AGQuq3095xjRciX-_zDK-a7_q_UyKRKjDnUjXkpiMzGfeilzfqMh-4PFfIXdQTF612QrSk7oZwF0XvqmjzQJYaGfPqdXtPcT3G7WDuS_YAdAQW5vIjAW96pXQ```      |
  | `x-jws-signature`   | ```eyJhbGciOiJSUzI1NiIsImtpZCI6ImY2NzZiNjg4LTA3YTItNDUwYi1hYmI1LTU3ZmJiOThlY2FiZSIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il19..e1u2OaOBDRzlCDQE58320TQfwlP3Lw027FoCysaq8d4YduXtCkyBkgsSSMq45-E5dkldG9LT2rLoMKQRol3VKSv6LE93IN1wpbJmfezdCekGStHEFO5fNDylsHhq9IJs3bgt5EXvCbVqUQMwXy3SeEumqpH8sYtSzcUsj_R4wEn9ynhllUOKNEQHt2fpTl6BKr9JQOwJ5nlRSz3Rv-AJs-Bm2lkgg4_IlM1zj9Opdu7sMAtUH0f0wJOehy1gkdlxSqVkNtJI1EIKGsDpqm9xjFrOSfpdwbkAe2E0Nnp_J_Fs_eagNQLf_4Ji99ukAue24L5x88S0n1xx7vGEX8pSuA```      |


Response Expected: 

```
    {
        "ver": "1.0",
        "timestamp": "2020-04-07T07:24:09.185+0000",
        "txnid": "50aabff2-0278-4840-b338-845e9f4d9955",
        "FI": [
      {
          "fipID": "BARB0KIMXXX",
          "data": [
        {
            "linkRefNumber": "03948856668800",
            "maskedAccNumber": "XXXXXXXXX8000",
            "encryptedFI": "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"
        }
          ],
          "KeyMaterial": {
        "cryptoAlg": "ECDH",
        "curve": "Curve25519",
        "params": "None",
        "DHPublicKey": {
            "expiry": "2020-04-08T07:24:09.185+0000",
            "Parameters": null,
            "KeyValue": "-----BEGIN PUBLIC KEY-----MIIBMTCB6gYHKoZIzj0CATCB3gIBATArBgcqhkjOPQEBAiB/////////////////////////////////////////7TBEBCAqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqYSRShRAQge0Je0Je0Je0Je0Je0Je0Je0Je0Je0Je0JgtenHcQyGQEQQQqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqqq0kWiCuGaG4oIa04B7dLHdI0UySPU1+bXxhsinpxaJ+ztPZAiAQAAAAAAAAAAAAAAAAAAAAFN753qL3nNZYEmMaXPXT7QIBCANCAAR9JhxPpdggmkojZFrmTXiUabn9BWEBsxQpf4/93DUJM17b61y0tNqMOaCv+M3CkxxZ+blt6Bx4ByPpHkIOLoQ1-----END PUBLIC KEY-----"
        },
        "Nonce": "L33ZJco/0mvJOrgSVfd59p5ftsn21QWtAUELoKSUXkQ="
          }
      }
        ]
    }
```

### Consent Notifications

HTTP METHOD: `POST`

URL: `http://api.finvu.in/ConnectHub/V1/Consent/Notification`

## Request headers

Below `http` headers need to be set as part of each request

  |  Key          |   Value       |
  | ------------- |:-------------:|
  | `content-Type` | `application/json` |
  | `Accept` | `application/json` |
  | `aa_api_key`   | ```eyJraWQiOiJrZXlJZDEiLCJhbGciOiJSUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbG9jYWxob3N0OjgwODAvb3BlbmlkLWNvbm5lY3Qtc2VydmVyLXdlYmFwcC8iLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjkwOTAvQ29ubmVjdEh1Yi9WMS8iLCJleHAiOjE2MTMxMjM0NDAsImp0aSI6Ii11NmVNQXMxZGxpWGtPeWVYZGd3cmciLCJpYXQiOjE1ODE1ODc0NDAsIm5iZiI6MTU4MTU4NzM4MCwic3ViIjoibWFub2pAZmludnUuaW4ifQ.NlBDFmCh8SsX9T9eFZoiilfIkYObFpe57JQiSV-yc4Svt6AaHQFq3IT_0Z3I4880HixSvfcFCAUcP_meYguYk6Qp7YpTBMQ-S9j3ekcMnL-whDkR2dmChrgGI-ZaXtz-zlQXmfUNJiPKKJm8Ca68Bxi7lzvgF5YMxgz99m8Hj0ia1Ax3a468mo8JtvxelOrjYT-yVZDlH22Qo4INrdl3kIO_jDRB-AGQuq3095xjRciX-_zDK-a7_q_UyKRKjDnUjXkpiMzGfeilzfqMh-4PFfIXdQTF612QrSk7oZwF0XvqmjzQJYaGfPqdXtPcT3G7WDuS_YAdAQW5vIjAW96pXQ```      |
  | `x-jws-signature`   | ```eyJhbGciOiJSUzI1NiIsImtpZCI6ImY2NzZiNjg4LTA3YTItNDUwYi1hYmI1LTU3ZmJiOThlY2FiZSIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il19..Ye5-zRpQ5et1zydpTETMKp7kbyHhx_dOAOSYCWqHjXhxh6rm-ZpbIT4--6JKroLc_F9Juk6jhuV1vuE1hXv6-ii08c7zmuWS3dCduivvxlEmDLMaqX-sND1sWdrNh8IBmnDRnm3eszRGegVM1q7JjpsFs6XfRjjSkb-nNIoSjOTQmxA4V5KUMpPE2GIEYeiPikLkeRUAsNKklIyx_FiZDdQhHv-a5n3wncAguuDN0x6JzZO-YXQVktcEpzUGusfiDZeCOZtG3CpPOas9elBhWVbpQAcYxOQEkNgquGPtknx9wcBNTdWZgRou0_iBgtfRKRBiENKf-OKjKZIek6rpfg```      |

Request Body

```
      {
          "ver": "1.0",
          "timestamp": "2020-04-07T09:23:33.744+0000",
          "txnid": "f4a7674d-9f0c-4840-a3eb-45e7b9af0fc1",
          "Notifier": {
        "type": "AA",
        "id": "cookiejar-aa@finvu.in"
          },
          "ConsentStatusNotification": {
        "consentId": "264a3946-2c16-44cb-bcc2-6503d624d68d",
        "consentStatus": "REVOKED"
          }
      }
```

Response Expected: 

```
200 OK
```
### Consent 

HTTP METHOD: `POST`

URL: `http://api.finvu.in/ConnectHub/V1/Consent`

## Request headers

Below `http` headers need to be set as part of each request

  |  Key          |   Value       |
  | ------------- |:-------------:|
  | `content-Type` | `application/json` |
  | `Accept` | `application/json` |
  | `aa_api_key`   | ```eyJraWQiOiJrZXlJZDEiLCJhbGciOiJSUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbG9jYWxob3N0OjgwODAvb3BlbmlkLWNvbm5lY3Qtc2VydmVyLXdlYmFwcC8iLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjkwOTAvQ29ubmVjdEh1Yi9WMS8iLCJleHAiOjE2MTMxMjM0NDAsImp0aSI6Ii11NmVNQXMxZGxpWGtPeWVYZGd3cmciLCJpYXQiOjE1ODE1ODc0NDAsIm5iZiI6MTU4MTU4NzM4MCwic3ViIjoibWFub2pAZmludnUuaW4ifQ.NlBDFmCh8SsX9T9eFZoiilfIkYObFpe57JQiSV-yc4Svt6AaHQFq3IT_0Z3I4880HixSvfcFCAUcP_meYguYk6Qp7YpTBMQ-S9j3ekcMnL-whDkR2dmChrgGI-ZaXtz-zlQXmfUNJiPKKJm8Ca68Bxi7lzvgF5YMxgz99m8Hj0ia1Ax3a468mo8JtvxelOrjYT-yVZDlH22Qo4INrdl3kIO_jDRB-AGQuq3095xjRciX-_zDK-a7_q_UyKRKjDnUjXkpiMzGfeilzfqMh-4PFfIXdQTF612QrSk7oZwF0XvqmjzQJYaGfPqdXtPcT3G7WDuS_YAdAQW5vIjAW96pXQ```      |
  | `x-jws-signature`   | ```eyJhbGciOiJSUzI1NiIsImtpZCI6ImY2NzZiNjg4LTA3YTItNDUwYi1hYmI1LTU3ZmJiOThlY2FiZSIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il19..CICFu3GS_eDrzBvvfuudi2AJ1cLI1bObtfdEKKV5YU9bct9hZr0BuWSNeg4mRDfg1y2XTQZuCuEv3tyPT_d9mSFc6v0Rz6QRdxC3WV83lDnEEcxW0kwKG01fM0WMZS3YXQGcqteejDLA6KBQD_fXRg40LiyPZXKe6uXAqSpBkHCajPrN3h7ViecnbTIbYQRxlKRCba8M-zOicUMUT0-iNHJQ5psVElQvWSH2DL3gkqxVdUXRAuVSvOXverkRK-qcgmUe2Rn59d_Zw6KttiwDDuFyw-aykMEehmgeP5grKWx4KU0oif-yyOU7-kOMTmN7zsD_XJVrL4eqoulMr54AxQ```      |


Request Body

```
    {
        "ver": "1.0",
        "txnid": "0428ae6e-43b5-421e-9042-a532ced2f66d",
        "consentId": "1c79f3ba-ec2e-4d8b-8a43-8c4190fcad92",
        "status": "ACTIVE",
        "createTimestamp": "2020-04-07T07:09:45.670+0000",
        "signedConsent": "eyJhbGciOiJSUzI1NiIsImtpZCI6ImY2NzZiNjg4LTA3YTItNDUwYi1hYmI1LTU3ZmJiOThlY2FiZSIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il19.eyJjb25zZW50U3RhcnQiOjE1ODYyNDMzNzg4NzcsImNvbnNlbnRFeHBpcnkiOjE2MTc2OTI5NzY0NjYsImNvbnNlbnRNb2RlIjoiVklFVyIsImZldGNoVHlwZSI6IlBFUklPRElDIiwiY29uc2VudFR5cGVzIjpbIlNVTU1BUlkiLCJUUkFOU0FDVElPTlMiLCJQUk9GSUxFIl0sImZpVHlwZXMiOlsiREVQT1NJVCIsIlRFUk0tREVQT1NJVCJdLCJEYXRhQ29uc3VtZXIiOnsiaWQiOiJjb29raWVqYXItYWFAZmludnUuaW4iLCJ0eXBlIjoiQUEifSwiRGF0YVByb3ZpZGVyIjp7ImlkIjoiQkFSQjBLSU1YWFgiLCJ0eXBlIjoiRklQIn0sIkN1c3RvbWVyIjp7ImlkIjoiamF5QGZpbnZ1In0sIkFjY291bnRzIjpbeyJmaVR5cGUiOiJERVBPU0lUIiwiZmlwSWQiOiJCQVJCMEtJTVhYWCIsImFjY1R5cGUiOiJDVVJSRU5UIiwibGlua1JlZk51bWJlciI6IjAzOTQ4ODU2NjY4ODAwIiwibWFza2VkQWNjTnVtYmVyIjoiWFhYWFhYWFhYODAwMCJ9XSwiUHVycG9zZSI6eyJjb2RlIjoiMTAyIiwicmVmVXJpIjoiaHR0cHM6Ly9hcGkucmViaXQub3JnLmluL2FhL3B1cnBvc2UvMTAyLnhtbCIsInRleHQiOiJQZXJzb25hbCBGaW5hbmNlIE1hbmFnZW1lbnQiLCJDYXRlZ29yeSI6eyJ0eXBlIjoicHVycG9zZUNhdGVnb3J5VHlwZSJ9fSwiRklEYXRhUmFuZ2UiOnsiZnJvbSI6MTU3MDUxODU3NjQ2NSwidG8iOjE1ODYyNDMzNzg4NzZ9LCJEYXRhTGlmZSI6eyJ1bml0IjoiWUVBUiIsInZhbHVlIjoxfSwiRnJlcXVlbmN5Ijp7InVuaXQiOiJEQVkiLCJ2YWx1ZSI6MX0sIkRhdGFGaWx0ZXIiOlt7InR5cGUiOiJUUkFOU0FDVElPTkFNT1VOVCIsIm9wZXJhdG9yIjoiPiIsInZhbHVlIjoiMTAifV19.eWLuIHPW5KlCnTSrtG29zD3ibL14FN0Et45UgTPtPXuOhSXIPFF5K_vOf5JWdS2eHQvAYgD63Nb4U1vAnV_Iqq2J-7WgyAb68gjYkdG_oG5QqbrIs4MThR7GqFCSB_vd8G_vWqB08fNS9kjiAzLCtKqCw42Lu-_yCWlKin-INJMRTyXnorO0Y5prDwiK5SFLCkRLK2unFXY_aKEPbXXboR39CSbHmg6fVm4zxhC1fEMtjNUZcP33Gj3F6cW9k_jj94CBFyaqlEz_zvB97M_oTRcO-tP_TrqvZAUW8r3EpdAfTBTvdnnOroXm36OpavKKxGLT7m-M6eF2GUsHOc-kFA",
        "ConsentUse": {
      "logUri": "consent_use_loguri",
      "count": 0,
      "lastUseDateTime": "2020-04-07T07:09:38.877+0000"
        }
    }
```

Response Expected: 

```
200 OK
```
### Heartbeat

HTTP METHOD: `GET`

URL: `http://api.finvu.in/ConnectHub/V1/Heartbeat`

## Request headers

Below `http` headers need to be set as part of each request

  |  Key          |   Value       |
  | ------------- |:-------------:|
  | `content-Type` | `application/json` |
  | `Accept` | `application/json` |
  | `aa_api_key`   | ```eyJraWQiOiJrZXlJZDEiLCJhbGciOiJSUzI1NiJ9.eyJpc3MiOiJodHRwOi8vbG9jYWxob3N0OjgwODAvb3BlbmlkLWNvbm5lY3Qtc2VydmVyLXdlYmFwcC8iLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjkwOTAvQ29ubmVjdEh1Yi9WMS8iLCJleHAiOjE2MTMxMjM0NDAsImp0aSI6Ii11NmVNQXMxZGxpWGtPeWVYZGd3cmciLCJpYXQiOjE1ODE1ODc0NDAsIm5iZiI6MTU4MTU4NzM4MCwic3ViIjoibWFub2pAZmludnUuaW4ifQ.NlBDFmCh8SsX9T9eFZoiilfIkYObFpe57JQiSV-yc4Svt6AaHQFq3IT_0Z3I4880HixSvfcFCAUcP_meYguYk6Qp7YpTBMQ-S9j3ekcMnL-whDkR2dmChrgGI-ZaXtz-zlQXmfUNJiPKKJm8Ca68Bxi7lzvgF5YMxgz99m8Hj0ia1Ax3a468mo8JtvxelOrjYT-yVZDlH22Qo4INrdl3kIO_jDRB-AGQuq3095xjRciX-_zDK-a7_q_UyKRKjDnUjXkpiMzGfeilzfqMh-4PFfIXdQTF612QrSk7oZwF0XvqmjzQJYaGfPqdXtPcT3G7WDuS_YAdAQW5vIjAW96pXQ```      |

Request Body

```
No Request Body expected
```
Response Expected: 

```
    {
        "ver": "1.0",
        "timestamp": "2019-01-23T04:08:25.132+0000",
        "Status": "UP"
    }
```
