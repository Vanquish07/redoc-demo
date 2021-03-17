# Introduction

Our APIs are a fast and easy way to integrate our shipping functionality into your business applications and websites. Each API provides access to Estes functionality, allowing you to bypass the traditional HTML forms process and make shipping with Estes a more convenient solution.

# Accessing Our APIs

To use our APIs, you will need to generate an API key for the production environment and another API key for the test environment. This API key is used for all APIs. These keys are the only ones needed to communicate with our APIs.
(API keys are not used with Estes legacy web services. To review older web services, see
<https://www.estes-express.com/resources/digital-services/api/index>.)

-   If you are a Transportation Management System (TMS) API customer (these are TMS providers who want to connect to Estes APIs on behalf of multiple customers need to use a client ID)

-   If you are an Individual/Direct API customer (these are individual customers who want to connect to Estes APIs directly who use their MyEstes username and password to create an API key)

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


