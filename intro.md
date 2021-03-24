# Introduction

Our APIs are a fast and easy way to integrate our shipping functionality into your business applications and websites. Each API provides access to Estes functionality, allowing you to bypass the traditional HTML forms process and make shipping with Estes a more convenient solution.

# Accessing Our APIs

To use our APIs, you will need to generate an API key for the production environment and another API key for the test environment. This API key is used for all APIs. These keys are the only ones needed to communicate with our APIs.

(API keys are not used with Estes legacy web services. To review older web services, see
<https://www.estes-express.com/resources/digital-services/api/index>.)

-   If you are a TMS provider who wants to connect to Estes APIs on behalf of
    multiple customers need to use a client ID, see (Transportation Management
    System) **TMS API Customers**  

-   If you are an individual customer who wants to connect to Estes APIs directly
    who use their MyEstes username and password to create an API key, see
    **Individual/Direct API Customers**

## TMS API Customers

Obtain your API key by providing the following information in an email to <WebSupport@estes-express.com>:

-   Developer Name
-   Developer Email
-   Developer Title
-   Developer Company

You will receive two emails with a client ID and client secret, one for test environment and another for production environment.].

See the next steps, How to Create and Retrieve Your API Key

### How To Create Your API Key

With Postman or a similar API tool, pass your client ID and client secret using **Basic Authentication** using the following method:

Production example:
```
curl --request POST 'https://cloudapi.estes-express.com/apikey'   
--header 'Content-Type: application/json'   
--header 'Authorization: Basic
ZThkNmM4Y2MtMDY3ZC00ZmY4LTgxYzMtNWJmNjAxNjUzYjYwOjUyZmRmYzA3LTIxODItNjU0Zi0xNjNmLTVmMGY5YTYyMWQ3Mg=='
```

Test example:
```
curl --request POST 'https://uat-cloudapi.estes-express.com/apikey' 
--header 'Content-Type: application/json' 
--header 'Authorization: Basic
ZThkNmM4Y2MtMDY3ZC00ZmY4LTgxYzMtNWJmNjAxNjUzYjYwOjUyZmRmYzA3LTIxODItNjU0Zi0xNjNmLTVmMGY5YTYyMWQ3Mg=='
```

In the response, you will receive an API Key, your Client ID and a new Client Secret.

*Important: This new Client Secret replaces the secret sent in the previous e-mail.*

Store this new Client Secret so you may remember it.

### How To Retrieve Your API Key

If you lost the API Key information, use the GET method for /apikey to retrieve it. Do not forget to use your Client ID and new Client Secret.

Production example:
```
curl --request GET 'https://cloudapi.estes-express.com/apikey' 
--header 'Content-Type: application/json' 
--header 'Authorization: Basic
ZThkNmM4Y2MtMDY3ZC00ZmY4LTgxYzMtNWJmNjAxNjUzYjYwOjUyZmRmYzA3LTIxODItNjU0Zi0xNjNmLTVmMGY5YTYyMWQ3Mg=='
```

Test example:
```
curl --request GET 'https://uat-cloudapi.estes-express.com/apikey'   
--header 'Content-Type: application/json'  
--header 'Authorization: Basic
ZThkNmM4Y2MtMDY3ZC00ZmY4LTgxYzMtNWJmNjAxNjUzYjYwOjUyZmRmYzA3LTIxODItNjU0Zi0xNjNmLTVmMGY5YTYyMWQ3Mg=='
```

## Individual/Direct API Customers

For individual or direct customers, you will need your MyEstes Username and MyEstes Password. If you do not have a MyEstes profile, you can [sign up for one
here](https://www.estes-express.com/myestes/home/login).

### Generating API Keys for Individual/Direct Customers

To generate an API Key for the *production* environment, submit a POST request to the following URL with your MyEstes Username and MyEstes Password as the username and password in the basic authorization header. See this example.
```
curl -u myEstes-username:myEstes-password -H "accept: application/json" -X POST
"https://cloudapi.estes-express.com/v1/api-key"
```

To generate an API Key for the *test* environment, submit a POST request to the following URL with your MyEstes Username and MyEstes Password as the username and password in the basic authorization header. See this example.
```
curl -u myEstes-username:myEstes-password -H "accept: application/json" -X POST
"https://uat-cloudapi.estes-express.com/v1/api-key"
```

The response will contain the API Key for the chosen environment.

### Retrieving API Keys for Individual/Direct Customers

To retrieve a previously issued API Key for production environment , submit a GET request to the following URL with your MyEstes Username and MyEstes Password as the username and password in the basic authorization header. See this CURL example (for test environment, you need to change the domain to: *https://uat-cloudapi.estes-express.com*):
```
curl -u myEstes-username:myEstes-password -H "accept: application/json" -X GET
"https://cloudapi.estes-express.com/v1/api-key"
```

To change the previously issued API Key for production environment, submit a DELETE request to the following URL with your MyEstes Username and MyEstes Password as the username and password in the basic authorization header. (For test environment, you need to change the domain to: *https://uat-cloudapi.estes-express.com*):
```
curl -u myEstes-username:myEstes-password -H "accept: application/json" -X
DELETE "https://cloudapi.estes-express.com/v1/api-key"
```

Then submit a POST request to generate a new key as explained above. Remember that you must pass the API Key in a header while making requests to the other APIs on the platform. 

See this example for production:
```
curl -H "accept: application/json" -H "apikey: *your-api-key*" -X GET
<https://cloudapi.estes-express.com/v1/invoices?pro=1234567890>
```

See this example for test:
```
curl -H "accept: application/json" -H "apikey: *your-api-key*" -X GET
<https://uat-cloudapi.estes-express.com/v1/invoices?pro=1234567890>
```

### Using API Keys (For TMS and Individual/Direct Customers)

**Step 1**

When using our APIs and Web Services, you must pass the API Key using the /authenticate method to initially request a bearer token.

Production example:
```
curl -X POST "https://cloudapi.estes-express.com/authenticate" -H "accept:
application/json" -H "apikey: 0101010101"
```

Test example:
```
curl -X POST "https://uat-cloudapi.estes-express.com/authenticate" -H "accept: application/json" -H "apikey: 0101010101"
```

The response JSON will contain the bearer token.

**Bearer Token JSON Sample**  

```
{  
"access_token":
"eyJhbGciOiJSUzI1NiIsImtpZCI6Imp3dC1zaWduLWNlcnQifQ.eyJzY29wZSI6IiIsImNsaWVudF9pZCI6ImtvbmciLCJpc3MiOiJodHRwczovL2ZlZGVyYXRpb24tcWEuZ3NrLmNvbSIsImV4cCI6MTUzOTk3MzQyM30.IRvv0m8QKuOSDbhnlYx11bdvjk3PJBgz0cV7cSO4c1Phxfo4dRvLBvKx3TBnlaHwNYx4k3BcPEP5yDeflEVGVAhM0Is1potXWJfTQsH4PECZHEJNa7eoJFMKo9FKOutLoPg5avY2V0Oq0EU1wO8cTfrC2hNyJxfMMAYtK7pfB0u_a3ZyWLLWH9LN6xztYM86eh7QavHyns3__-uGy0O-imFDJ3Oi0SdKA1XYQDnqNhvN8J9omOVVMxEBuRdTeldM0lbeLxpWmXybQotIbMFGRVFUrwSIU6OxPA3wHyuL6F7p53C2ZsJXP463Sx2Y-9SILvVsuFtKWiUjbUn2--141g",  
"token_type": "Bearer",  
"expires_in": 35999  
}
```

**Step 2**

Include the bearer token with your API requests.

*Example: Using Your API Key and Bearer Token with Shipment Tracking*

**GET ​/v1​/shipments/history**

This method returns shipment tracking details associated with an account.

The **Authorization** parameter {TOKEN_HERE} is the bearer token returned after
requesting authentication.

The **apikey** parameter is your API key.

Production example:
```
curl -X GET "https://cloudapi.estes-express.com/v1/shipments/history?pro=0000000000" -H
"accept: application/json" -H "A
```

Test example:
```
curl -X GET
"https://uat-cloudapi.estes-express.com/v1/shipments/history?pro=0000000000" -H
"accept: application/json" -H "A
```

# Geo Location 

Geo Location (GPS) data represents the physical location of freight at key points while in transit. The timing and availability of geo location information is dependent on the stage of the transit lifecycle. For example, there are more triggering events when freight is Out for Delivery than when moving through the Line Haul network. Data is collected through Driver Hand Held (HH) devices and the Line Haul Central Dispatch network. Be aware that GPS data may not be available during transit depending on certain conditions.

The following table indicates the availability of geo location data returned by the Tracking API:

| Freight Movement (Location) | Geo Location Data Availability | 
| --------------------------- | ------------------------------ |
| Origin Terminal | Yes (Departure only*) No freight at this point.|
| Stops Away From Pickup | Yes (Departure only*) No freight at this point.|
| Pick Up | Yes (Departure only*) |
| Return to Origin Terminal | Yes (Departure only*) |
| Hub(s) | Yes |
| Line Haul Meet Point** | Yes |
| Destination Terminal | Yes |
| Stops away from delivery | Yes (Departure only*)|
| Delivery Location | Yes (Departure only*)|
| | |

\* "Departure only" indicates data is collected when the Estes vehicle has departed the location.

\** Certain Line Haul Meet Point locations may not be on the Central Dispatch network and may not have GPS data. 

Geo Location data is presented in **longitude, latitude** order. 

The following example is presented in this JSON fragment returned from Shipment Tracking and Pickup APIs. 

`    "geoCoordinates": [`
`        "-72.900644",`
`        "41.547504"`
`    ],`

# Push Services (Subscriptions)

Definitions coming soon.


# Data Definitions

Definitions for data fields passed through APIs are listed here by their API object.

Some data fields are classes – they contain other fields within their JSON objects. 

Additional fields within classes are followed by the row *contains*.

## Pickup Request 

| Field | Description |     |
| ----- | ----------- | --- |
| requestNumber | A reference number given to the customer by the time-critical team when they request a time-critical shipment. It’s the number used to identify the request in the system throughout the shipping process. | |
| pro | PRO Number is a pre-assigned, 10-digit freight bill number given to each shipment to serve as a tracking number. PRO is an acronym for Progressive Rotating Order. | |
| status | A class to describe the condition or position of an object. | |
| *contains* | description  | Text describing this status. |
| | reason  | The reason for this status condition or position, expressed as text. |
| | reasonCode  | The reason for this status condition or position, expressed as a code. |
| shipper | This is the address of the pickup location. Although it’s optional, either it or the accountCode must be indicated. If an accountCode is provided, the shipper address (pickup location) is pulled from the Estes account master by the account code. If an address is provided in addition to the account code, the address associated with the account code will override the information provided in the shipperAddress element. NOTE: Shipper contains several classes including name, address and contacts. | |
| *contains* | name  | The name of this branch or division of an organization. |
| | accountCode  | |
| address | A class to define common information related to an address. | |
| *contains* | line  | An unstructured address line. |
| | city  | The name of a city, town, or village. |
| | state  | A territorial division of a country, such as a county or state, expressed as text. |
| | postalCode  | The postal identifier for this address according to the relevant national postal service, such as a ZIP code or Post Code. |
| | country  | The country in which this address is situated. |
| contacts | A class that contains contact information | |
| *contains* | type  | The type of this contract, expressed as text, such as “Cost plus award fee” and “Cost plus fixed fee” from UNCEFACT Contract Type code list. |
| | name  | The name of this contact. It is recommended that this be used for a functional name and not a personal name. |
| | email  | The primary email address of this contact. |
| | phone  | The primary telephone number of this contact. |
| | fax  | The primary fax number of this contact. |
| | receiveNotifications | Boolean |
| | notificationMethod  | This code indicates the method of notification if the receiveNotifications element is enabled for the contact (Y). Valid values are listed below: |
| |  | • E — Email |
| |  | • F — Fax (NOTE Fax-based notifications are unavailable at this time.) |
| requestAction | This is the pickup action to perform. If the request is for Estes to pick up a full trailer, choose HE (to indicate empty) or HL (to indicate loaded). If you need Estes to drop off an empty trailer, choose SE. If the request is for a pickup of freight from your dock that is not a trailer-load, then pass LL (or don’t pass this element, and it will default to LL). If Estes must call to set up an appointment before arriving, then pass AP. Valid values are listed below: | |
| | • AP — Appointment required | |
| | • HE — LTL hook empty | |
| | • HL — LTL hook loaded | |
| | • LL — LTL live load [default] | |
| | • SE — LTL spot/drop empty | |
| paymentTerms | These are the requested payment terms to apply to any resulting shipments picked up. Valid values include: | |
| | • COL — Collect  | |
| | • PPD — Prepaid  | |
| totalPieces |  | |
| totalWeight | The total declared weight of the goods in this consignment, including packaging but excluding the carrier’s equipment. | |
| totalHandlingUnits |  | |
| hazmatFlag | Use this to indicate the requirement to pick up hazardous materials. Cite additional details and specify the identity and type of hazardous materials in the request’s commodity elements area. | |
| expeditedCode | This is an optional code indicating the priority of the resulting shipment after successful pickup. Valid values are listed below: | |
| | • (BLANK) — normal [default] | |
| | • E — Estes Forwarding | |
| | • G — Guaranteed  | |
| | • H — Hot  | |
| whoRequested | This optional code indicates the party that requested the pickup. The following are the valid values: | |
| | • (BLANK) — Unknown  | |
| | • C — Consignee  | |
| | • S — Shipper  | |
| | • 3 — 3rd party  | |
| | • 4 — 4th party  | |
| userName |  | |
| userAccount |  | |
| pickupDate |  | |
| pickupStartTime | This is a 4-digit time with a 2-digit hour and 2-digit minute that indicates the start of the time-window when the client expects Estes to execute the pickup. | |
| pickupEndTime | This is a 4-digit time with a 2-digit hour and 2-digit minute that indicates the end of the time-window when the client expects Estes to execute the pickup. | |
| appointmentHistory | class  | |
| *contains* | startDate  | The date on which this period begins. |
| | startTime  | The time at which this period begins. |
| | endDate  | The date on which this period ends. |
| | endTime  | The time at which this period ends. |
| | createdDate  | |
| | createdTime  | |
| transportEvent | An event associated with this Transportation Status report. | |
| *contains* | driver  | Describes a person responsible for driving the transport means. |
| | driverCoordinates  | |
| | estimatedPickupDate  | |
| | estimatedPickupTime  | |
| | stopsAway  | |
| | lastUpdatedDate  | |
| | lastUpdatedTime  | |
| trailers | The part of the rig used to haul goods. A trailer is hooked to an engine-powered tractor. | |
| *contains* | id  | |
| | length  | Use this optional code if the request directs Estes to hook or drop off a trailer at the pickup location. The following are the valid values: |
| |  | • (BLANK) — Trailer length not specified |
| |  | • 20 — 20 feet |
| |  | • 28 — 28 feet |
| |  | • 40 — 40 feet |
| |  | • 45 — 45 feet |
| |  | • 48 — 48 feet |
| |  | • 53 — 53 feet |
| | type  | This optional code indicates the trailer type if the request requires Estes to hook up or drop off a trailer at the pickup location. The following are the valid values: |
| |  | • (BLANK) — Trailer type not specified |
| |  | • CT — Straight Container |
| |  | • LG — Lift Gate |
| |  | • RD — Roll Door |
| |  | • SD — Side Door |
| |  | • ST — Swing Door Truck |
| referenceNumbers | Used in each referenceNumber element of the optional unbounded referenceNumbers element, this code defines the type of reference number passed in that element. Below are the valid values: | |
| | • BOL — Bill of Lading number | |
| | • DPT — Consignee department number | |
| | • NUM — Shipper ID number | |
| | • PKG — Shipper package ID number | |
| | • PON — Consignee purchase order number | |
| | • RAU — Return authority | |
| | PRO – ask Bala about new codes | |
| | SID  | |
| | EUI  | |
| | LDN  | |
| commodities | class  | |
| *contains* | code  | Used in each commodity element of the optional unbounded commodities element, this unique commodity code defines the type of commodity being passed. It supports custom commodity code values or you may leave it blank (an empty string) and it will default to “MISC” (without quotes). If you are unsure what to pass, use MISC. |
| | packageCode  | Used in each commodity element of the optional unbounded commodities element, this is a unit of measure for the commodity. Valid values are listed below : |
| |  | • BD — Bundles |
| |  | • BG — Bags |
| |  | • BK — Buckets |
| |  | • BL — Bales |
| |  | • BR — Barrels |
| |  | • BX — Boxes |
| |  | • CN — Cans |
| |  | • CR — Crates |
| |  | • CS — Cases |
| |  | • CT — Cartons |
| |  | • CY — Cylinders |
| |  | • DR — Drums |
| |  | • JC — Jerrican |
| |  | • KT — Kits |
| |  | • PC — Pieces |
| |  | • PK — Packages |
| |  | • PL — Pails |
| |  | • PT — Pallets |
| |  | • RE — Reels |
| |  | • RL — Rolls |
| |  | • SK — Skids |
| |  | • TL — Truckload |
| |  | • TO — Totes |
| description |  | |
| hazmat | *Hazardous Materials:* The Transportation Safety Act of 1974 defines hazardous material as “a substance or material in quantity and form which may pose an unreasonable risk to health and safety or property when transported in commerce.” Consists of hazmarCode and hazmatFlag. | |
| *contains* | hazmatCode  | The hazmat element is optional. If the commodity is not hazardous, omit this element from the commodity being passed to prevent validations from requiring its child elements. Used in each commodity element of the optional unbounded commodities element, this is required if the adjacent hazmat flag has a value. It must start with one of the two values listed here to be a valid industry standard hazardous material code. |
| |  | • NA |
| |  | • UN |
| | hazmatFlag  | Used in each commodity element of the optional unbounded commodities element, the hazmat code here represents the type of hazmat commodity. Valid values are listed below: |
| |  | • (BLANK) |
| |  | • C — Corrosive |
| |  | • D — Dangerous |
| |  | • E — Explosives |
| |  | • F — Flammable |
| |  | • G — Flammable gas |
| |  | • H — Hazardous |
| |  | • L — Chlorine |
| |  | • M — Combustible |
| |  | • N — Nonflammable gas |
| |  | • P — Poison |
| |  | • R — Radioactive |
| |  | • S — Flammable solid |
| |  | • X — Oxidizer |
| pieces | The number of pieces of transport handling equipment (pallets, boxes, cases, etc.) in this consignment. | |
| weight | The total declared weight of the goods in this consignment, including packaging but excluding the carrier’s equipment. | |
| nmfcNumber |  | |
| nmfcSubNumber |  | |
| comments | Used in each comment element of the optional unbounded comments element, the type code here indicates the type of comment. Valid values are listed below: | |
| | • CCM — Consignee Comment | |
| | • CSI — Consignee Special Instruction | |
| | • SCM — Shipper/Stop Comment | |
| | • SSI — Shipper/Stop Special Instruction | |
| | • 3CM — 3rd Party Comment | |
| | • 3SI — 3rd Party Special Instruction | |
| | • 4CM — 4th Party Comment | |
| | • 4SI — 4th Party Special Instruction | |
| | • 5CM — 5th Party Comment | |
| | • 5SI — 5th Party Special Instruction | |
| | • 6CM — 6th Party Comment | |
| | • 6SI — 6th Party Special Instruction | |
| addresses | A class to define common information related to an address. | |
| *contains* | type  | Used in each address element of the optional unbounded addresses element, the type code here indicates the type of address being passed. Valid values are listed below: |
| |  | • C — Consignee Address |
| |  | • 3 — 3rd Party Address |
| |  | • 4 — 4th Party Address |
| |  | • 5 — 5th Party Address |
| |  | • 6 — 6th Party Address |
| | line  | An unstructured address line. |
| | city  | The name of a city, town, or village. |
| | state  | A territorial division of a country, such as a county or state, expressed as text. |
| | postalCode  | The postal identifier for this address according to the relevant national postal service, such as a ZIP code or Post Code. |
| | country  | The country in which this address is situated. |
| contacts | Used in each contact element of the optional unbounded contacts element, the type code here indicates the type of contact being passed. Valid values are listed below: | |
| *contains* | • A — Actual Submitter | |
| | • C — Consignee Contact | |
| | • R — Requested Response Contact | |
| | • S — Shipper Contact | |
| | • 3 — Third Party Contact | |
| | • 4 — Fourth Party Contact | |
| | • 5 — Fifth Party Contact | |
| | • 6 — Sixth Party Contact | |
| | name  | The name of this contact. It is recommended that this be used for a functional name and not a personal name. |
| | email  | The primary email address of this contact. |
| | phone  | The primary telephone number of this contact. |
| | fax  | The primary fax number of this contact. |
| | receiveNotifications | Boolean |
| | notificationMethod  | This code indicates the method of notification if the receiveNotifications element is enabled for the contact (Y). Valid values are listed below: |
| |  | • E — Email |
| |  | • F — Fax (NOTE Fax-based notifications are unavailable at this time.) |
| notifications | You can subscribe to automatic notification emails, which are sent at key events throughout the pickup lifecycle. This code indicates the type of event to subscribe to for automatic notifications. (Valid values are listed below.) It’s also possible to pass multiple notification elements with a different type on each to receive notifications when more than one of the following events occur. The notifications will be sent to all contacts passed with the receiveNotifications element set to Y via a valid associated email address. | |
| | • ACC — Terminal accepted pickup | |
| | • BGN — Work has begun | |
| | • RCV — Pickup request received | |
| | • RJT — Pickup request rejected | |
| | • WRK — Pickup request worked (Estes has the freight.) | |
| originTerminal | The terminal at which freight is received from the shipper. | |
| *contains* | number  | |
| | name  | |
| | address  | A class to define common information related to an address. |
| | *contains*  | |
| | line  | An unstructured address line. |
| | city  | The name of a city, town, or village. |
| | state  | A territorial division of a country, such as a county or state, expressed as text. |
| | postalCode  | The postal identifier for this address according to the relevant national postal service, such as a ZIP code or Post Code. |
| | country  | The country in which this address is situated. |
| | telephone  | The primary telephone number of this contact. |
| | fax  | The primary fax number of this contact. |
| | email  | The primary email address of this contact. |

## Shipment History 

| Field | Description |     |
| ----- | ----------- | --- |
| pro | PRO-tracking number | |
| documentReference | The document reference contains additional BOL & PO numbers, and other document references. References are data type strings. Example: “BOL” | |
| *contains* | ID | |
| | documentType | Document type code |
| pickupRequestNumber | | |
| pickupDate | object - The actual pickup date. | |
| status | A class to describe the condition or position of an object. | |
| *contains* | conciseStatus | |
| | expandedStatus | |
| | referenceDate | The reference date for this status. |
| | referenceTime | The reference time for this status. |
| | reasonCode | The reason for this status condition or position, expressed as a code. |
| | reason | The reason for this status condition or position, expressed as text. |
| | quantity | The total number of goods items in this shipment. |
| | packageType | |
| | packageDescription | |
| | receivedBy | |
| estimatedDelivery | Object - The period estimated for delivery. | |
| *contains* | startDate | The date on which this period begins. |
| | startTime | The time at which this period begins. |
| | endDate | The date on which this period ends. |
| | endTime | The time at which this period ends. |
| driverInfo | | |
| *contains* | name | |
| | geoCoordinates | |
| | stopsAway | |
| | driverName | |
| appointment | | |
| *contains* | status | |
| | startDate | |
| | startTime | |
| | endDate | |
| | endTime | |
| appointmentHistory | Object | |
| *contains* | status | |
| | createdDate | |
| | createdTime | |
| | startDate | |
| | startTime | |
| | endDate | |
| | endTime | |
| piecesCount | | |
| totalWeight | | |
| consigneeParty | Object - The designated recipient (customer) of a shipment as indicated on the [Bill of Lading](https://www.estes-express.com/resources/transportation-glossary ##bol). | |
| *contains* | accountNumber | Used in each referenceNumber element of the optional unbounded referenceNumbers element, this code defines the type of reference number passed in that element. Below are the valid values: |
| | | • BOL — Bill of Lading number |
| | | • DPT — Consignee department number |
| | | • NUM — Shipper ID number |
| | | • PKG — Shipper package ID number |
| | | • PON — Consignee purchase order number |
| | | • RAU — Return authority |
| | name | The name of this branch or division of an organization. |
| | address | class |
| | line (items) | An unstructured address line. |
| | city | The name of a city, town, or village. |
| | state | the state abbreviation |
| | postalCode | The postal identifier for this address according to the relevant national postal service, such as a ZIP code or Post Code. |
| shipperParty | Object - The designated shipper as indicated on the [Bill of Lading](https://www.estes-express.com/resources/transportation-glossary ##bol). | |
| *contains* | accountNumber | Used in each referenceNumber element of the optional unbounded referenceNumbers element, this code defines the type of reference number passed in that element. Below are the valid values: |
| | | • BOL — Bill of Lading number |
| | | • DPT — Consignee department number |
| | | • NUM — Shipper ID number |
| | | • PKG — Shipper package ID number |
| | | • PON — Consignee purchase order number |
| | | • RAU — Return authority |
| | name | The name of this branch or division of an organization. |
| | address | class |
| | line (items) | An unstructured address line. |
| | city | The name of a city, town, or village. |
| | state | the state abbreviation |
| | postalCode | The postal identifier for this address according to the relevant national postal service, such as a ZIP code or Post Code. |
| thirdParty | Object - The designated third party of a shipment as indicated on the [Bill of Lading](https://www.estes-express.com/resources/transportation-glossary ##bol). | |
| *contains* | accountNumber | Used in each referenceNumber element of the optional unbounded referenceNumbers element, this code defines the type of reference number passed in that element. Below are the valid values: |
| | | • BOL — Bill of Lading number |
| | | • DPT — Consignee department number |
| | | • NUM — Shipper ID number |
| | | • PKG — Shipper package ID number |
| | | • PON — Consignee purchase order number |
| | | • RAU — Return authority |
| | name | The name of this branch or division of an organization. |
| | address | class |
| | line (items) | An unstructured address line. |
| | city | The name of a city, town, or village. |
| | state | the state abbreviation |
| | postalCode | The postal identifier for this address according to the relevant national postal service, such as a ZIP code or Post Code. |
| destinationTerminal | Object - The terminal that will deliver the shipment within the geographical area that the terminal serves. | |
| *contains:* | number | |
| | name | The name of this branch or division of an organization. |
| | address | references consigneeParty/address - A class to define common information related to an address. |
| | telephone | The primary telephone number of this contact. |
| | fax | The primary fax number of this contact. |
| | email | The primary email address of this contact. |
| interlineInfo | references consigneeParty | |
| freightCharges | | |
| interlinePro | Interline pro for shipment tracking | |
| disclaimers | | |
| movementHistory | Object (this section includes current history and the running history of the movement of freight) | |
| *contains* | id | |
| | description | |
| | location | *contains* |
| | id | |
| | name | |
| | code | |
| | address | *contains* |
| | line | |
| | city | |
| | state | |
| | postalCode | |
| | geoCoordinates | (See chapter on Geo Location) |
| | contact | *contains* |
| | telephone | |
| | fax | |
| | transportEventTypeCode | |
| | statusHistory | *contains* |
| | conciseStatus | |
| | expandedStatus | |
| | referenceDate | |
| | referenceTime | |
| | reasonCode | |
| | reason | |
| | quantity | |
| | packageType | |
| | packageDescription | |

## Invoice 

| Field | Description |     |
| ----- | ----------- | --- |
| invoiceID | An identifier for this document, assigned by the sender. | |
| trailerNumber | | |
| issueDate | The date, assigned by the sender, on which this document was issued. | |
| note | Free-form text pertinent to this document, conveying information that is not contained explicitly in other structures. | |
| pro | PRO Number: A pre-assigned, 10-digit freight bill number given to each shipment to serve as a tracking number. PRO is an acronym for Progressive Rotating Order. | |
| dueDate | The date on which Invoice is due. | |
| consignorAssignedID | An identifier for this consignment, assigned by the consignor. | |
| consigneeParty | Object - A party to which goods are consigned. | |
| *contains* | partyIdentification | An identifier for this party. |
| | partyName | A name for this party. |
| | addressLine | An unstructured address line. |
| | city | The name of a city, town, or village. |
| | postalCode | The postal identifier for this address according to the relevant national postal service, such as a ZIP code or Post Code. |
| | state | A territorial division of a country, such as a county or state, expressed as text. |
| | telephone | The primary telephone number of this contact. |
| shipperParty | references consigneeParty | |
| po | | |
| bol | Bill of Lading - A legal document signed by the shipper and carrier tendering the responsibility of the freight to the carrier. The BOL states pertinent information for the shipment such as the complete address of the shipper and consignee, number of pieces, description, weight, and any hazardous material information. | |
| additionalDocumentReference | The additional document reference contains additional BOL & PO numbers, and other document references | |
| *contains* | documentType | The type of document being referenced, expressed as text. |
| | id | |
| | documentTypeCode | example (BOL) |
| | | |
| accountingSupplierParty | references consigneeParty | |
| accountingCustomerParty | references consigneeParty | |
| allowanceCharge | object - An allowance or charge covered by these delivery terms. | |
| *contains* | discountFunction | |
| | totalDiscount | |
| | totalDiscountPercentage | |
| payableAmount | The amount of the monetary total to be paid. | |
| chargeTotalAmount | The total monetary amount of all charges. | |
| amountPaid | | |
| invoiceLine | object - A line describing an invoice item. | |
| *contains* | id | |
| | note | Free-form text pertinent to this document, conveying information that is not contained explicitly in other structures. |
| | quantity | |
| | lineExtensionAmount | The total amount for this invoice line, including allowance charges but net of taxes. |
| | itemDescription | |
| | hazardousCategoryCode | A code signifying a kind of hazard for a material. |
| | weight | |
| documentReference | A reference to a document associated with this invoice line. | |
| *contains* | documentType | The type of document being referenced, expressed as text. |
| | id | |
| | documentTypeCode | The type of document being referenced, expressed as a code. |
| commodityCode | The harmonized international commodity code for cross border and regulatory (customs and trade statistics) purposes. | |
| firstArrivalPortLocation | object - The first arrival location in a transport. This would be a port for sea, an airport for air, a terminal for rail, or a border post for land crossing. | |
| *contains:* | id | |
| | description | Text describing the attribute that applies to the condition. |
| lastExitPortLocation | references firstArrivalPortLocation | |
| grossWeightMeasure | The entire weight of a shipment including containers and packaging materials. | |
| invoiceType | A code signifying the type of the Invoice. | |
| scacCode | | |
| pickupDate | The actual pickup date. | |
| deliveryDate | The actual date of delivery. | |
| billingTerms | | |
| imageRetrievalResult | A string which indicates an image is available for the retrieved invoice. If “SUCCESS”, there will be data in the images object. | |
| images | object | |
| *contains* | url | The url locater for the image. |
| | documentType | The document type. |
| | data | |
| | contentType | The content type. |

# API Examples

The examples listed here consist of a CURL (https request) statement with necessary parameters or request body followed by a response in JSON format.

Examples are for illustrative purposes only. You need a valid API key and bearer authentication token. See *Accessing Our Apis* for more information.

## Pull an Invoice

Returns specific invoice(s) corresponding to the provided PRO tracking, PO (purchase order) or BOL (bill of lading) number. 
 
### Available Parameters 
 
| Parameter | Passed | Type | Max | Min | Required | Description | 
| --------- | ------ | ---- | --- | --- | -------- | ----------- | 
| pro | query | number | 9999999999 | 0 | N/A | PRO tracking number | 
| latest | query | boolean |  |  | N/A | Set to true to get only the most recent version of the invoice when looking up by PRO number. | 
| po | query | string | 15 | 1 | N/A | Purchase order number | 
| bol | query | string | 25 | 1 | N/A | Bill of lading number | 


```
CURL:

curl --location --request GET 'https://cloudapi.estes-express.com/v1/invoices?pro=000000000' \
--header 'apikey: apikey-here' \
--header 'Authorization: Bearer your-token-here'

RESPONSE SCHEMA:

{
    "data": [
        {
            "invoiceID": "2238130",
            "issueDate": "2019-08-21",
            "pro": "0031928990",
            "dueDate": "2019-09-20",
            "consignorAssignedID": "8007388848",
            "consigneeParty": {
                "partyIdentification": [
                    "B001310"
                ],
                "partyName": "NONSTOP DELIVERY",
                "serviceProvider": {},
                "addressLine": [
                    "333 STRAWBERRY FIELDS ROAD, UN",
                    "UNIT 9"
                ],
                "city": "SEEKONK",
                "postalCode": "02886",
                "state": "RI"
            },
            "shipperParty": {
                "partyIdentification": [
                    "0304497"
                ],
                "partyName": "ARMSTRONG FLOORING INC",
                "serviceProvider": {},
                "addressLine": [
                    "1720 SOUTH MILITARY HIGHWAY",
                    ""
                ],
                "city": "CHESAPEAKE",
                "postalCode": "23320",
                "state": "VA"
            },
            "accountingSupplierParty": {
                "partyIdentification": [
                    ""
                ],
                "partyName": "Estes",
                "serviceProvider": {},
                "addressLine": [
                    "PO Box 25612"
                ],
                "city": "Richmond",
                "postalCode": "23260-5612",
                "state": "VA",
                "telephone": "804.353.1900"
            },
            "accountingCustomerParty": {
                "partyIdentification": [
                    "5067376"
                ],
                "partyName": "ARMSTRONG FLOORING SAP/EDI",
                "serviceProvider": {},
                "addressLine": [
                    "FLOOR PRODUCTS",
                    "PO BOX 3237"
                ],
                "city": "LANCASTER",
                "postalCode": "17604",
                "state": "PA"
            },
            "allowanceCharge": {
                "totalDiscount": "36.61",
                "totalDiscountPercentage": "0.000"
            },
            "payableAmount": 101.84,
            "chargeTotalAmount": 138.45,
            "invoiceLine": [
                {
                    "id": "1",
                    "note": [
                        "SAID TO CONTAIN"
                    ],
                    "quantity": 1,
                    "referenceNumber": [
                        {
                            "ID": "0405278532",
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "ID": "7705386",
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "1",
                    "note": [
                        "SAID TO CONTAIN"
                    ],
                    "quantity": 1,
                    "referenceNumber": [
                        {
                            "ID": "0405278532",
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "ID": "7705386",
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "1",
                    "note": [
                        "SAID TO CONTAIN"
                    ],
                    "quantity": 1,
                    "referenceNumber": [
                        {
                            "ID": "0405278532",
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "ID": "7705386",
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "1",
                    "note": [
                        "SAID TO CONTAIN"
                    ],
                    "quantity": 1,
                    "referenceNumber": [
                        {
                            "ID": "0405278532",
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "ID": "7705386",
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "2",
                    "note": [
                        "TENDERED ON SHIPPER WRAPPED SKIDS"
                    ],
                    "quantity": 4,
                    "referenceNumber": [
                        {
                            "ID": "0405278532",
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "ID": "7705386",
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "2",
                    "note": [
                        "TENDERED ON SHIPPER WRAPPED SKIDS"
                    ],
                    "quantity": 4,
                    "referenceNumber": [
                        {
                            "ID": "0405278532",
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "ID": "7705386",
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "2",
                    "note": [
                        "TENDERED ON SHIPPER WRAPPED SKIDS"
                    ],
                    "quantity": 4,
                    "referenceNumber": [
                        {
                            "ID": "0405278532",
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "ID": "7705386",
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "2",
                    "note": [
                        "TENDERED ON SHIPPER WRAPPED SKIDS"
                    ],
                    "quantity": 4,
                    "referenceNumber": [
                        {
                            "ID": "0405278532",
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "ID": "7705386",
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "3",
                    "note": [
                        "FOAM"
                    ],
                    "weight": 16,
                    "referenceNumber": [
                        {
                            "ID": "0405278532",
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "ID": "7705386",
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "3",
                    "note": [
                        "FOAM"
                    ],
                    "weight": 16,
                    "referenceNumber": [
                        {
                            "ID": "0405278532",
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "ID": "7705386",
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "3",
                    "note": [
                        "FOAM"
                    ],
                    "weight": 16,
                    "referenceNumber": [
                        {
                            "ID": "0405278532",
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "ID": "7705386",
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "3",
                    "note": [
                        "FOAM"
                    ],
                    "weight": 16,
                    "referenceNumber": [
                        {
                            "ID": "0405278532",
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "ID": "7705386",
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "4",
                    "note": [
                        "1CT;"
                    ],
                    "referenceNumber": [
                        {
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "4",
                    "note": [
                        "1CT;"
                    ],
                    "referenceNumber": [
                        {
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "4",
                    "note": [
                        "1CT;"
                    ],
                    "referenceNumber": [
                        {
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "4",
                    "note": [
                        "1CT;"
                    ],
                    "referenceNumber": [
                        {
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "5",
                    "note": [
                        "PRYZM VVATERTRONT SKY SIUE"
                    ],
                    "lineExtensionAmount": 129.61,
                    "weight": 140,
                    "referenceNumber": [
                        {
                            "ID": "0405278532",
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "ID": "7705386",
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "5",
                    "note": [
                        "PRYZM VVATERTRONT SKY SIUE"
                    ],
                    "lineExtensionAmount": 129.61,
                    "weight": 140,
                    "referenceNumber": [
                        {
                            "ID": "0405278532",
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "ID": "7705386",
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "5",
                    "note": [
                        "PRYZM VVATERTRONT SKY SIUE"
                    ],
                    "lineExtensionAmount": 129.61,
                    "weight": 140,
                    "referenceNumber": [
                        {
                            "ID": "0405278532",
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "ID": "7705386",
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "5",
                    "note": [
                        "PRYZM VVATERTRONT SKY SIUE"
                    ],
                    "lineExtensionAmount": 129.61,
                    "weight": 140,
                    "referenceNumber": [
                        {
                            "ID": "0405278532",
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "ID": "7705386",
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "15",
                    "note": [
                        "Fuel Surcharge added at 09.50%"
                    ],
                    "lineExtensionAmount": 8.84,
                    "referenceNumber": [
                        {
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "15",
                    "note": [
                        "Fuel Surcharge added at 09.50%"
                    ],
                    "lineExtensionAmount": 8.84,
                    "referenceNumber": [
                        {
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "15",
                    "note": [
                        "Fuel Surcharge added at 09.50%"
                    ],
                    "lineExtensionAmount": 8.84,
                    "referenceNumber": [
                        {
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                },
                {
                    "id": "15",
                    "note": [
                        "Fuel Surcharge added at 09.50%"
                    ],
                    "lineExtensionAmount": 8.84,
                    "referenceNumber": [
                        {
                            "documentType": "Purchase Order",
                            "documentTypeCode": "PO"
                        },
                        {
                            "documentType": "Bill of Lading",
                            "documentTypeCode": "BOL"
                        }
                    ]
                }
            ],
            "firstArrivalPortLocation": {
                "id": "003",
                "description": "NFK"
            },
            "lastExitPortLocation": {
                "id": "058",
                "description": "SEE"
            },
            "grossWeightMeasure": 156,
            "additionalDocumentReference": [
                {
                    "ID": "0059313059",
                    "documentType": "PUR"
                },
                {
                    "ID": "0059313059",
                    "documentType": "PUR"
                },
                {
                    "ID": "0059313059",
                    "documentType": "PUR"
                },
                {
                    "ID": "0405278532",
                    "documentType": "PON"
                },
                {
                    "ID": "0059313059",
                    "documentType": "PUR"
                },
                {
                    "ID": "0405278532",
                    "documentType": "PON"
                },
                {
                    "ID": "0405278532",
                    "documentType": "PON"
                },
                {
                    "ID": "12.79",
                    "documentType": "DIM"
                },
                {
                    "ID": "0405278532",
                    "documentType": "PON"
                },
                {
                    "ID": "12.79",
                    "documentType": "DIM"
                },
                {
                    "ID": "12.79",
                    "documentType": "DIM"
                },
                {
                    "ID": "12.79",
                    "documentType": "DIM"
                },
                {
                    "ID": "7705386",
                    "documentType": "BOL"
                },
                {
                    "ID": "7705386",
                    "documentType": "BOL"
                },
                {
                    "ID": "7705386",
                    "documentType": "BOL"
                },
                {
                    "ID": "7705386",
                    "documentType": "BOL"
                },
                {
                    "ID": "8007388848",
                    "documentType": "SNO"
                },
                {
                    "ID": "8007388848",
                    "documentType": "SNO"
                },
                {
                    "ID": "8007388848",
                    "documentType": "SNO"
                },
                {
                    "ID": "8007388848",
                    "documentType": "SNO"
                }
            ],
            "bol": "7705386",
            "po": "7705386",
            "deliveryDate": "2019-08-16"
        }
    ],
    "error": {
        "code": 0,
        "message": "",
        "details": ""
    }
}
```


## Create a pickup request


```
CURL:

curl --location --request POST 'https://cloudapi.estes-express.com/v1/pickup-requests' \
--header 'apikey: apikey-here' \
--header 'Authorization: Bearer your-token-here' \
--header 'Content-Type: application/json' \
--data-raw '{
    "requestNumber": "1234",
    "shipper": {
        "shipperName": "ACCEPTANCE TESTER",
        "shipperAddress": {
            "addressInfo": {
                "addressLine1": "30 FIREMENS WAY",
                "city": "POUGHKEEPSIE",
                "stateProvince": "NY",
                "postalCode": 12603,
                "countryAbbrev": "US"
            }
        },
        "shipperContacts": {
            "shipperContact": [
                {
                    "contactInfo": {
                        "name": {
                            "firstName": "SARAH",
                            "middleName": "RANDAZZO X115",
                            "lastName": "INC"
                        },
                        "email": "info@promptlogistics.com",
                        "phone": {
                            "areaCode": 845,
                            "number": 4736780,
                            "extension": 1234
                        },
                        "receiveNotifications": "Y",
                        "notificationMethod": "E"
                    }
                }
            ]
        }
    },
    "requestAction": "LL",
    "paymentTerms": "PPD",
    "pickupDate": "2020-07-24",
    "pickupStartTime": 1000,
    "pickupEndTime": 1600,
    "totalPieces": 188,
    "totalWeight": 3720,
    "totalHandlingUnits": 8,
    "whoRequested": "3",
    "referenceNumbers": {
        "referenceNumber": [
            {
                "referenceInfo": {
                    "type": "BOL",
                    "value": "407519",
                    "required": "N"
                }
            }
        ]
    },
    "commodities": {
        "commodity": [
            {
                "commodityInfo": {
                    "code": "100",
                    "packageCode": "PT",
                    "description": "NOVELTIES",
                    "pieces": 188,
                    "weight": 3720
                }
            }
        ]
    },
    "addresses": {
        "address": [
            {
                "addressInfo": {
                    "addressType": "C",
                    "addressLine1": "2110 LINCOLN HWY",
                    "city": "EDISON",
                    "stateProvince": "NJ",
                    "postalCode": 12603,
                    "countryAbbrev": "US"
                }
            },
            {
                "addressInfo": {
                    "addressType": 3,
                    "addressLine1": "212 2nd Suite 205A",
                    "city": "Lakewood",
                    "stateProvince": "NJ",
                    "postalCode": 12603,
                    "countryAbbrev": "US"
                }
            }
        ]
    },
    "contacts": {
        "contact": [
            {
                "contactInfo": {
                    "contactType": "S",
                    "name": {
                        "firstName": "SARAH",
                        "middleName": "RANDAZZO X115 BABYVISION",
                        "lastName": "INC"
                    },
                    "email": "info@promptlogistics.com",
                    "phone": {
                        "areaCode": 845,
                        "number": 4736780,
                        "extension": 1234
                    },
                    "receiveNotifications": "Y",
                    "notificationMethod": "E"
                }
            },
            {
                "contactInfo": {
                    "contactType": "C",
                    "name": {
                        "firstName": "NEWPORT",
                        "lastName": "LOGISTICS"
                    },
                    "email": "info@promptlogistics.com",
                    "phone": {
                        "areaCode": 732,
                        "number": 2871440,
                        "extension": 225
                    },
                    "receiveNotifications": "Y",
                    "notificationMethod": "E"
                }
            },
            {
                "contactInfo": {
                    "contactType": 3,
                    "name": {
                        "firstName": "Prompt",
                        "lastName": "Logistics"
                    },
                    "email": "info@promptlogistics.com",
                    "phone": {
                        "areaCode": 732,
                        "number": 9058686,
                        "extension": 1234
                    },
                    "receiveNotifications": "Y",
                    "notificationMethod": "E"
                }
            },
            {
                "contactInfo": {
                    "contactType": "A",
                    "name": {
                        "firstName": "Michelle",
                        "lastName": "Gutin"
                    },
                    "email": "michael@promptlogistics.com",
                    "phone": {
                        "areaCode": 732,
                        "number": 9058686,
                        "extension": 1234
                    },
                    "receiveNotifications": "Y",
                    "notificationMethod": "E"
                }
            }
        ]
    }
}'


RESPONSE SCHEMA:

{
    "data": {
        "requestNumber": "66307782"
    },
    "error": {
        "code": 0,
        "message": "",
        "details": "",
        "validationFailures": null
    }
}
```


## Update a pickup request



```
CURL:

curl --location --request PUT 'https://cloudapi.estes-express.com/v1/pickup-requests' \
--header 'apikey: apikey-here' \
--header 'Authorization: Bearer your-token-here' \
--header 'Content-Type: application/json' \
--data-raw '{
    "requestNumber": "66263321",
    "shipper": {
        "shipperName": "ACCEPTANCE TESTER",
        "shipperAddress": {
            "addressInfo": {
                "addressLine1": "30 FIREMENS WAY",
                "city": "POUGHKEEPSIE",
                "stateProvince": "NY",
                "postalCode": 12603,
                "countryAbbrev": "US"
            }
        },
        "shipperContacts": {
            "shipperContact": [
                {
                    "contactInfo": {
                        "name": {
                            "firstName": "SARAH",
                            "middleName": "RANDAZZO X115",
                            "lastName": "INC"
                        },
                        "email": "info@promptlogistics.com",
                        "phone": {
                            "areaCode": 845,
                            "number": 4736780,
                            "extension": 1234
                        },
                        "receiveNotifications": "Y",
                        "notificationMethod": "E"
                    }
                }
            ]
        }
    },
    "requestAction": "LL",
    "paymentTerms": "PPD",
    "pickupDate": "2020-07-24",
    "pickupStartTime": 1000,
    "pickupEndTime": 1600,
    "totalPieces": 188,
    "totalWeight": 3720,
    "totalHandlingUnits": 8,
    "whoRequested": "3",
    "referenceNumbers": {
        "referenceNumber": [
            {
                "referenceInfo": {
                    "type": "BOL",
                    "value": "407519",
                    "required": "N"
                }
            }
        ]
    },
    "commodities": {
        "commodity": [
            {
                "commodityInfo": {
                    "code": "100",
                    "packageCode": "PT",
                    "description": "NOVELTIES",
                    "pieces": 188,
                    "weight": 3720
                }
            }
        ]
    },
    "addresses": {
        "address": [
            {
                "addressInfo": {
                    "addressType": "C",
                    "addressLine1": "2110 LINCOLN HWY",
                    "city": "EDISON",
                    "stateProvince": "NJ",
                    "postalCode": 12603,
                    "countryAbbrev": "US"
                }
            },
            {
                "addressInfo": {
                    "addressType": 3,
                    "addressLine1": "212 2nd Suite 205A",
                    "city": "Lakewood",
                    "stateProvince": "NJ",
                    "postalCode": 12603,
                    "countryAbbrev": "US"
                }
            }
        ]
    },
    "contacts": {
        "contact": [
            {
                "contactInfo": {
                    "contactType": "S",
                    "name": {
                        "firstName": "SARAH",
                        "middleName": "RANDAZZO X115 BABYVISION",
                        "lastName": "INC"
                    },
                    "email": "info@promptlogistics.com",
                    "phone": {
                        "areaCode": 845,
                        "number": 4736780,
                        "extension": 1234
                    },
                    "receiveNotifications": "Y",
                    "notificationMethod": "E"
                }
            },
            {
                "contactInfo": {
                    "contactType": "C",
                    "name": {
                        "firstName": "NEWPORT",
                        "lastName": "LOGISTICS"
                    },
                    "email": "info@promptlogistics.com",
                    "phone": {
                        "areaCode": 732,
                        "number": 2871440,
                        "extension": 225
                    },
                    "receiveNotifications": "Y",
                    "notificationMethod": "E"
                }
            },
            {
                "contactInfo": {
                    "contactType": 3,
                    "name": {
                        "firstName": "Prompt",
                        "lastName": "Logistics"
                    },
                    "email": "info@promptlogistics.com",
                    "phone": {
                        "areaCode": 732,
                        "number": 9058686,
                        "extension": 1234
                    },
                    "receiveNotifications": "Y",
                    "notificationMethod": "E"
                }
            },
            {
                "contactInfo": {
                    "contactType": "A",
                    "name": {
                        "firstName": "Michelle",
                        "lastName": "Gutin"
                    },
                    "email": "michael@promptlogistics.com",
                    "phone": {
                        "areaCode": 732,
                        "number": 9058686,
                        "extension": 1234
                    },
                    "receiveNotifications": "Y",
                    "notificationMethod": "E"
                }
            }
        ]
    }
}'

RESPONSE SCHEMA:

{
    "data": {
        "requestNumber": "66307782"
    },
    "error": {
        "code": 0,
        "message": "",
        "details": "",
        "validationFailures": null
    }
}
```


## Cancel a pickup request

Pass the pickup request number in the call.


```
CURL:

curl --location --request DELETE 'https://cloudapi.estes-express.com/v1/pickup-requests/66263321' \
--header 'apikey: apikey-here' \
--header 'Authorization: Bearer your-token-here' \
--header 'Content-Type: application/json' \
--data-raw '{
    "requestNumber": "66307782",
    "comment": {
        "type": "ABC",
        "text": "Sample text for comment"
    }
}'

RESPONSE SCHEMA:

{
    "data": {
        "requestNumber": "66307782"
    },
    "error": {
        "code": 0,
        "message": "",
        "details": "",
        "validationFailures": null
    }
}
```


## Get Pickup Status

Pass the pickup request number in the call.


```
CURL:

curl --location --request GET 'https://cloudapi.estes-express.com/v1/pickup-requests/66263321' \
--header 'apikey: apikey-here' \
--header 'Authorization: Bearer your-token-here'

RESPONSE SCHEMA:

{
    "data": [
        {
            "requestNumber": "66307782",
            "pro": "",
            "status": {
                "description": "No freight received",
                "reason": "",
                "reasonCode": ""
            },
            "shipper": {
                "name": "ACCEPTANCE TESTER",
                "accountCode": "0100777",
                "address": {
                    "line": [
                        "30 FIREMENS WAY"
                    ],
                    "city": "POUGHKEEPSIE",
                    "state": "NY",
                    "postalCode": "12603",
                    "country": "US"
                },
                "contacts": [
                    {
                        "type": "S",
                        "name": "SARAH RANDAZZO X115 INC",
                        "email": "info@promptlogistics.com",
                        "phone": "8454736780 x 1234",
                        "fax": "",
                        "receiveNotifications": "Y",
                        "notificationMethod": "E"
                    },
                    {
                        "type": "S",
                        "name": "SARAH RANDAZZO X115 BABYVISION INC",
                        "email": "info@promptlogistics.com",
                        "phone": "8454736780 x 1234",
                        "fax": "",
                        "receiveNotifications": "Y",
                        "notificationMethod": "E"
                    },
                    {
                        "type": "S",
                        "name": "SARAH RANDAZZO X115 BABYVISION INC",
                        "email": "info@promptlogistics.com",
                        "phone": "8454736780 x 1234",
                        "fax": "",
                        "receiveNotifications": "Y",
                        "notificationMethod": "E"
                    },
                    {
                        "type": "S",
                        "name": "SARAH RANDAZZO X115 BABYVISION INC",
                        "email": "info@promptlogistics.com",
                        "phone": "8454736780 x 1234",
                        "fax": "",
                        "receiveNotifications": "Y",
                        "notificationMethod": "E"
                    }
                ]
            },
            "requestAction": "LL",
            "paymentTerms": "PPD",
            "totalPieces": 188,
            "totalWeight": 3720,
            "totalHandlingUnits": 8,
            "hazmatFlag": "N",
            "expeditedCode": "",
            "whoRequested": "3",
            "userName": "OMEGA1",
            "userAccount": "2895833",
            "pickupDate": "2020-08-26",
            "pickupStartTime": "10:00:00-04:00",
            "pickupEndTime": "16:00:00-04:00",
            "appointmentHistory": [
                {
                    "startDate": "2020-08-26",
                    "startTime": "10:00:00-04:00",
                    "endDate": "2020-08-26",
                    "endTime": "16:00:00-04:00",
                    "createdDate": "2020-08-26",
                    "createdTime": "19:25:07+0000"
                }
            ],
            "transportEvent": {
                "driver": "",
                "driverCoordinates": [
                    "",
                    ""
                ],
                "estimatedPickupDate": "",
                "estimatedPickupTime": "",
                "stopsAway": "",
                "lastUpdatedDate": "",
                "lastUpdatedTime": ""
            },
            "trailers": [],
            "referenceNumbers": [
                {
                    "type": "BOL",
                    "value": "407519"
                },
                {
                    "type": "BOL",
                    "value": "407519"
                },
                {
                    "type": "BOL",
                    "value": "407519"
                }
            ],
            "commodities": [
                {
                    "code": "100",
                    "packageCode": "PT",
                    "description": "NOVELTIES",
                    "hazmat": {
                        "hazmatCode": "",
                        "hazmatFlag": ""
                    },
                    "pieces": 188,
                    "weight": 3720,
                    "nmfcNumber": "",
                    "nmfcSubNumber": ""
                },
                {
                    "code": "100",
                    "packageCode": "PT",
                    "description": "NOVELTIES",
                    "hazmat": {
                        "hazmatCode": "",
                        "hazmatFlag": ""
                    },
                    "pieces": 188,
                    "weight": 3720,
                    "nmfcNumber": "",
                    "nmfcSubNumber": ""
                },
                {
                    "code": "100",
                    "packageCode": "PT",
                    "description": "NOVELTIES",
                    "hazmat": {
                        "hazmatCode": "",
                        "hazmatFlag": ""
                    },
                    "pieces": 188,
                    "weight": 3720,
                    "nmfcNumber": "",
                    "nmfcSubNumber": ""
                }
            ],
            "comments": [
                {
                    "text": "Customer Cancelled P/U Request"
                },
                {
                    "text": "Sample text for comment"
                }
            ],
            "addresses": [
                {
                    "type": "A",
                    "line": [],
                    "city": "",
                    "state": "",
                    "postalCode": "",
                    "country": ""
                },
                {
                    "type": "C",
                    "line": [
                        "2110 LINCOLN HWY"
                    ],
                    "city": "EDISON",
                    "state": "NJ",
                    "postalCode": "12603",
                    "country": "US"
                },
                {
                    "type": "3",
                    "line": [
                        "212 2nd Suite 205A"
                    ],
                    "city": "Lakewood",
                    "state": "NJ",
                    "postalCode": "12603",
                    "country": "US"
                }
            ],
            "contacts": [
                {
                    "type": "A",
                    "name": "Michelle  Gutin",
                    "email": "michael@promptlogistics.com",
                    "phone": "7329058686 x 1234",
                    "fax": "",
                    "receiveNotifications": "Y",
                    "notificationMethod": "E"
                },
                {
                    "type": "C",
                    "name": "NEWPORT  LOGISTICS",
                    "email": "info@promptlogistics.com",
                    "phone": "7322871440 x 225",
                    "fax": "",
                    "receiveNotifications": "Y",
                    "notificationMethod": "E"
                },
                {
                    "type": "3",
                    "name": "Prompt  Logistics",
                    "email": "info@promptlogistics.com",
                    "phone": "7329058686 x 1234",
                    "fax": "",
                    "receiveNotifications": "Y",
                    "notificationMethod": "E"
                }
            ],
            "notifications": [],
            "originTerminal": {
                "number": "061",
                "name": "NEWBURGH",
                "address": {
                    "line": [
                        "12 Stone Castle Road"
                    ],
                    "city": "Rock Tavern",
                    "state": "NY",
                    "postalCode": "12575",
                    "country": "US"
                },
                "telephone": "(845) 567-1080",
                "fax": "18455676275",
                "email": "custsrv@estes-express.com"
            }
        }
    ],
    "error": {
        "code": 0,
        "message": "",
        "details": "",
        "validationFailures": null
    }
}
```


## Get shipment history


```
CURL:

curl --location --request GET 'https://cloudapi.estes-express.com/v1/shipments/status?pro=1710510386' \
--header 'apikey: apikey-here' \
--header 'Authorization: Bearer your-token-here'

RESPONSE SCHEMA:

{
    "data": [
        {
            "pro": "1710510386",
            "documentReference": [
                {
                    "ID": "0055178413",
                    "documentType": "PUR"
                },
                {
                    "ID": "LOD222",
                    "documentType": "LOD"
                },
                {
                    "ID": "005123221",
                    "documentType": "PON"
                },
                {
                    "ID": "39.77",
                    "documentType": "DIM"
                },
                {
                    "ID": "817321379",
                    "documentType": "BOL"
                }
            ],
            "status": {},
            "shipmentStatusTimestamp": " ",
            "estimatedDelivery": {},
            "stopsAway": "2 Stops Away",
            "dimensionalWeight": "648",
            "consigneeParty": {
                "referenceNumber": "4508113",
                "address": {
                    "city": "JACKSONVILLE",
                    "state": "FL",
                    "postalCode": "32219"
                }
            },
            "shipperParty": {
                "referenceNumber": "9441301",
                "address": {
                    "city": "SOUTH BEND",
                    "state": "IN",
                    "postalCode": "46628"
                }
            },
            "destinationTerminal": {
                "number": "045",
                "name": "Jacksonville",
                "address": {}
            },
            "interlineInfo": {
                "referenceNumber": "SCAC333"
            },
            "interlinePro": "ip-12799999"
        }
    ],
    "error": {
        "code": 0,
        "message": "",
        "details": ""
    }
}
```
