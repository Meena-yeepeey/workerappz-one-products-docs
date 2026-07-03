# Get Exchange Rate

### Description

The Get Exchange Rate API is used to retrieve the real-time exchange rate and transaction calculation details for a specific transaction corridor.

This API calculates the conversion value between the sending currency and receiving currency based on the provided sending amount and transaction configuration.

In addition to the exchange rate, the API also returns:

* Service fees
* Margin values
* Receiving amount
* Final payable amount

This API is typically called before transaction creation to display the final transaction calculation and payout details to the customer.

The exchange rate and calculation may vary depending on:

* Sending currency
* Receiving currency
* Sending country
* Agent configuration
* Corridor setup
* Margin configuration
* Service fee configuration

This API helps ensure transparent transaction pricing and accurate payout calculations before processing a remittance transaction.

***

### Endpoint

```
POST /api/v1/getexchangerate
```

***

### Headers

| Header        | Value                |
| ------------- | -------------------- |
| Authorization | Bearer `<JWT_TOKEN>` |
| Content-Type  | application/json     |

### Request Body

```
{
  "sendingAmount": 1,
  "sendingCurrency": "USD",
  "receivingCurrency": "AUD",
  "sendingAgentId": "WASMXXXX",
  "sendCountry": "Australia"
}
```

***

### Request Field Description

<table><thead><tr><th width="165.8499755859375">Field</th><th width="111.75">Type</th><th width="105.75">Required</th><th>Description</th></tr></thead><tbody><tr><td>sendingAmount</td><td>decimal</td><td>Yes</td><td>Amount entered by the sender for the transaction.</td></tr><tr><td>sendingCurrency</td><td>string</td><td>Yes</td><td>Currency code of the sending transaction amount.</td></tr><tr><td>receivingCurrency</td><td>string</td><td>Yes</td><td>Currency code of the beneficiary payout amount.</td></tr><tr><td>sendingAgentId</td><td>string</td><td>Yes</td><td>Unique identifier of the sending agent initiating the transaction request.</td></tr><tr><td>sendCountry</td><td>string</td><td>Yes</td><td>Country from which the transaction is being initiated.</td></tr></tbody></table>

### Exchange Rate Calculation

The API calculates transaction values based on:

* Currency conversion rate
* Configured service fees
* Margin values
* Agent and corridor configuration

The response values are dynamically generated according to the configured payout corridor and pricing rules.

### Sample Success Response

```
{
  "status": "SUCCESS",
  "statusCode": 200,
  "message": "Exchange Rate Fetched Successfully!",
  "exchange_rate": "0.601127",
  "service_fees": "0.473126",
  "Margin_value": "0.806325",
  "sending_currency": "USD",
  "receiving_currency": "AUD",
  "sending_amount": "1.000000",
  "receiving_amount": "0.601127",
  "final_Rate_Payable": "1.473126"
}
```

***

### Success Response Description

<table><thead><tr><th width="177.71661376953125">Field</th><th width="143.16668701171875">Type</th><th>Description</th></tr></thead><tbody><tr><td>status</td><td>string</td><td>Represents the overall API response status.</td></tr><tr><td>statusCode</td><td>integer</td><td>Status code returned by the API request.</td></tr><tr><td>message</td><td>string</td><td>Response message describing the request result.</td></tr><tr><td>exchange_rate</td><td>decimal</td><td>Exchange rate applied for the selected currency corridor.</td></tr><tr><td>service_fees</td><td>decimal</td><td>Service fee applied to the transaction.</td></tr><tr><td>Margin_value</td><td>decimal</td><td>Margin value applied during exchange rate calculation.</td></tr><tr><td>sending_currency</td><td>string</td><td>Currency code of the sending amount.</td></tr><tr><td>receiving_currency</td><td>string</td><td>Currency code of the receiving amount.</td></tr><tr><td>sending_amount</td><td>decimal</td><td>Amount entered by the sender.</td></tr><tr><td>receiving_amount</td><td>decimal</td><td>Amount the beneficiary will receive after currency conversion.</td></tr><tr><td>final_Rate_Payable</td><td>decimal</td><td>Final total amount payable including applicable fees and calculations.</td></tr></tbody></table>

***

### Sample Failure Responses

**400 — Missing or Invalid Request Parameters**

```
{  
    "status": "ERROR",  
    "statusCode": 400,  
    "message": "Missing or invalid request parameters"
}
```

This response is returned when one or more required request fields are missing or contain invalid values.

***

**401 — Unauthorized or Invalid Authentication Token**

```
{  
    "status": "ERROR",  
    "statusCode": 401,  
    "message": "Unauthorized or invalid authentication token"
}
```

This response is returned when the authentication token is missing, expired, or invalid.

***

**403 — Access Restricted**

```
{  
    "status": "ERROR",  
    "statusCode": 403,  
    "message": "Access to the requested service is restricted"
}
```

This response is returned when the authenticated agent does not have permission to access the exchange rate service.

***

**404 — Exchange Rate Not Found**

```
{  
    "status": "ERROR",  
    "statusCode": 404,  
    "message": "Exchange rate not found"
}
```

This response is returned when no active exchange rate configuration exists for the selected currency corridor or agent configuration.

***

**500 — Internal Server Error**

```
{  
    "status": "ERROR",  
    "statusCode": 500,  
    "message": "Internal server error occurred while processing the request"
}
```

This response is returned when the system encounters an unexpected processing failure while fetching the exchange rate details.

***

### Important Notes

* Exchange rates may vary based on corridor configuration and market pricing.
* Service fees and margin values are dynamically calculated during the request.
* The API should be called before transaction creation to ensure accurate transaction calculations.
* Returned values may differ depending on agent-level pricing configuration.
