# Overview

## Introduction

Welcome to Finvu !. Here you will find details on how to integrate and use the Account Aggregator APIs. While we are mainly playing the role of Account Aggregator (AA) in the ecosystem, however we are also providing the modules that implement the FIU and FIP functionality and their APIs. FIUs and FIPs can implement these modules in their production environment to enable quick onboarding to the AA ecosystem. 

Alternatively, FIU or FIP can consume our AA REST API if they wish to build ther own FIU or FIP module. For this purpose, Finvu has built an [‘AA API sandbox’](finvu_aa_integration) which is an implementation of the REST APIs needed to be implemented by an AA. Here we outline all the necessary information needed from a prospective of FIU or FIP to interface with our AA REST API so they can be onboarded in the AA ecosystem. 

We are trying to keep upto the pace by implementing latest community and Rebit API specs for the simulators, however if there any issues, do drop us a note at `support@cookiejar.co.in`

## Glossary

`AA` - Account Aggregators that facilitate secure information exchange between FIU/Customer and FIP.

`FIP` - Financial Information Providers that hold the customer account information and share encrypted information on presentation of a consent and data request from the FIU or Customer.

`FIU` - Financial Information Users that request consent from a customer via an AA and subsequently request for data on the basis of an approved consent from an AA. These are the data consumers.

`aa_api_key` - The HTTP header that needs to be set when a AA calls the FIP or FIU API. This header value is the token that FIP or FIU generates and gives to AA. 

`fip_api_key` - This HTTP header needs to be set when FIP calls the AA APIs. This is a token that AA gives to FIP and is used in conjunction with the `x-jws-signature` header. 

`client_api_key` - The HTTP header that needs to be set for every API call when FIU calls the AA APIs and value contains the token that AA gives to FIU. This is used in conjunction with the `x-jws-signature` that FIU will set in the API when calling AA.

`x-jws-signature` - HTTP header that contains the 'detached' signature of the body. API request/response need to be signed and the signature to be set in this header. Please see the details in our [How to](how_to) section to generate the signature

## API Information

All API request and responses are in standard [JSON](https://www.json.org) format. The APIs use `GET` and `POST` requests and HTTP response codes to indicate status and errors. All requests must include a Content-Type of `application/json` and the body must be valid JSON. API use `https` protocol for security. 

## Get Started

So, [Lets get started](get_started) with the integration and building out products using the AA ecosystem. 

## Version

We are adhering to the latest API specifications as per ReBIT and community which are currently at 1.1.3