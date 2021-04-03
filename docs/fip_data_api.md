# Test Data Entry API

In order for FIU to test with simulated consumer financial accounts and data we have created a set of APIs to enter sample data in our FIP sandbox which is the source of customer account information.

These can be used to add accounts for the discovery & linking flows in the AA and the associated account transactions, balance, etc for consumption in the FIU. 

These are proprietary set of APIs to enter test data, however the account structure confirm to the [ReBIT FIType Schemas](https://api.rebit.org.in/schema)

[Postman](https://www.getpostman.com) or any other appropriate tool can be used for execution. 

We support the `DEPOSIT`, `TERM-DEPOSIT`, `RECURRING_DEPOSIT`, `MUTUAL_FUNDS` FI Types to add sample account data in our sandbox environment. 

You can also play with multiple simulated FIPs. 

We have simulated two Banks 

**Finvu Bank** url : `https://api.finvu.in`

**Dhanagar Bank** url : `https://apialt.finvu.in`

## Step 1. Adding Test Accounts ( /Accounts/add )

This API adds the customer's financial account and maps the associated information for that account such as Mobile No, PAN, Account No which serve as identifiers during the discovery and linking process of the AA flows. The Mobile No is a strong identifier and hence should be a valid mobile no that is required for discovery and linking.

	
  |          |             |
  | ------------- |-------------|
  | URL      | `https://api.finvu.in/Accounts/add` |
  | HTTP METHOD      | `POST` |

  Field Usage

  | Field Name         | Usage            | Enum Values
  | ------------- |-------------|-------------|
  | accountNo      | The Customer unique financial account No | None, can be any value |
  | accountRefNo      | A ref number unique to the accountNo | None, can be any value |
  | accountTypeEnum | The type of account  | Depending on the FIType |
  | pan		| The PAN of the account holder can be used during AA discovery flow| None, can be any value |
  | mobile  | The Registered Mobile No of the account holder. OTP will be sent to this mobile during linking | Should be valid mobile no |
  | email  | The Registered email of the account holder. OTP will be sent to this email during linking | Should be valid email id |
  | aadhar | This is the aadhar of the customer and is not used | None, can be any value |
  | FIType | The Financial Information Type | DEPOSIT 
  |			|								|	TERM-DEPOSIT 
  |			|								|	RECURRING_DEPOSIT 
  |			|								|	MUTUAL_FUNDS 
  

Mapping of the `FITYPE` and associated `accountTypeEnum` 

  | FIType        | AccountTypes (Enum values)| 
  | ------------- |-------------|
  | DEPOSIT       | `SAVINGS` or `CURRENT` |
  | TERM-DEPOSIT       | DEFAULT |
  | RECURRING_DEPOSIT       | DEFAULT |
  | MUTUAL_FUNDS       | DEFAULT |
  

The `accountRefNo` and `accountNo` field values need to be changed as per your own.


Sample Request Body
``` xml
<UserAccountInfo>
    <UserAccount accountRefNo="" accountNo="" accountTypeEnum="CURRENT" FIType="DEPOSIT">
      <Identifiers pan="CGDPM1781T" mobile="9999988888" email="name@email" aadhar="6895324456"></Identifiers> 
    </UserAccount>
</UserAccountInfo>
```
Response Expected
```
User account(s) added.

  Account Reference Number : REFBOB1478596
  Account Number : BOB1478596
  (Its used in Account Discovery.)

 Please save this information for FI request API calls.
```


## Step 2. Adding Account Information ( /Accounts/Transaction/add )

This api adds the account information (Profile, Summary, Transactions) for a particular account. This should be used in sequence to the Add User Account API with valid values as per the account.

  |          |             |
  | ------------- |-------------|
  | URL      | `https://api.finvu.in/Accounts/Transaction/add` |
  | HTTP METHOD      | `POST` |

  Field Usage

  | Field Name         | Usage            | Enum Values
  | ------------- |-------------|-------------|
  | accountNo      | The Customer unique financial account No | None, can be any value |
  | accountRefNo      | A ref number unique to the accountNo | None, can be any value |
  | accountTypeEnum | The type of account  | Depending on the FIType |
  | FIType | The Financial Information Type | DEPOSIT 
  |			|								|	TERM-DEPOSIT 
  |			|								|	RECURRING_DEPOSIT 
  |			|								|	MUTUAL_FUNDS |
  | accountData | This contains the account transactions, balance, summary information of the account. This is embedded in a CDATA section and structure confirms to the [ReBIT FIType Schema](https://api.rebit.org.in/schema) . | The complete XML based on the FIType | 


Mapping of the `FITYPE` and associated `accountTypeEnum` 

  | FIType        | AccountTypes (Enum values)| 
  | ------------- |-------------|
  | DEPOSIT       | `SAVINGS` or `CURRENT` |
  | TERM-DEPOSIT       | DEFAULT |
  | RECURRING_DEPOSIT       | DEFAULT |
  | MUTUAL_FUNDS       | DEFAULT |


!!! note "Values in the CDATA section"
	In the `<Account>` Xml tag below values to be changed
	The **linkedAccRef** and **maskedAccNumber** should be unique refNo. 
	The type="deposit" for the FIType `DEPOSIT`
	    type="term_deposit" for the FIType `TERM-DEPOSIT`
		type="recurring_deposit" for the FIType `RECURRING_DEPOSIT`
		type="mutualfunds" for the FIType `MUTUAL_FUNDS`
		
	Modify the details in the <Holder> xml tag email, mobile, pan should match that entered in the Add account api.
	In the `<Summary>` tag the `type` should be one of the type enum value based on the FIType. Refer to the [ReBIT Schema](https://api.rebit.org.in/schema)
	 


The `accountRefNo` and `accountNo` field values need to be same as those provided in the /Accounts/add API.

Sample Request Body
```
<UserAccountTrans>
    <UserAccount>
        <accountRefNo></accountRefNo>
    <accountNo></accountNo>
        <FIType>DEPOSIT</FIType>
        <accountTypeEnum>CURRENT</accountTypeEnum>
        <accountData><![CDATA[<Account xmlns="http://api.rebit.org.in/FISchema/deposit" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://api.rebit.org.in/FISchema/deposit ../FISchema/deposit.xsd" linkedAccRef="REF0002345666" maskedAccNumber="0002345666" version="1.0" type="deposit"><Profile><Holders type="JOINT"><Holder name="YOUR NAME" dob="1992-09-24" mobile="9999988888" nominee="NOT-REGISTERED" email="name@email" pan="CGDMP1444K" ckycCompliance="true"/></Holders></Profile><Summary currentBalance="4007.55" currency="INR" exchgeRate="5.5" balanceDateTime="2019-04-12T13:20:00-05:00" type="CURRENT" branch="Pune" facility="CC" ifscCode="BARB0SHIPOO" micrCode="411012011" openingDate="2018-01-01" currentODLimit="20000" drawingLimit="10000" status="ACTIVE"><Pending amount="20.0"/></Summary><Transactions startDate="2019-04-12" endDate="2020-04-12"><Transaction txnId="M391232" type="DEBIT" mode="OTHERS" amount="23.6" currentBalance="4884.79" transactionTimestamp="2019-07-14T13:20:00" valueDate="2019-07-14" narration="TO ATM TXN CHRGE 08 Jul 2019" reference="REF0001112"/><Transaction txnId="M391443" type="DEBIT" mode="OTHERS" amount="4500.0" currentBalance="361.19" transactionTimestamp="2019-07-14T18:30:00" valueDate="2019-07-14" narration="ATM CASH TXN/BOB BANK LIMITED Pune   KL" reference="REF0001112"/><Transaction txnId="M196581" type="CREDIT" mode="OTHERS" amount="460.0" currentBalance="821.19" transactionTimestamp="2019-07-15T18:30:00" valueDate="2019-07-15" narration="PC8027317       CFD ETRANSFER" reference="REF0001112"/><Transaction txnId="M28746" type="DEBIT" mode="OTHERS" amount="300.0" currentBalance="521.19" transactionTimestamp="2019-07-17T18:30:00" valueDate="2019-07-17" narration="BOBMOBILE-RECHARGE/KBPUEHAFB5F3" reference="REF0001112"/><Transaction txnId="M28746" type="DEBIT" mode="OTHERS" amount="50.0" currentBalance="4007.55" transactionTimestamp="2019-07-17T18:30:00" valueDate="2019-07-17" narration="BOBMOBILE-RECHARGE/KBPUEHAFB5F3" reference="REF0001112"/></Transactions></Account>]]></accountData>
</UserAccount>
</UserAccountTrans> 
```
Response Expected: 
```
User account transaction added.
```
