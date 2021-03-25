**WARNING: This documentation is early access and is under active development.**
# [![NETCRED LOGO](https://netcredbrasil.com.br/wp-content/uploads/2017/01/NETCRED-Meios-de-pagamento.png)](https://netcredbrasil.com.br/)

[*Netcred*](https://netcredbrasil.com.br/) is a Brazillian company focused on the Payment service segment for the Industry and Retail sector.
Our mission are acting as a facilitator and payment service agent in operations using credit card, debt, billet and others. 


- Facilitator of commerce, industry and resellers.
- Credit card, debt card and billet solution system, in a presencial way and online.
- Creation of a new sales strategy with the latest technologies in the forms of payment service.

We're compromisse in finding new and strategic solutions for any client and merch segment. We know this solutions must be appropriate to Individual Payment Way of each one of the Comerce Relationship Trade. 


# API


This document serves as auxiliary documentation for NETCRED’s API, it should be used in conjunction to the [*Playground*](https://sandbox.netcredbrasil.com.br/), in order to get the most out of the experience. This document will get you acquainted to creating charges, managing companies, marketplaces and financial contracts through NETCRED's ecosystem.

## Overview
The core concept needed for integration with this API is GraphQL. GraphQL is a query language for APIs and a runtime for fulfilling those queries with your existing data. GraphQL provides a complete and understandable description of the data, and gives clients the power to ask for exactly what they need and nothing more. You can learn more about it in the [*GraphQL Docs*](https://graphql.org/).


## Tutorials


A set of guides that will hopefully help you in the process of integration with this API.

Authentication takes place via **JWT** token, more details on this format at [*JWT Docs*](https://jwt.io/).

To authenticate you need to execute a tokenAuth request with your username and password. By a successful request, you receive a token to authenticate in other requests, it does lasts 24 hours from the moment of it's creation. 

Subsequent requests need the header  **"Authorization": "JWT {*your token*}"**.

The token can be refreshed for another 24 hours using the refreshToken* request (before it expires, of course), and you can check the time until its expiration using verifyToken.

For a better knowledge you can observe this diagram:

![Image](https://raw.githubusercontent.com/netcredbrasil/docs/main/images/AUTHENTICATION.jpg)

*Observation: If expired, the token needs to be generated again.*


## Error Codes


When a *Error* happens, it will appear a **Error Code**. *Error codes* will help in the process of understanding the problem and how you can fix it. As an Example:

>PAYMENT_METHOD_INVALID = "Payment method is unknown"

When any mutation are made, you should retrieve the *errors* array, composed by "field" and "message", when running that mutation and a *error* proceed, will be displayed an **Error Code** in the results, compose by the name of the code and a quick description. 

A list with all the custom errors can be found directly in our Postman documentation.


*Observation: An Error can be sorted in different ways and when a error are not expected a syntax error are a point that needed to be addressed.*


## UserType and Companies


very User needs to have an *UserType*, and even with the ambiguous name, an *UserType* is types of Company that an User needs to be associated with. 
To understand the companies types and how they correlate with them, you must have to know how they work, you will be able to find a complete description of each part of the companies in our Postman documentation.


A **COMPANY** can be a **MERCHANT**, **MARKETPLACE**, **FACILITATOR**, **FINANCIER** or a **COMISSIONED**. And knowing all this types you need to know how each one of them are correlated each other, as viewed in this diagram:

![Image](https://raw.githubusercontent.com/netcredbrasil/docs/main/images/COMPANY%20TYPES.jpg)


- A *FACILITATOR*, can intermediate a *MERCHANT*, *MARKETPLACE*, *FINANCIER* or a *COMISSIONED*;
- A *MERCHANT* can be part of a *MARKETPLACE*;
- A *MERCHANT* can be financed by a *FINANCIER*;
- A *MERCHANT* can comission a *COMISSIONED*;

Knowing all the types of Companies and how they work together, an useful information is the state of this companies. This is called *CompanyState* and this are them:

- *ACTIVE* - The company is active;
- *ACTIVE_MONITORED* - The company is Active with monitoring;
- *INACTIVE* - The company is inactive;
- *SUSPENDED* - The company is suspended;
- *AWAITING_APPROVAL* - The company is awaiting approval;



**You can find full documentation [*Here!*](https://documenter.getpostman.com/view/14324610/TW6urARy#intro)**
