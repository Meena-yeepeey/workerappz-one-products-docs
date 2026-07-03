# Get Request Fields (Enum)

### Description

The Get Request Fields API is used to retrieve the dynamic field configuration required for creating and processing a transaction in the WAOne platform.

This API helps identify the complete set of fields, validations, dropdown options, and mandatory requirements that must be collected before submitting a transaction request.

The response is dynamically generated based on the selected transaction corridor and configuration. Field structures may vary depending on:

* Sending currency
* Receiving currency
* Transfer type
* Payout method
* Country configuration
* Compliance requirements

This API is primarily used to dynamically generate transaction forms and validate transaction data before creating a remittance or payout transaction.

The response contains multiple transaction sections including:

* Transaction Information
* Payment Details
* Sender Details
* Receiver Details

Each field configuration may include:

* Field identifier
* Display label
* Data type
* Validation rules
* Minimum and maximum values
* Dropdown options
* Mandatory status
* Active status

This allows applications to build flexible and configurable transaction flows without hardcoding field structures.

### Endpoint

```
GET /api/v1/getrequestfields?sendingCurrency=USD&receivingCurrency=INR
```

### Headers

<table><thead><tr><th width="349.7166748046875">Header</th><th>Value</th></tr></thead><tbody><tr><td>Authorization</td><td>Bearer <code>&#x3C;JWT_TOKEN></code></td></tr></tbody></table>

### Query Parameters

<table><thead><tr><th width="170.13336181640625">Parameter</th><th width="103.9666748046875">Type</th><th width="109.93328857421875">Required</th><th>Description</th></tr></thead><tbody><tr><td>sendingCurrency</td><td>string</td><td>Yes</td><td>Currency code of the sender transaction amount.</td></tr><tr><td>receivingCurrency</td><td>string</td><td>Yes</td><td>Currency code of the beneficiary payout amount.</td></tr></tbody></table>

### Example Request

```
GET /api/v1/getrequestfields?sendingCurrency=USD&receivingCurrency=INR
```

### Sample Success Response

```
{
  "status": "SUCCESS",
  "statusCode": 200,
  "message": "Field configuration fetched successfully",
  "data": {
    "transactionInfo": [
      {
        "field": "sending_Country",
        "label": "Sending Country",
        "type": "string",
        "mandatory": true,
        "minLength": 3,
        "maxLength": 3,
        "active": true
      },
      {
        "field": "sending_Currency",
        "label": "Sending Currency",
        "type": "string",
        "mandatory": true,
        "minLength": 3,
        "maxLength": 3,
        "active": true
      },
      {
        "field": "destination_Country",
        "label": "Receiving Country",
        "type": "string",
        "mandatory": true,
        "minLength": 3,
        "maxLength": 3,
        "active": true
      },
      {
        "field": "destination_Currency",
        "label": "Receiving Currency",
        "type": "string",
        "mandatory": true,
        "minLength": 3,
        "maxLength": 3,
        "active": true
      },
      {
        "field": "payout_Method",
        "label": "Payout Method",
        "type": "dropdown",
        "mandatory": true,
        "options": [
          {
            "label": "Bank Transfer",
            "value": "BANK_TRANSFER"
          },
          {
            "label": "Cash Transfer",
            "value": "CASH_TRANSFER"
          },
          {
            "label": "Wallet Transfer",
            "value": "WALLET_TRANSFER"
          }
        ],
        "active": true,
        "minLength": null,
        "maxLength": null
      },
      {
        "field": "transfer_Type",
        "label": "Transfer Type",
        "type": "dropdown",
        "mandatory": true,
        "options": [
          {
            "label": "Customer to Customer",
            "value": "C2C"
          },
          {
            "label": "Business to Business",
            "value": "B2B"
          },
          {
            "label": "Customer to Business",
            "value": "C2B"
          },
          {
            "label": "Business to Customer",
            "value": "B2C"
          }
        ],
        "active": true,
        "minLength": null,
        "maxLength": null
      }
    ],
    "Payment_Details": [
      {
        "field": "reference_Number",
        "label": "Reference Number",
        "type": "string",
        "mandatory": false,
        "maxLength": 50,
        "active": true,
        "minLength": null
      },
      {
        "field": "payin_Amount",
        "label": "Sending Amount",
        "type": "decimal",
        "mandatory": true,
        "minValue": 1,
        "maxValue": 1000000,
        "active": true,
        "minLength": 1,
        "maxLength": 1000000
      },
      {
        "field": "payout_Amount",
        "label": "Receiving Amount",
        "type": "decimal",
        "mandatory": true,
        "active": true,
        "minLength": null,
        "maxLength": null
      },
      {
        "field": "final_Rate_Payable",
        "label": "Final Amount Payable",
        "type": "decimal",
        "mandatory": true,
        "active": true,
        "minLength": null,
        "maxLength": null
      }
    ],
    "Sender_Details": [
      {
        "field": "first_Name",
        "label": "First Name",
        "type": "string",
        "mandatory": true,
        "minLength": 2,
        "maxLength": 50,
        "regex": "^[A-Za-z ]+$",
        "active": true
      },
      {
        "field": "last_Name",
        "label": "Last Name",
        "type": "string",
        "mandatory": true,
        "minLength": 1,
        "maxLength": 50,
        "active": true
      },
      {
        "field": "gender",
        "label": "Gender",
        "type": "dropdown",
        "mandatory": true,
        "options": [
          {
            "label": "Male",
            "value": "MALE"
          },
          {
            "label": "Female",
            "value": "FEMALE"
          }
        ],
        "active": true,
        "minLength": null,
        "maxLength": null
      },
      {
        "field": "id_Type",
        "label": "ID Type",
        "type": "dropdown",
        "mandatory": true,
        "options": [
          {
            "label": "Aadhar Card",
            "value": "AADHAR_CARD"
          },
          {
            "label": "Passport",
            "value": "PASSPORT"
          },
          {
            "label": "USA ID",
            "value": "USA_ID"
          }
        ],
        "active": true,
        "minLength": null,
        "maxLength": null
      },
      {
        "field": "id_Value",
        "label": "ID Number",
        "type": "string",
        "mandatory": true,
        "minLength": 5,
        "maxLength": 20,
        "active": true
      },
      {
        "field": "expiry_Date",
        "label": "ID Expiry Date",
        "type": "date",
        "mandatory": true,
        "active": true,
        "minLength": null,
        "maxLength": null
      },
      {
        "field": "dob",
        "label": "Date of Birth",
        "type": "date",
        "mandatory": true,
        "active": true,
        "minLength": null,
        "maxLength": null
      },
      {
        "field": "mobile_No",
        "label": "Mobile Number",
        "type": "string",
        "mandatory": true,
        "regex": "^\\+?[0-9]{8,15}$",
        "active": true,
        "minLength": null,
        "maxLength": null
      },
      {
        "field": "zip_Code",
        "label": "Zip Code",
        "type": "string",
        "mandatory": false,
        "maxLength": 10,
        "active": true,
        "minLength": null
      },
      {
        "field": "source_of_Funds",
        "label": "Source of Funds",
        "type": "dropdown",
        "mandatory": false,
        "active": true,
        "minLength": null,
        "maxLength": null,
        "options": [
          {
            "label": "Business",
            "value": "BUSINESS"
          },
          {
            "label": "Rent",
            "value": "RENT"
          },
          {
            "label": "Salary",
            "value": "SALARY"
          }
        ]
      },
      {
        "field": "customer_Relationship",
        "label": "Customer Relationship",
        "type": "string",
        "mandatory": false,
        "active": true,
        "minLength": null,
        "maxLength": null
      },
      {
        "field": "nationality",
        "label": "Nationality",
        "type": "string",
        "mandatory": true,
        "active": true,
        "minLength": null,
        "maxLength": null
      }
    ],
    "Receiver_Details": [
      {
        "field": "first_Name",
        "label": "First Name",
        "type": "string",
        "mandatory": true,
        "active": true,
        "minLength": null,
        "maxLength": null
      },
      {
        "field": "last_Name",
        "label": "Last Name",
        "type": "string",
        "mandatory": true,
        "active": true,
        "minLength": null,
        "maxLength": null
      },
      {
        "field": "address",
        "label": "Address",
        "type": "string",
        "mandatory": true,
        "active": true,
        "minLength": null,
        "maxLength": null
      },
      {
        "field": "city",
        "label": "City",
        "type": "string",
        "mandatory": false,
        "active": true,
        "minLength": null,
        "maxLength": null
      },
      {
        "field": "mobile_No",
        "label": "Mobile Number",
        "type": "string",
        "mandatory": true,
        "active": true,
        "minLength": null,
        "maxLength": null
      },
      {
        "field": "bank_Account_Number",
        "label": "Account Number",
        "type": "string",
        "mandatory": true,
        "minLength": 6,
        "maxLength": 18,
        "active": true
      },
      {
        "field": "bank_Name",
        "label": "Bank Name",
        "type": "string",
        "mandatory": true,
        "active": true,
        "minLength": null,
        "maxLength": null
      },
      {
        "field": "bank_Branch_Name",
        "label": "Branch Name",
        "type": "string",
        "mandatory": false,
        "active": true,
        "minLength": null,
        "maxLength": null
      },
      {
        "field": "bank_Code",
        "label": "IFSC Code",
        "type": "string",
        "mandatory": false,
        "regex": "^[A-Z]{4}0[A-Z0-9]{6}$",
        "active": true,
        "minLength": null,
        "maxLength": null
      },
      {
        "field": "bank_Address",
        "label": "Bank Address",
        "type": "string",
        "mandatory": false,
        "active": true,
        "minLength": null,
        "maxLength": null
      },
      {
        "field": "receive_EmailId",
        "label": "Email ID",
        "type": "string",
        "mandatory": true,
        "active": true,
        "minLength": null,
        "maxLength": null
      },
      {
        "field": "dob",
        "label": "Date of Birth",
        "type": "date",
        "mandatory": true,
        "active": true,
        "minLength": null,
        "maxLength": null
      },
      {
        "field": "source_of_Funds",
        "label": "Source of Funds",
        "type": "dropdown",
        "mandatory": true,
        "active": true,
        "minLength": null,
        "maxLength": null,
        "options": [
          {
            "label": "Business",
            "value": "BUSINESS"
          },
          {
            "label": "Rent",
            "value": "RENT"
          },
          {
            "label": "Salary",
            "value": "SALARY"
          }
        ]
      },
      {
        "field": "beneficiary_Relationship",
        "label": "Beneficiary Relationship",
        "type": "string",
        "mandatory": true,
        "active": true,
        "minLength": null,
        "maxLength": null
      }
    ],
    "createdAtGST": "19/02/2026 10:48:17 am",
    "updatedAtGST": "26/02/2026 11:44:19 am"
  }
}
```

### Success Response Description

<table><thead><tr><th width="159.70001220703125">Field</th><th width="120.88336181640625">Type</th><th>Description</th></tr></thead><tbody><tr><td>status</td><td>string</td><td>Represents the overall status of the API response.</td></tr><tr><td>statusCode</td><td>integer</td><td>Status code returned by the API request.</td></tr><tr><td>message</td><td>string</td><td>Message describing the result of the request.</td></tr><tr><td>data</td><td>object</td><td>Contains the complete dynamic field configuration required for transaction processing.</td></tr><tr><td>transactionInfo</td><td>array</td><td>Contains transaction-related field configurations such as currencies, payout methods, and transfer types.</td></tr><tr><td>Payment_Details</td><td>array</td><td>Contains payment-related field configurations such as sending amount, payout amount, and payable amount details.</td></tr><tr><td>Sender_Details</td><td>array</td><td>Contains sender information field configurations including identity, contact, and compliance-related fields.</td></tr><tr><td>Receiver_Details</td><td>array</td><td>Contains beneficiary information field configurations including payout and bank-related fields.</td></tr><tr><td>createdAtGST</td><td>string</td><td>Date and time when the field configuration was initially created in GST timezone format.</td></tr><tr><td>updatedAtGST</td><td>string</td><td>Date and time when the field configuration was last updated in GST timezone format.</td></tr></tbody></table>

### Field Configuration Structure

Each field object inside the configuration sections contains metadata required for form generation and validation.

***

### Field Object Properties

<table><thead><tr><th width="135.4166259765625">Property</th><th width="121.9166259765625">Type</th><th>Description</th></tr></thead><tbody><tr><td>field</td><td>string</td><td>Unique field identifier used in transaction requests.</td></tr><tr><td>label</td><td>string</td><td>Display name shown for the field in forms or UI screens.</td></tr><tr><td>type</td><td>string</td><td>Data type of the field such as <code>string</code>, <code>decimal</code>, <code>date</code>, or <code>dropdown</code>.</td></tr><tr><td>mandatory</td><td>boolean</td><td>Indicates whether the field is mandatory for transaction submission.</td></tr><tr><td>active</td><td>boolean</td><td>Indicates whether the field is currently enabled and available for use.</td></tr><tr><td>minLength</td><td>integer</td><td>Minimum allowed character length for string-based fields.</td></tr><tr><td>maxLength</td><td>integer</td><td>Maximum allowed character length for string-based fields.</td></tr><tr><td>minValue</td><td>decimal</td><td>Minimum allowed numeric value for decimal fields.</td></tr><tr><td>maxValue</td><td>decimal</td><td>Maximum allowed numeric value for decimal fields.</td></tr><tr><td>regex</td><td>string</td><td>Validation pattern used to validate field input values.</td></tr><tr><td>options</td><td>array</td><td>Contains selectable dropdown values for dropdown type fields.</td></tr></tbody></table>

***

### Transaction Information Configuration

The `transactionInfo` section contains the basic transaction setup fields required for initiating a transaction.

Example fields include:

* Sending Country
* Sending Currency
* Receiving Country
* Receiving Currency
* Payout Method
* Transfer Type

This section helps configure the overall transaction corridor and payout behavior.

***

### Payment Details Configuration

The `Payment_Details` section contains payment-related transaction fields.

Example fields include:

* Reference Number
* Sending Amount
* Receiving Amount
* Final Amount Payable

Validation rules, such as minimum and maximum transaction amounts, may also be included.

***

### Sender Details Configuration

The `Sender_Details` section contains sender-related information and compliance fields.

Example fields include:

* First Name
* Last Name
* Gender
* ID Type
* ID Number
* Date of Birth
* Mobile Number
* Nationality
* Source of Funds

This section helps ensure proper sender identification and regulatory compliance.

***

### Receiver Details Configuration

The `Receiver_Details` section contains beneficiary and payout-related information.

Example fields include:

* Beneficiary Name
* Address
* Mobile Number
* Bank Account Number
* Bank Name
* IFSC Code
* Email ID
* Beneficiary Relationship

These fields are required to process payouts successfully through the selected payout channel.

***

### Dropdown Field Configuration

Dropdown type fields may include selectable values inside the `options` array.

Example:

```
{  "label": "Bank Transfer",  "value": "BANK_TRANSFER"}
```

This allows applications to dynamically render selectable transaction options.

***

### Validation Rules

Some fields may contain validation patterns and limits to ensure the proper formatting of transaction dataDropdown-type.

Example validations include:

<table><thead><tr><th width="334.83331298828125">Validation Type</th><th>Example</th></tr></thead><tbody><tr><td>Name Validation</td><td><code>^[A-Za-z ]+$</code></td></tr><tr><td>Mobile Number Validation</td><td><code>^\\+?[0-9]{8,15}$</code></td></tr><tr><td>IFSC Code Validation</td><td><code>^[A-Z]{4}0[A-Z0-9]{6}$</code></td></tr><tr><td>Length Validation</td><td><code>minLength</code> and <code>maxLength</code></td></tr><tr><td>Amount Validation</td><td><code>minValue</code> and <code>maxValue</code></td></tr></tbody></table>

These validations help prevent the submission of invalid transaction data.

### Sample Failure Responses

**400 — Missing or Invalid Request Parameters**

```
{  
    "status": "ERROR",  
    "statusCode": 400,  
    "message": "Missing or invalid request parameters"
}
```

This response is returned when the required query parameters are missing or invalid in the request.

***

**401 — Unauthorized or Invalid Authentication Token**

```
{  
   "status": "ERROR",  
   "statusCode": 401,  
   "message": "Unauthorized or invalid authentication token"
}
```

This response is returned when the authentication token is missing, invalid, or expired.

***

**403 — Access Restricted**

```
{  
    "status": "ERROR",  
    "statusCode": 403,  
    "message": "Access to the requested service is restricted"
}
```

This response is returned when the authenticated agent does not have permission to access the requested service.

***

**404 — Configuration Not Found**

```
{  
    "status": "ERROR",  
    "statusCode": 404,  
    "message": "No data available for this agent/currency combination."
}
```

This response is returned when no active field configuration exists for the specified agent and currency corridor.

***

**500 — Internal Server Error**

```
{  
    "status": "ERROR",  
    "statusCode": 500,  
    "message": "Internal server error occurred while processing the request"
}
```

This response is returned when the system encounters an unexpected processing failure while retrieving the field configuration.

