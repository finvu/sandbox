# Get Started

You can integrate with our AA in multiple ways as it depends on what you are building.  

Interaction and integration with Finvu Account Aggregator (AA) would be as a FIP or FIU. Refer to the appropriate section for details on integration and calling of apis.

## Understanding the FIU flows

Below are the high level flows for a FIU. 

### Consent Flow - Request for consent
The FIU requests for consent from the customer, by calling the AA server `/Consent` API. The AA server on receiving the request notifies the customer through an app notification, SMS, etc of the consent request. The customer views details of the consent on the Finvu app (mobile or Web) and approves/rejects the consent as appropriate.

### Consent Flow - Notify FIU of the consent
Once the customer approves or rejects the consent on the Finvu app (Mobile or Web), AA server notifies the FIU by calling the FIU `/Consent/Notification` API. The FIU on receiving the notification can chose to update their system and subsequently gets details of the consent from the AA server by calling the `/Consent/{id}`.

### Data Flow - Making a data request
If the customer has approved the consent and FIU has received the details of the consent from Finvu AA , data can be requested for that consent by calling the AA `/FI/request` api. AA server returns a unique session identifier for that request and subsequently forwards the request to the FIPs as per the consent details.

### Data Flow - Receiving data
FIU after making a data request will need to wait for the Data Ready notification from AA as AA server gets the data from the FIP. Once data is available, AA notifies the FIU of the data ready. On receiving the ready notification, FIU server can fetch the data from the AA server.

## Understanding the AA flows and Customer interaction

Before the customer can start sharing their financial information securely with FIUs, the customer would have to be registered with a licensed AA. Finvu AA provides a mobile or web application for the customer interaction. This is a fairly simple process for the customer, with only a few steps. 

### Step 1. Customer Registration with AA
The Customer registers with the Finvu Account Aggregator either on the Finvu mobile app or through web. The customer after registration gets a unique handle / AA id e.g. `yourname@finvu` or could be your mobile no `9999910000@finvu` . The choice is yours !. This virtual user handle can be given to a FIU for consent requests (much like a UPI handle for payment collection). 

### Step 2. Customer Linking their financial accounts 
The Customer need to link their accounts with their unique Finvu AA id, and authentication is a simple process via an OTP that is sent to the customer registered mobile no by their Financial Institution.

### Step 3. Securely share financial information
Customer can now accept or reject consent requests coming from a FIU and share their financial account information for their choice of selected accounts. This can be done through Finvu mobile or web app. Once the consent is accepted, FIU can request for financial information from their selected accounts in the consent through the Finvu AA. 

## Integrating with our FIU module
We have built the nuts and bolts and the complexity of the FIU functionality to interact with an AA. This would help you to focus on building your app once you receive the decrypted data. 

Our FIU sandbox environment is hosted and available at all times for you to access. 

The FIU sandbox is AA agnostic and can interface with any account aggregator, this is done on basis of the handle of the AA user e.g. customer1@finvu will redirect to the 'Finvu AA', customer2@otheraa will redirect requests to the 'Other AA'

If you are building apps on FIU side start integrating with our FIU sandbox. 

[Integrating with Finvu FIU]

## Integrating using your own FIU

If you are building your own FIU module you would need to first build the FIU functionality and the APIs. Then move to integrating with the Finvu AA sandbox 

[Integrating with Finvu AA]


## Sample data for testing
Whether you are building your own FIU or using our FIU, you would need sample data for testing. 

We have made it simple by creating simulated FIP and data entry can be done as per your requirements for different FI Types. Refer to the APIs for the same. 

We have created multiple FIP sandboxes so you can test for real scenarios.

Refer to the [Sample Test Data] section for entering sample data. The data schemas are compliant with the [ReBIT FIType schemas](https://api.rebit.org.in/schema).

As data is sourced from FIP (Financial Information Provider) we have built a FIP sandbox as well. However as a FIU developer you need not worry about FIP as FIU never interact with FIP directly and communication is always through an AA. For reference more details of FIP at [FIP Sandbox](/fip_simulator/)

  