# Transaction

### Description

The Transaction API is used to create and process remittance transactions within the WAOne platform.

This API is the core transaction processing endpoint used for initiating cross-border money transfers between senders and beneficiaries across supported payout corridors.

The API supports multiple transaction models, including:

* C2C (Customer to Customer)
* C2B (Customer to Business)
* B2C (Business to Customer)
* B2B (Business to Business)

The transaction request contains complete transaction information, including:

* Transaction configuration
* Payment and exchange rate details
* Sender information
* Beneficiary information
* Payout details
* Agent information
* Financial calculations

The API supports multiple payout methods, such as:

* Bank Transfer
* Wallet Transfer
* Cash Transfer

Before creating a transaction, it is recommended to:

1. Authenticate the API request
2. Fetch dynamic request fields
3. Retrieve exchange rate details
4. Validate beneficiary account information

This helps ensure accurate transaction validation and successful payout processing.

***

### Endpoint

```
POST /api/v1/TransactionManagement/Transactiondetails/Create
```

***

### Headers

| Header        | Value                |
| ------------- | -------------------- |
| Authorization | Bearer `<JWT_TOKEN>` |
| Content-Type  | application/json     |

***

### Request Body

```
{
  "Common_Details": {
    "Sending_Country": "MUS",
    "Sending_Currency": "USD",
    "Destination_Country": "MUS",
    "Destination_Currency": "INR",
    "Payout_Method": "Bank Transfer",
    "Transfer_Type": "C2C"
  },
  "Payment_Details": {
    "Reference_Number": "WATRXXXXXXXXXX",
    "Payin_Amount": 1,
    "Payout_Amount": 91.027,
    "Service_Fees": 0,
    "Exchange_Rate": 91.03,
    "Sending_Commission": 0,
    "Receiving_Commission": 0,
    "SendMargin_Value": 5,
    "Final_Rate_Payable": 1
  },
  "Sender_Details": {
    "First_Name": "XXXXYY",
    "Last_Name": "XXYXXX",
    "Gender": "Male",
    "Id_Type": "Aadhar Card",
    "Id_Value": "6272722",
    "Issue_Date": "",
    "Expiry_Date": "2026-05-28",
    "Nationality": "Andorra",
    "Zip_Code": "673014",
    "DOB": "2008-05-16",
    "Source_of_Funds": "Gaming",
    "Customer_Relationship": "Friend",
    "Purpose_of_Remittance": "Own service Transfer",
    "Address": "Address",
    "Mobile_No": "XXXXXXXXXX",
    "Sender_City": XXXXXXXXX",
    "Sender_State": "XXXXX",
    "Send_Company_Name": "",
    "Send_Company_ID": "",
    "Send_Company_Zip_Code": "XXXXXX",
    "Send_Owners_name": "",
    "Send_Owners_Id_Number": "",
    "Send_Owners_Expiry_Date": "",
    "Send_Companys_Address": "",
    "Send_Companys_Contact_Number": "",
    "Send_EmailId": "",
    "Sender_DialCode": "+213",
    "dynamicIdFields": null
  },
  "Receiver_Details": {
    "First_Name": "XXXXYYY",
    "Last_Name": "YYYZZZ",
    "Gender": "",
    "Id_Type": "Aadhar Card",
    "Id_Value": "XXXYYXXZZ",
    "Issued_Date": "",
    "Expiry_Date": "",
    "Nationality": "",
    "Zip_Code": "YYXXZZ",
    "DOB": "2008-05-16",
    "Source_of_Funds": "Salary",
    "Beneficiary_Relationship": "Friend",
    "Purpose_of_Remittance": "Home Loan",
    "Address": "XXXYYYZZZ",
    "Mobile_No": "XXXXXXXXXX",
    "Receiver_City": "XXXXXXXX",
    "Receiver_State": "YYYYYYY",
    "Bank_Account_Number": "XXXXXYYYYYY",
    "Bank_Name": "XXYYZZ",
    "Bank_Branch_Name": "XXYY",
    "Bank_Code": "ABHYYYXXXZZ",
    "Bank_Address": "",
    "Receive_Company_Name": "",
    "Receive_Company_ID": "",
    "Receive_Company_Zip_Code": "",
    "Receive_Owners_name": "",
    "Receive_Owners_Id_Number": "",
    "Receive_Owners_Expiry_Date": "",
    "Receive_Companys_Address": "",
    "Receive_Companys_Contact_Number": "",
    "Receive_EmailId": "testagent@gmail.com",
    "Receiver_DialCode": "+376",
    "Receiver_Wallet_Number": "",
    "Receiver_Wallet_Type": "",
    "Receiver_Channel": ""
  },
  "Notes": "",
  "User_Details": {
    "Agent_Name": "XXXYY ZZ",
    "Agent_Code": "WASMXXXX",
    "Sender_CreditLimitUsed": 0,
    "Receiving_Agent_Code": "WARMXXXX",
    "Receiving_Name": "XXYYZZ"
  }
}
```

### Request Structure

The transaction request contains the following sections:

<table><thead><tr><th width="211.066650390625">Section</th><th>Description</th></tr></thead><tbody><tr><td>Common_Details</td><td>Contains transaction corridor and payout configuration details.</td></tr><tr><td>Payment_Details</td><td>Contains transaction amount and exchange rate calculation details.</td></tr><tr><td>Sender_Details</td><td>Contains sender personal and compliance-related information.</td></tr><tr><td>Receiver_Details</td><td>Contains beneficiary and payout information.</td></tr><tr><td>Notes</td><td>Additional remarks or transaction notes.</td></tr><tr><td>User_Details</td><td>Contains sending and receiving agent details.</td></tr></tbody></table>

### Common\_Details

The `Common_Details` section defines the transaction corridor and payout configuration.

#### Example Fields

<table><thead><tr><th width="218.89996337890625">Field</th><th>Description</th></tr></thead><tbody><tr><td>Sending_Country</td><td>Country from which the transaction is initiated.</td></tr><tr><td>Sending_Currency</td><td>Currency used by the sender.</td></tr><tr><td>Destination_Country</td><td>Beneficiary destination country.</td></tr><tr><td>Destination_Currency</td><td>Currency received by the beneficiary.</td></tr><tr><td>Payout_Method</td><td>Selected payout method such as Bank Transfer, Wallet Transfer, or Cash Transfer.</td></tr><tr><td>Transfer_Type</td><td>Transaction type such as C2C, C2B, B2C, or B2B.</td></tr></tbody></table>

***

### Payment\_Details

The `Payment_Details` section contains transaction financial calculations and pricing details.

#### Example Fields

<table><thead><tr><th width="232.2166748046875">Field</th><th>Description</th></tr></thead><tbody><tr><td>Reference_Number</td><td>Unique transaction reference identifier.</td></tr><tr><td>Payin_Amount</td><td>Amount paid by the sender.</td></tr><tr><td>Payout_Amount</td><td>Amount received by the beneficiary.</td></tr><tr><td>Service_Fees</td><td>Service charges applied to the transaction.</td></tr><tr><td>Exchange_Rate</td><td>Exchange rate applied during currency conversion.</td></tr><tr><td>Sending_Commission</td><td>Commission charged on the sender side.</td></tr><tr><td>Receiving_Commission</td><td>Commission charged on the receiver side.</td></tr><tr><td>SendMargin_Value</td><td>Margin value applied to the exchange rate calculation.</td></tr><tr><td>Final_Rate_Payable</td><td>Final payable amount including all fees and calculations.</td></tr></tbody></table>

***

### Sender\_Details

The `Sender_Details` section contains sender personal, identification, and compliance-related information.

#### Example Fields

<table><thead><tr><th width="272.16668701171875">Field</th><th>Description</th></tr></thead><tbody><tr><td>First_Name</td><td>Sender first name.</td></tr><tr><td>Last_Name</td><td>Sender last name.</td></tr><tr><td>Gender</td><td>Sender gender information.</td></tr><tr><td>Id_Type</td><td>Type of identification document provided.</td></tr><tr><td>Id_Value</td><td>Identification document number.</td></tr><tr><td>Expiry_Date</td><td>Expiry date of the identification document.</td></tr><tr><td>Nationality</td><td>Sender nationality.</td></tr><tr><td>DOB</td><td>Sender date of birth.</td></tr><tr><td>Source_of_Funds</td><td>Declared source of transaction funds.</td></tr><tr><td>Purpose_of_Remittance</td><td>Purpose of the remittance transaction.</td></tr><tr><td>Address</td><td>Sender residential address.</td></tr><tr><td>Mobile_No</td><td>Sender contact number.</td></tr><tr><td>Sender_City</td><td>Sender city information.</td></tr><tr><td>Sender_State</td><td>Sender state or region information.</td></tr><tr><td>Send_EmailId</td><td>Sender email address.</td></tr><tr><td>Sender_DialCode</td><td>Sender country dial code.</td></tr></tbody></table>

Additional company-related fields may be required depending on the selected transfer type.

***

### Receiver\_Details

The `Receiver_Details` section contains beneficiary and payout-related information.

#### Example Fields

<table><thead><tr><th width="254.1500244140625">Field</th><th>Description</th></tr></thead><tbody><tr><td>First_Name</td><td>Beneficiary first name.</td></tr><tr><td>Last_Name</td><td>Beneficiary last name.</td></tr><tr><td>Address</td><td>Beneficiary address.</td></tr><tr><td>Mobile_No</td><td>Beneficiary contact number.</td></tr><tr><td>Receiver_City</td><td>Beneficiary city information.</td></tr><tr><td>Receiver_State</td><td>Beneficiary state or region information.</td></tr><tr><td>Bank_Account_Number</td><td>Beneficiary bank account number.</td></tr><tr><td>Bank_Name</td><td>Beneficiary bank name.</td></tr><tr><td>Bank_Branch_Name</td><td>Beneficiary bank branch name.</td></tr><tr><td>Bank_Code</td><td>IFSC or routing code used for payout processing.</td></tr><tr><td>Bank_Address</td><td>Beneficiary bank address.</td></tr><tr><td>Receive_EmailId</td><td>Beneficiary email address.</td></tr><tr><td>Receiver_DialCode</td><td>Beneficiary country dial code.</td></tr><tr><td>Receiver_Wallet_Number</td><td>Wallet number used for wallet-based payouts.</td></tr><tr><td>Receiver_Wallet_Type</td><td>Wallet provider or wallet type information.</td></tr><tr><td>Receiver_Channel</td><td>Payout channel information.</td></tr><tr><td>Beneficiary_Relationship</td><td>Relationship between sender and beneficiary.</td></tr></tbody></table>

This section supports both bank payouts and wallet-based transactions.

***

### User\_Details

The `User_Details` section contains sending and receiving agent information.

#### Example Fields

<table><thead><tr><th width="265.11663818359375">Field</th><th>Description</th></tr></thead><tbody><tr><td>Agent_Name</td><td>Name of the sending agent initiating the transaction.</td></tr><tr><td>Agent_Code</td><td>Unique identifier of the sending agent.</td></tr><tr><td>Sender_CreditLimitUsed</td><td>Credit limit utilized during transaction processing.</td></tr><tr><td>Receiving_Agent_Code</td><td>Unique identifier of the receiving payout agent.</td></tr><tr><td>Receiving_Name</td><td>Name of the receiving payout partner or agent.</td></tr></tbody></table>

### Transaction Validation Process

During transaction creation, the system performs:

* Dynamic field validation
* Exchange rate validation
* Financial calculation validation
* Beneficiary validation
* Agent validation
* Compliance verification
* Payout configuration validation

The transaction is processed only after all validations are completed successfully.

### Sample Success Response

```
{
  "addTransactionResponse": {
    "results": {
      "resCode": 200,
      "resData": [
        {
          "rpTxnNo": "WATRXXXXXXXXXX",
          "status": "Initiated",
          "message": "Status moved to Initiated",
          "data": {
            "transaction_No": "WATR6XXXXXXXXXX",
            "agent_Name": "XXXYYY ZZ",
            "old_Status_Name": " ",
            "new_Status_Name": "Initiated",
            "auto_Approval": true,
            "message": "Status moved to Initiated"
          }
        }
      ],
      "resMessage": "Insert Success!"
    }
  },
  "calculateInternalRatesResponse": {
    "status": "Success",
    "statusCode": 200,
    "message": "Calculate Value Successfully Updated"
  },
  "localSave": {
    "success": true,
    "transactionId": "xaxxxxecyfyyyeaxxfzcdcec"
  },
  "debitInfo": {
    "success": true,
    "agent": {
      "_id": "xaxxaydyyyycxfbzffzzzeda",
      "externalAgentId": "WASMXXXX",
      "referAgentID": "WASMXXXX",
      "agentName": "XXXYY ZZ",
      "displayName": "XXXYY ZZ",
      "agentType": 1,
      "agentAddress": "address",
      "dialCode": "+355",
      "contactNumber": "xxxxxxyyy",
      "email": "testagent@gmail.com",
      "prefundingRequired": true,
      "contactPerson": "",
      "alternativeEmails": [],
      "agentCreditLimitExpiry": "2",
      "agentCreditLimit": 100,
      "prefundingLimit": 199,
      "balance": 86.26,
      "lastVoucherBalance": 0,
      "isEmailSent": true,
      "lastLowBalanceEmailDay": null,
      "generatedAccounts": [
        {
          "sendingPrincipalAccount": "XXYY ZZ PRINCIPAL & COMMISSION A/C USD",
          "receivingAccount": "",
          "sendingExCommissionAccount": "",
          "sendingVatPayableAccount": ""
        },
        {
          "sendingPrincipalAccount": "XXXYYY ZZZ PRINCIPAL & COMMISSION A/C INR",
          "receivingAccount": "",
          "sendingExCommissionAccount": "",
          "sendingVatPayableAccount": ""
        }
      ],
      "isRemoteAPICall": true,
      "partnerId": null,
      "createdBy": "xxxxxxdyycydfzzzcyyyyyce",
      "updatedBy": "system",
      "countryManagement": [
        {
          "countryName": "India",
          "countryShortname": "IND",
          "countryLimit": 100000,
          "currencies": [
            {
              "currencyShortname": "USD",
              "currencyLimit": 1000,
              "currencyType": 2,
              "creditsBalance": 0,
              "nriReceiverAgent": "",
              "nonNriReceiverAgent": "",
              "_id": "xxxxxxdyycydfzzzcyyyyyce"
            },
            {
              "currencyShortname": "INR",
              "currencyLimit": 1000,
              "currencyType": 2,
              "creditsBalance": 0,
              "nriReceiverAgent": "",
              "nonNriReceiverAgent": "",
              "_id": "xxxxxxdyycydfzzzcyyyyyce"
            },
            {
              "currencyShortname": "AED",
              "currencyLimit": 10000,
              "currencyType": 2,
              "creditsBalance": 0,
              "nriReceiverAgent": "",
              "nonNriReceiverAgent": "",
              "_id": "xxxxxxdyycydfzzzcyyyyyce"
            },
            {
              "currencyShortname": "CNY",
              "currencyLimit": 100,
              "currencyType": 2,
              "creditsBalance": 0,
              "nriReceiverAgent": null,
              "nonNriReceiverAgent": null,
              "_id": "xxxxxxdyycydfzzzcyyyyyce"
            },
            {
              "currencyShortname": "HKD",
              "currencyLimit": 199,
              "currencyType": 2,
              "creditsBalance": 0,
              "nriReceiverAgent": null,
              "nonNriReceiverAgent": null,
              "_id": "6a10af71466c0fb5ff0026e3"
            },
            {
              "currencyShortname": "CAD",
              "currencyLimit": 299,
              "currencyType": 2,
              "creditsBalance": 0,
              "nriReceiverAgent": null,
              "nonNriReceiverAgent": null,
              "_id": "xxxxxxdyycydfzzzcyyyyyce"
            }
          ],
          "cityLocation": [
            {
              "city": "xxxx",
              "locations": [
                "xxxyyyx"
              ],
              "_id": "xxxxxxdyycydfzzzcyyyyyce"
            },
            {
              "city": "xxxyyy",
              "locations": [
                "xxxyyy"
              ],
              "_id": "xxxxxxdyycydfzzzcyyyyyce"
            }
          ],
          "purposeOfTransfer": [
            "Family Support",
            "Investment purpose",
            "Own Account Transfer",
            "Own service Transfer",
            "Salary Transfer"
          ],
          "idTypes": [
            {
              "bsId": "xxxxxxdyycydfzzzcyyyyyce",
              "idType": "Aadhar Card",
              "lastSyncedIdTypeName": "Aadhar Card",
              "fields": [
                "Aadhar Number",
                "Aadhar Expiry Date"
              ]
            },
            {
              "bsId": "xxxxxxdyycydfzzzcyyyyyce",
              "idType": "Citizenship ID",
              "lastSyncedIdTypeName": "Citizenship ID",
              "fields": [
                "ID Number",
                "Expiry Date"
              ]
            },
            {
              "bsId": "xxxxxxdyycydfzzzcyyyyyce",
              "idType": "NID card",
              "lastSyncedIdTypeName": "NID card",
              "fields": [
                "Id Number",
                "Expiry Date"
              ]
            },
            {
              "bsId": "xxxxxxdyycydfzzzcyyyyyce",
              "idType": "PAN Card",
              "lastSyncedIdTypeName": "PAN Card",
              "fields": [
                "ID Number",
                "Expiry Date",
                "hhjhj",
                "jjjj"
              ]
            },
            {
              "bsId": "xxxxxxdyycydfzzzcyyyyyce",
              "idType": "Passport",
              "lastSyncedIdTypeName": "Passport",
              "fields": [
                "Passport Number",
                "Expiry Date"
              ]
            }
          ],
          "deletedIdTypeBsIds": [],
          "sourceOfFund": [
            "Business",
            "Gaming",
            "Rent",
            "Resot Transfer",
            "Salary"
          ],
          "paymentModes": [
            {
              "Paymode": "Bank Transfer",
              "PaymentLimit": 100,
              "_id": "xxxxxxdyycydfzzzcyyyyyce"
            },
            {
              "Paymode": "Cash Transfer",
              "PaymentLimit": 100,
              "_id": "xxxxxxdyycydfzzzcyyyyyce"
            },
            {
              "Paymode": "Wallet Transfer",
              "PaymentLimit": 100,
              "_id": "xxxxxxdyycydfzzzcyyyyyce"
            }
          ],
          "receiverAgents": [
            {
              "name": "",
              "status": "",
              "condition": "",
              "_id": "xxxxxxdyycydfzzzcyyyyyce"
            }
          ],
          "limitManagement": {
            "creditLimit": 0,
            "creditBalance": 0,
            "_id": "xxxxxxdyycydfzzzcyyyyyce"
          },
          "_id": "xxxxxxdyycydfzzzcyyyyyce",
          "status": true
        }
      ],
      "isDeleted": false,
      "status": true,
      "alternativeEmail": "",
      "creditLimitUsed": 0,
      "creditLimitValidityDays": 7,
      "creditLimitExpiryDate": "2026-05-24T22:48:48.000Z",
      "creditLimitFirstUsedDate": null,
      "isBlocked": false,
      "prefundingLimitExpiry": null,
      "apiRequired": true,
      "apiCredentials": true,
      "clientId": "XXXXXXAXDCBAYDDYYYFY",
      "secretKey": "XXXXXYYYYYYXXXXXZZZZZZZ",
      "autoApproval": true,
      "currentApiToken": null,
      "approvalStatus": "Approved",
      "createdAt": "2026-05-22T18:43:34.786Z",
      "updatedAt": "2026-05-23T07:31:56.393Z",
      "internalAgentId": "INTXXXXXXXX",
      "__v": 2,
      "agentId": "WASMXXXX"
    },
    "syncedData": {
      "balance": 86.26,
      "isBlocked": false,
      "creditLimitUsed": 0,
      "creditLimitExpiryDate": "2026-05-24 22:48:48",
      "isExpired": false
    }
  },
  "receiverDebitInfo": {
    "success": true,
    "debitedAmount": 1.5,
    "receiverCode": "WARMXXXX",
    "newBalance": 88.72
  }
}
```

***

### Success Response Description

<table><thead><tr><th width="266.23333740234375">Field</th><th width="113.88336181640625">Type</th><th>Description</th></tr></thead><tbody><tr><td>addTransactionResponse</td><td>object</td><td>Contains the primary transaction creation response returned after successful transaction processing.</td></tr><tr><td>results</td><td>object</td><td>Contains transaction processing result information.</td></tr><tr><td>resCode</td><td>integer</td><td>Response code returned after transaction creation.</td></tr><tr><td>resData</td><td>array</td><td>Contains the transaction reference and status information.</td></tr><tr><td>rpTxnNo</td><td>string</td><td>Unique transaction number generated for the remittance transaction.</td></tr><tr><td>status</td><td>string</td><td>Current transaction processing status.</td></tr><tr><td>message</td><td>string</td><td>Transaction status message returned during processing.</td></tr><tr><td>transaction_No</td><td>string</td><td>Internal transaction reference number.</td></tr><tr><td>agent_Name</td><td>string</td><td>Name of the sending agent that initiated the transaction.</td></tr><tr><td>old_Status_Name</td><td>string</td><td>Previous transaction status before status update.</td></tr><tr><td>new_Status_Name</td><td>string</td><td>Updated transaction status after processing.</td></tr><tr><td>auto_Approval</td><td>boolean</td><td>Indicates whether the transaction was automatically approved by the system.</td></tr><tr><td>resMessage</td><td>string</td><td>Final response message returned after transaction insertion.</td></tr><tr><td>calculateInternalRatesResponse</td><td>object</td><td>Contains exchange rate and financial calculation update status information.</td></tr><tr><td>statusCode</td><td>integer</td><td>Status code returned for internal rate calculation processing.</td></tr><tr><td>localSave</td><td>object</td><td>Contains local database transaction save information.</td></tr><tr><td>transactionId</td><td>string</td><td>Internal database transaction identifier generated after successful transaction storage.</td></tr><tr><td>debitInfo</td><td>object</td><td>Contains sending agent balance synchronization and debit information.</td></tr><tr><td>syncedData</td><td>object</td><td>Contains updated sending agent balance and credit information after transaction processing.</td></tr><tr><td>balance</td><td>decimal</td><td>Updated sending agent balance after transaction debit processing.</td></tr><tr><td>isBlocked</td><td>boolean</td><td>Indicates whether the sending agent is blocked.</td></tr><tr><td>creditLimitUsed</td><td>decimal</td><td>Credit amount utilized by the sending agent.</td></tr><tr><td>isExpired</td><td>boolean</td><td>Indicates whether the credit limit has expired.</td></tr><tr><td>receiverDebitInfo</td><td>object</td><td>Contains receiving agent debit and balance update details.</td></tr><tr><td>debitedAmount</td><td>decimal</td><td>Amount debited from the receiving agent account.</td></tr><tr><td>receiverCode</td><td>string</td><td>Receiving payout agent identifier.</td></tr><tr><td>newBalance</td><td>decimal</td><td>Updated receiving agent balance after debit processing.</td></tr></tbody></table>

### Additional Processing Information

The transaction creation process may also perform:

* Internal exchange rate calculation
* Agent balance synchronization
* Credit limit validation
* Auto approval validation
* Receiving agent debit processing
* Transaction status updates
* Local transaction storage

These processing details are returned in the response for transaction tracking and operational monitoring purposes.

### Sample Failure Responses

**400 — Missing or Invalid Transaction Request Fields**

```
{  
    "success": false,  
    "message": "Mandatory fields missing as per configuration",  
    "missingFields": [    
    {      
        "section": "Transaction Info",      
        "field": "sending_Country",      
        "label": "Sending Country"    
   }]
}
```

This response is returned when one or more mandatory transaction fields are missing based on the configured transaction corridor and validation rules.

***

**401 — Unauthorized or Invalid Authentication Token**

```
{  
    "success": false,  
    "message": "Unauthorized or invalid authentication token"
}
```

This response is returned when the authentication token is missing, invalid, or expired.

***

**403 — Access Restricted**

```
{  
    "success": false,  
    "message": "Access to the transaction service is restricted"
}
```

This response is returned when the authenticated agent does not have permission to access the transaction processing service.

***

**404 — Exchange Rate or Payout Configuration Not Found**

<pre><code>  {  
      "success": false,  
      "message": "Failed to calculate financial fields: No active rate found for USD-INR and agent WASM1636"
<strong>  }
</strong></code></pre>

This response is returned when no active exchange rate or payout configuration exists for the selected currency corridor and agent configuration.

***

**500 — Internal Server Error**

```
{  
    "success": false,  
    "message": "Internal server error occurred while processing the transaction"
}
```

This response is returned when the system encounters an unexpected processing failure during transaction creation.

***

### Important Notes

* Transaction fields may vary depending on the payout method and transfer type.
* Dynamic field validation is based on the Get Request Fields API configuration.
* Exchange rate calculation should be completed before transaction creation.
* Beneficiary verification is recommended before processing payouts.
* Wallet-related fields are required only for wallet-based transactions.
* Additional company-related fields may be required for B2B and B2C transaction types.
* Transaction creation may update agent balances and credit limits during processing.
