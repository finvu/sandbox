---
---
# Welcome to Finvu
#### **Software prerequisite**
- Postman    _(URL : https://www.getpostman.com/)_

### **API to enter your own sample data**
 - **Adding User Account API**
	
  |          |             |
  | ------------- |:-------------:|
  | URL      | _http://<<0.0.0.0>>:<<0000>>/Accounts/add_ |

  Request Body


```
<UserAccountInfo>
	<UserAccount accountRefNo="RefSBI002" accountNo="SBI222222222" accountTypeEnum="SAVINGS">
		<Identifiers pan="AFF34964FFF" mobile="7000000000" email="backend@gmail.com" aadhar="3408030493453"></Identifiers>	
	</UserAccount>
</UserAccountInfo>
```
Response Expected: 
```
UserAccountInfo [userAccounts=[UserAccount [accountRefNo=RefSBI002, accountNo=SBI222222222, accountTypeEnum=SAVINGS, identifiers=Identifiers [pan=AFF34964FFF, mobile=7000000000, email=backend@gmail.com, aadhar=3408030493453]]]]
  ```


 - **Adding User Account Transaction data API**
	
  |          |             |
  | ------------- |:-------------:|
  | URL      | _http://<<0.0.0.0>>:<<0000>>/Accounts/Transaction/add_ |

  Request Body


```
<UserAccountTrans>
	<UserAccount> 
		<accountRefNo>RefSBI001</accountRefNo> 
		<accountNo>SBI111111111111</accountNo> 
		<accountTypeEnum>SAVINGS</accountTypeEnum>
		<transactionRefNo>txn0001</transactionRefNo> 
		<accountBalance>10000.00</accountBalance> 
		<amount>300.00</amount> 
		<amountEntry>CR</amountEntry> 
		<transationNarration>salary</transationNarration>
	</UserAccount>
	<UserAccount> 
		<accountRefNo>RefSBI002</accountRefNo> 
		<accountNo>SBI222222222</accountNo> 
		<accountTypeEnum>SAVINGS</accountTypeEnum>
		<transactionRefNo>txn0001</transactionRefNo> 
		<accountBalance>100.00</accountBalance> 
		<amount>300.00</amount> 
		<amountEntry>CR</amountEntry> 
		<transationNarration>salary</transationNarration>
	</UserAccount>
</UserAccountTrans>
```
Response Expected: 
```
UserAccountTrans [userAccounts=[UserAccount [accountRefNo=RefSBI001, accountNo=SBI111111111111, accountTypeEnum=SAVINGS, transactionRefNo=txn0001, accountBalance=10000.0, amount=300.0, amountEntry=CR, transationNarration=salary], UserAccount [accountRefNo=RefSBI002, accountNo=SBI222222222, accountTypeEnum=SAVINGS, transactionRefNo=txn0001, accountBalance=100.0, amount=300.0, amountEntry=CR, transationNarration=salary]]]
```
  
### **Financial Information Provider API**


  - **Account Discover API**
	
  |          |             |
  | ------------- |:-------------:|
  | URL      | _http://<<0.0.0.0>>:<<0000>>/ConnectHub/V1/Accounts/discover_ |
  | Key      | ```x-access-token```      |
  | Value | ```Please email us on info@cookiejar.co.in for value of key``` |
  
  Request Body

 

```
<?xml version="1.0" encoding="UTF-8"?>
<AccDiscoveryRequest xmlns="https://standards.rebit.org.in/aa" ver="1.0" timestamp="2018-05-22T17:30:15.239Z" txnid="8399263c-4a15-11e8-bcd1-0277a9fbfedc">
<Identifiers><Identifier category="STRONG" type="MOBILE" value="7030608902"></Identifier></Identifiers>
<FIPDetails name="string" id="string">
<FITypes>
<FIType1 name="DEPOSIT" value="string"></FIType1>
<FIType name="DEPOSIT" value="string"></FIType>
</FITypes>
</FIPDetails>
<Meta type="PERSON" value="string">
<DeviceInfo>
<Tag name="MOBILE" value="string"></Tag>
<Tag1 name="GEOCODE" value="string"></Tag1>
<Tag3 name="LOCATION" value="string"></Tag3>
<Tag4 name="IP" value="string"></Tag4>
<Tag5 name="TYPE" value="string"></Tag5>
<Tag6 name="ID" value="string"></Tag6>
<Tag7 name="OS" value="string"></Tag7>
<Tag8 name="APP" value="string"></Tag8>
<Tag9 name="CAPABILITY" value="string"></Tag9>
<Tag10 name="TELECOM" value="string"></Tag10>
</DeviceInfo>
</Meta>
</AccDiscoveryRequest>
```
Response Expected: 
```
<AccDiscoveryResponse><timestamp>1527010215239</timestamp><txnid>8399263c-4a15-11e8-bcd1-0277a9fbfedc</txnid><AuthenticatorType/><DiscoveredAccounts><DiscoveredAccounts><Account><FIType>DEPOSIT</FIType><accType>CURRENT</accType><accRefNumber>999</accRefNumber><maskedAccNumber>XXXXXXXXX3456</maskedAccNumber><aeba>N</aeba></Account></DiscoveredAccounts></DiscoveredAccounts></AccDiscoveryResponse>
  ```


  - **Account Linking API**
	
  |          |             |
  | ------------- |:-------------:|
  | URL      | _http://<<0.0.0.0>>:<<0000>>/ConnectHub/V1/Accounts/{AccountRefNo}_ |
  | Key      | ```x-access-token```      |
  | Value | ```Please email us on info@cookiejar.co.in for value of key``` |
  
  e.g. URL : http://192.168.0.1:9090/ConnectHub/V1/Accounts/RefSBI004
  
  Request Body

 

```
<?xml version="1.0" encoding="UTF-8"?>
<AccLinkRequest xmlns="https://standards.rebit.org.in/aa" ver="1.0" timestamp="2018-05-09T17:51:18.412Z" callbackURL="string" txnid="f35761ac-4a18-11e8-96ff-0277a9fbfedc">
<AccDetails>
<Account FIType="DEPOSIT" accType="SAVINGS" accRefNumber="RefSBI001" maskedAccNumber="SBI111111111111" aeba="Y"></Account>
<FIPDetails id="string" name="string"></FIPDetails>
</AccDetails>
</AccLinkRequest>
```
Response Expected: 

```
<AccLinkResponse><ver>1.0</ver><timestamp>1529153879076</timestamp><txnid>f35761ac-4a18-11e8-96ff-0277a9fbfedc</txnid><Account><FIType>DEPOSIT</FIType><accType>SAVINGS</accType><accRefNumber>999</accRefNumber><maskedAccNumber>XXXXXXXXX3456</maskedAccNumber><aeba>Y</aeba></Account></AccLinkResponse>
```


  - **Account Confirm Token API**
	
  |          |             |
  | ------------- |:-------------:|
  | URL      | _http://<<0.0.0.0>>:<<0000>>/ConnectHub/V1/Accounts/{AccountRefNo}/confirm-token_ |
  | Key      | ```x-access-token```      |
  | Value | ```Please email us on info@cookiejar.co.in for value of key``` |
  
  e.g. URL : http://192.168.0.1:9090/ConnectHub/V1/Accounts/RefSBI001/confirm-token
  
  Request Body
  Put the SMS received on mobile in <token>{OTP sms}</token>
 

```
<?xml version="1.0" encoding="UTF-8"?>
<ConfirmLinkingRequest ver="1.0"
timestamp="2018-05-05T10:27:17.699Z"
txnid="410c2d2e-4a1e-11e8-960e-0277a9fbfedc">
<token>774265</token>
</ConfirmLinkingRequest>
```
Response Expected: 

```
<ConfirmLinkingResponse><ver>1.0</ver><timestamp>1525516037699</timestamp><txnid>410c2d2e-4a1e-11e8-960e-0277a9fbfedc</txnid></ConfirmLinkingResponse>
```



  - **Account FI request API**
	
  |          |             |
  | ------------- |:-------------:|
  | URL      | _http://<<0.0.0.0>>:<<0000>>/ConnectHub/V1/FI/request_ |
  | Key      | ```x-access-token```      |
  | Value | ```Please email us on info@cookiejar.co.in for value of key``` |
  
 
  Request Body
  Put the SMS received on mobile in <token>{OTP sms}</token>
 

```
<FIRequest ver="1.0" timestamp="2018-06-09T09:58:50.505Z" txnid="c5a1450c-d08a-45b4-a475-0468bd10e380">
	<ConsentID>c4a1450c-d08a-45b4-a475-0468bd10e380</ConsentID>
		<DataConsumer id="123456@finvu.in" type="AA" callbackURL="localhost:9090/AA/Test"></DataConsumer>
	<RequestFIParams>
		<KeyMaterials>
			<KeyMaterial startTime="2018-06-01T09:58:50.505Z">
				<SessionID>string</SessionID>
				<DHPublicKey expiry="2019-06-01T09:58:50.505Z">
					<Parameters>Param 1</Parameters>
					<KeyValue>W0C9Z43fLvtE1ab6itHiZy/5Cc4zvh8r80YQc0ezqAo=</KeyValue>
				</DHPublicKey>
				<Nonce>12345</Nonce>
				<Signature> Signature Value
				</Signature>
			</KeyMaterial>
		</KeyMaterials>
	</RequestFIParams>
</FIRequest>
```
Response Expected: 

```
TODO : 

```



  - **Account FI Fetch API**
	
  |          |             |
  | ------------- |:-------------:|
  | URL      | _http://<<0.0.0.0>>:<<0000>>/ConnectHub/V1/FI/fetch/{SessionID}_ |
  | Key      | ```x-access-token```      |
  | Value | ```Please email us on info@cookiejar.co.in for value of key``` |
  
 
  Request Body
  Put the Session ID from FI - Request response in <ConsentID>{SessionID}</ConsentID>
  e.g. http://192.168.0.1:9090/ConnectHub/V1/FI/fetch/17dbec77-3b43-4e67-9370-c347d7402671

```
<?xml version="1.0" encoding="UTF-8"?>
<FetchFIRequest xmlns="http://https//standards.rebit.org.in/aa" ver="1.0" timestamp="2018-05-09T18:14:25.305Z" txnid="af5b8023-aabc-4a46-8f37-d3c167129b1e">
	<ConsentID>c4a1450c-d08a-45b4-a475-0468bd10e380</ConsentID>
</FetchFIRequest>
```
Response Expected: 

```
<?xml version="1.0" encoding="UTF-8"?><FIFetchResponse timestamp="1529154796883" txnID="af5b8023-aabc-4a46-8f37-d3c167129b1e" ver="1.0"><responseCode/><FIPId/><Account><id>123456</id><type>string</type><FIPId>12345@hdfc.co.in</FIPId><FIs><FI><EncryptedFI>c1l2V2xRazh2OVdtS3JqWklBQk5zVm1xUFhucGRQc0xJVDZuYjFKa1JBMGlmUzVZTUZxdkRQbmI1
WU9mdit0UE9KbTBxYmNDMFpFdlVrQnBuWFBHdGc9PQ==</EncryptedFI><KeyMaterial><SessionID/><startTime>1528537218744</startTime><DHPublicKey><expiry>1528537218744</expiry><Parameters>Param 1</Parameters><KeyValue>KuhybmYeGpWh/VfCFmZAkIwDUfFtfRt2rcCVYZLxUEM=</KeyValue></DHPublicKey><Nonce>1</Nonce><Signature>Signature Value</Signature></KeyMaterial></FI></FIs></Account><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"><SignedInfo><CanonicalizationMethod Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/><SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#rsa-sha1"/><Reference URI=""><Transforms><Transform Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature"/></Transforms><DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/><DigestValue>PQP16tttmO+UFsU5GNu0krjPqcQ=</DigestValue></Reference></SignedInfo><SignatureValue>cpNw25twspqZK9Qdaa2xyMumNdzxHv7J24HJPFqXk4OLKjTo1hgK+cldFCN1jStauSDPyABiUMVE
FXC669ObNbD7hfCd6jdUO7RuvYx0Qq87ahZC7M+czG2RSreB/KScNz1lBWdCS0D80vGpYl4WhLzf
SyhSM1sMB/TMDGUP9BLoX/kOcnfVq15mDxgs8riuC4sx/dpbmr9fmI2HUw27TVF2SCQ9K+b5Fdse
aGAn8zxZ0/2leWM+MzzAJk9Zx2jexijTMvFKRxGvlC9A7g6USiJpFK9wcxDMhuLh36HatQPxVUyt
wHAvVax+DK52c67Q14WFIIfegNgY9PJu1jgATQ==</SignatureValue><KeyInfo><X509Data><X509SubjectName>CN=PP,OU=CTPL,O=CTPL,L=Pune,ST=Maharashtra,C=IN</X509SubjectName><X509Certificate>MIIDWTCCAkGgAwIBAgIEdZ+fzDANBgkqhkiG9w0BAQsFADBdMQswCQYDVQQGEwJJTjEUMBIGA1UE
CBMLTWFoYXJhc2h0cmExDTALBgNVBAcTBFB1bmUxDTALBgNVBAoTBENUUEwxDTALBgNVBAsTBENU
UEwxCzAJBgNVBAMTAlBQMB4XDTE4MDUzMDE3MTE0MloXDTE5MDUyNTE3MTE0MlowXTELMAkGA1UE
BhMCSU4xFDASBgNVBAgTC01haGFyYXNodHJhMQ0wCwYDVQQHEwRQdW5lMQ0wCwYDVQQKEwRDVFBM
MQ0wCwYDVQQLEwRDVFBMMQswCQYDVQQDEwJQUDCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoC
ggEBALfG14O4AJKktnFbM5/vfJ7gcNjWRn0tiOSc05Ha8T7ZyiqP+og0vg/KqaJyh8gowCnYcmQ9
gncRfLbu2B/KESMcLn6mdQawO2UeNwf4oLSH5F12BOaYLRdnDivAwjJmZ897kTgZ3MgDngKOqn4p
vbNjHM1gXLHcxUhfJ+dCDgsM872qYUvwsCDselfdB7pGz69YImbjiYs5RuHk2bg16jfb6Ps5H18n
UTu0qNkvnShBeNz98Z7dNP5phI2oCEuZdyZqB5wXdir4YrFGbk3wpIVLlLEYpIUMFLYtryK2c5xB
HMP39W5r6mnsY/F4vuuwtmWgnPXQa1+4ZblEVhLDkhkCAwEAAaMhMB8wHQYDVR0OBBYEFPZNZ7B8
XiTIhHEhNtDFj0b1LGj6MA0GCSqGSIb3DQEBCwUAA4IBAQBVDrNd9jwj3ylure8iGNvd6fzmc+or
hU/9itFomim7X/TMAT6lYzpvJKyBLKN1l/mZQulkV+yRVdY5ETDnvKVHHfBE7OVSES8JYJXe/41L
v0OQYTLEFcJwVSR+b6yOUgWBh2xdpkat358UwItQ5NIuVAU1EIbgfejHmMvJlUf/gWj1wD6+Hx9L
UJn6SSo59xjPxbTEsh8PLMEipM2eI7cXG/uGMpyBg41YfvW2JQrXa4ILokQ1fbtc3iZZtfYZMVC0
BaMXz5VPVRb8PrdxAt2szi93yS7HJ9UHYRbBmbRjbulFtrSXKd3GqvRfjht4174iKcBVkpNOpIQs
syBiW1qx</X509Certificate></X509Data></KeyInfo></Signature></FIFetchResponse>
```
