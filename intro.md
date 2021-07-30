# Introduction

Our APIs are a fast and easy way to integrate our shipping functionality into
your business applications and websites. Each API provides access to Estes
functionality, allowing you to bypass the traditional HTML forms process and
make shipping with Estes a more convenient solution.

# Accessing Our APIs

To use our APIs, you will need to generate an API key for the production
environment and another API key for the test environment. This API key is used
for all APIs. These keys are the only ones needed to communicate with our APIs.

(API keys are not used with Estes legacy web services. To review older web
services, see <https://www.estes-express.com/resources/digital-services/api/index>.)

-   If you are a TMS provider who wants to connect to Estes APIs on behalf of
    multiple customers using a client ID, see (Transportation Management
    System) **TMS API Customers**  

-   If you are an individual customer who wants to connect to Estes APIs directly
    using their MyEstes username and password to create an API key, see
    **Individual/Direct API Customers**

## TMS API Customers

Obtain your API key by providing the following information in an email
to <WebSupport@estes-express.com>:

-   Developer Name
-   Developer Email
-   Developer Title
-   Developer Company

You will receive two emails with a client ID and client secret, one for test
environment and another for production environment.].

See the next steps, How to Create and Retrieve Your API Key

### How To Create Your API Key

With Postman or a similar API tool, pass your client ID and client secret
using **Basic Authentication** using the following method:

Production example only:

` curl --request POST 'https://cloudapi.estes-express.com/apikey'  `
` --header 'Content-Type: application/json'  `
` --header 'Authorization: Basic `
` ZThkNmM4Y2MtMDY3ZC00ZmY4LTgxYzMtNWJmNjAxNjUzYjYwOjUyZmRmYzA3LTIxODItNjU0Zi0xNjNmLTVmMGY5YTYyMWQ3Mg' `

Test example only:

` curl --request POST 'https://uat-cloudapi.estes-express.com/apikey' ` 
` --header 'Content-Type: application/json'  `
` --header 'Authorization: Basic `
` ZThkNmM4Y2MtMDY3ZC00ZmY4LTgxYzMtNWJmNjAxNjUzYjYwOjUyZmRmYzA3LTIxODItNjU0Zi0xNjNmLTVmMGY5YTYyMWQ3Mg' `

In the response, you will receive an API Key, your Client ID and a new Client Secret.

*Important: This new Client Secret replaces the secret sent in the previous e-mail.*

Store this new Client Secret so you may remember it.

### How To Retrieve Your API Key

If you lost the API Key information, use the GET method for /apikey to retrieve it.

Do not forget to use your Client ID and new Client Secret.

Production example only:

` curl --request GET 'https://cloudapi.estes-express.com/apikey' ` 
` --header 'Content-Type: application/json' ` 
` --header 'Authorization: Basic `
` ZThkNmM4Y2MtMDY3ZC00ZmY4LTgxYzMtNWJmNjAxNjUzYjYwOjUyZmRmYzA3LTIxODItNjU0Zi0xNjNmLTVmMGY5YTYyMWQ3Mg' `

Test example only:

` curl --request GET 'https://uat-cloudapi.estes-express.com/apikey' ` 
` --header 'Content-Type: application/json'  `
` --header 'Authorization: Basic `
` ZThkNmM4Y2MtMDY3ZC00ZmY4LTgxYzMtNWJmNjAxNjUzYjYwOjUyZmRmYzA3LTIxODItNjU0Zi0xNjNmLTVmMGY5YTYyMWQ3Mg' `

## Individual/Direct API Customers

For individual or direct customers, you will need your MyEstes Username and
MyEstes Password. If you do not have a MyEstes profile, you can [sign up for one
here](https://www.estes-express.com/myestes/home/login).

### Generating API Keys for Individual/Direct Customers

To generate an API Key for the *production* environment, submit a POST request
to the following URL with your MyEstes Username and MyEstes Password as the
username and password in the basic authorization header. 

See this example:

` curl -u myEstes-username:myEstes-password -H "accept: application/json" -X POST `
` "https://cloudapi.estes-express.com/v1/api-key" `

To generate an API Key for the *test* environment, submit a POST request to the
following URL with your MyEstes Username and MyEstes Password as the username
and password in the basic authorization header. 

See this example:

` curl -u myEstes-username:myEstes-password -H "accept: application/json" -X POST `
` "https://uat-cloudapi.estes-express.com/v1/api-key" `

The response will contain the API Key for the chosen environment.

### Retrieving API Keys for Individual/Direct Customers

To retrieve a previously issued API Key for production environment , submit a
GET request to the following URL with your MyEstes Username and MyEstes Password
as the username and password in the basic authorization header. See this CURL
example (for test environment, you need to change the domain to:
*https://uat-cloudapi.estes-express.com*):

` curl -u myEstes-username:myEstes-password -H "accept: application/json" -X GET `
` "https://cloudapi.estes-express.com/v1/api-key" `

To change the previously issued API Key for production environment, submit a
DELETE request to the following URL with your MyEstes Username and MyEstes
Password as the username and password in the basic authorization header. (For
test environment, you need to change the domain to:
*https://uat-cloudapi.estes-express.com*):

` curl -u myEstes-username:myEstes-password -H "accept: application/json" -X `
` DELETE "https://cloudapi.estes-express.com/v1/api-key" `

Then submit a POST request to generate a new key as explained above.

Remember that you must pass the API Key in a header while making requests to the
other APIs on the platform. See this example for production:

` curl -H "accept: application/json" -H "apikey: *your-api-key*" -X GET `
` <https://cloudapi.estes-express.com/v1/invoices?pro=1234567890> `

See this example for test:

` curl -H "accept: application/json" -H "apikey: *your-api-key*" -X GET `
` <https://uat-cloudapi.estes-express.com/v1/invoices?pro=1234567890> `

### Using API Keys (For TMS and Individual/Direct Customers)

**Step 1**

When using our APIs and Web Services, you must pass the API Key using the
/authenticate method to initially request a bearer token.

Production environment example:

` curl -X POST "https://cloudapi.estes-express.com/authenticate" -H "accept: `
` application/json" -H "apikey: 0101010101" `

Test environment example:

` curl -X POST "https://uat-cloudapi.estes-express.com/authenticate" -H "accept: `
` application/json" -H "apikey: 0101010101" `

The response JSON will contain the bearer token.

Bearer Token JSON Sample  

```json  
{  
"access_token":
"eyJhbGciOiJSUzI1NiIsImtpZCI6Imp3dC1zaWduLWNlcnQifQ.eyJzY29wZSI6IiIsImNsaWVudF9pZCI6ImtvbmciLCJpc3MiOiJodHRwczovL2ZlZGVyYXRpb24tcWEuZ3NrLmNvbSIsImV4cCI6MTUzOTk3MzQyM30.IRvv0m8QKuOSDbhnlYx11bdvjk3PJBgz0cV7cSO4c1Phxfo4dRvLBvKx3TBnlaHwNYx4k3BcPEP5yDeflEVGVAhM0Is1potXWJfTQsH4PECZHEJNa7eoJFMKo9FKOutLoPg5avY2V0Oq0EU1wO8cTfrC2hNyJxfMMAYtK7pfB0u_a3ZyWLLWH9LN6xztYM86eh7QavHyns3__-uGy0O-imFDJ3Oi0SdKA1XYQDnqNhvN8J9omOVVMxEBuRdTeldM0lbeLxpWmXybQotIbMFGRVFUrwSIU6OxPA3wHyuL6F7p53C2ZsJXP463Sx2Y-9SILvVsuFtKWiUjbUn2--141g",  
"token_type": "Bearer",  
"expires_in": 35999  
}
```

**Step 2**

Include the bearer token with your API requests.

### Example: Using Your API Key and Bearer Token with Shipment Tracking

**GET ​/v1​/shipments/history**

This method returns shipment tracking details associated with an account.

The **Authorization** parameter {TOKEN_HERE} is the bearer token returned after
requesting authentication.

The **apikey** parameter is your API key.

Production environment example:

` curl -X GET "https://cloudapi.estes-express.com/v1/shipments/history?pro=0000000000" -H `
` "accept: application/json" -H "A `

Test environment example:

` curl -X GET "https://uat-cloudapi.estes-express.com/v1/shipments/history?pro=0000000000" -H `
` "accept: application/json" -H "A `


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
