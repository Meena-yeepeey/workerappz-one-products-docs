# Get Transaction

### Description

The Get Transaction API is used to retrieve transaction records from the WAOne platform based on different search criteria.

This API allows users to search and track previously created remittance transactions using transaction details, sender information, receiver information, account details, company details, or date filters.

The API supports:

* Transaction history retrieval
* Transaction tracking
* Sender-based transaction search
* Beneficiary-based transaction search
* Date-based transaction filtering
* Latest transaction retrieval

This API is commonly used for:

* transaction monitoring,
* payout tracking,
* compliance review,
* reconciliation,
* customer support,
* and transaction status verification.

The response includes complete transaction information such as:

* transaction details,
* sender and receiver information,
* payout information,
* financial calculations,
* agent details,
* and transaction status.

***

### Endpoint

```
POST /api/v1/gettransaction
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
  "searchValue": "",
  "startDate": null,
  "endDate": null,
  "topRecord": 1
}
```

***

### Request Field Description

<table><thead><tr><th width="141.566650390625">Field</th><th width="140.76666259765625">Type</th><th width="119.98333740234375">Required</th><th>Description</th></tr></thead><tbody><tr><td>searchValue</td><td>string</td><td>No</td><td>Search value used to find matching transaction records.</td></tr><tr><td>startDate</td><td>date/null</td><td>No</td><td>Start date used for transaction date range filtering.</td></tr><tr><td>endDate</td><td>date/null</td><td>No</td><td>End date used for transaction date range filtering.</td></tr><tr><td>topRecord</td><td>integer</td><td>No</td><td>Number of latest transaction records to retrieve.</td></tr></tbody></table>

### Supported Search Parameters

The API supports searching transactions using multiple criteria, including:

* Transaction Number
* Sender Mobile Number
* Sender ID Number
* Sender Zip Code
* Receiver ID Number
* Beneficiary Account Number
* Receiver Mobile Number
* Sending Company Name
* Receiving Company Name

At least one valid search parameter or `topRecord` value must be provided.

### Search Behavior

The API supports different transaction retrieval scenarios.

#### 1. Latest Transactions Retrieval

If `topRecord` is provided, the API returns the latest transaction records.

Example:

* `topRecord = 10`

This returns the most recent 10 transaction records.

***

#### 2. Search Using Transaction or Customer Details

The `searchValue` field can be used to retrieve transactions using:

* transaction number,
* sender details,
* beneficiary details,
* account number,
* or company details.

***

#### 3. Date-Based Transaction Search

The API supports transaction filtering using:

* `startDate`
* `endDate`

This helps retrieve transactions created within a specific date range.

### Sample Success Response

```
{
  "resCode": 0,
  "resData": [
    {
      "id": XXXX,
      "transaction_Number": "WATRXXXXXXXXXX",
      "reference_Number": "WATRXXXXXXXXXX",
      "sending_Country": "IND",
      "sending_Currency": "USD",
      "destination_Country": "IND",
      "destination_Currency": "CAD",
      "payout_Method": "Bank Transfer",
      "transfer_Type": "C2C",
      "sender_First_Name": "XXXX ",
      "sender_Last_Name": "YYYY",
      "sender_DialCode": "+91",
      "sender_Mobile_No": "XXXXXXXXXX",
      "sender_Gender": "Male",
      "sender_Dob": "09-06-1997",
      "sender_Id_Type": "Passport",
      "sender_Id_Value": "XXXXXXXXX",
      "sender_Issued_Date": "01-01-0001",
      "sender_Expiry_Date": "01-01-0001",
      "sender_Nationality": "United Arab Emirates",
      "sender_Zip_Code": "XXXXXXX",
      "sender_Source_Of_Funds": "Business",
      "sender_Beneficiary_Relationship": "Friend",
      "sender_Purpose_Of_Remittance": "Balance Transfer",
      "sender_Address": "test",
      "sender_Dynamic_IdFields": "{}",
      "sender_City": "tes",
      "sender_State": "Kerala",
      "receiver_First_Name": "XXXXX",
      "receiver_Last_Name": "YYYYY",
      "receiver_DialCode": "+91",
      "receiver_Mobile_No": "XXXXXXXXXX",
      "receiver_Gender": "",
      "receiver_Dob": "23-01-1999",
      "receiver_Id_Type": "",
      "receiver_Id_Value": "",
      "receiver_Issued_Date": "01-01-0001",
      "receiver_Expiry_Date": "01-01-0001",
      "receiver_Nationality": "United Arab Emirates",
      "receiver_Zip_Code": "000000",
      "receiver_Source_Of_Funds": "Salary",
      "receiver_Beneficiary_Relationship": "Family",
      "receiver_Purpose_Of_Remittance": "Home Loan",
      "receiver_Address": "XXXYYYZZZ",
      "receiver_Bank_Name": "XXXXYYY ZZZZ",
      "receiver_Bank_Account_Number": "XXXXXXXXXXX",
      "receiver_Bank_Branch_Name": "Toronto",
      "receiver_Bank_Code": "XXXXYYYYXX",
      "receiver_Bank_Address": "",
      "receiver_Wallet_Number": "",
      "receiver_Wallet_Type": "",
      "receiver_Channel": "",
      "receiver_City": "dubai",
      "receiver_State": "Dubai",
      "payin_Amount": "3.000000",
      "payout_Amount": "3.145149",
      "service_Fees": "0.007037",
      "exchange_Rate": "1.048383",
      "sending_Commission": "0.007037",
      "receiving_Commission": "0.003000",
      "sendMargin_Value": "0.334567",
      "final_Rate_Payable": "3.007037",
      "agent_Name": "XXXX YYY",
      "agent_Code": "WASMXXXX",
      "referAgentId": "WASMXXXX",
      "receiving_Name": "XXXYY ZZZ",
      "receiving_Agent_Code": "WARMXXXX",
      "created_At": "05/25/2026 17:04:52",
      "send_Company_Name": "",
      "send_Company_ID": "",
      "send_Company_Zip_Code": "XXXXXXX",
      "send_Owners_Name": "",
      "send_Owners_ID_Number": "",
      "send_Owners_Expiry_Date": null,
      "send_Companys_Address": "",
      "send_Companys_Contact_Number": "",
      "send_EmailId": "",
      "receive_Company_Name": "",
      "receive_Company_ID": "",
      "receive_Company_Zip_Code": "",
      "receive_Owners_Name": "",
      "receive_Owners_ID_Number": "",
      "receive_Owners_Expiry_Date": null,
      "receive_Companys_Address": "",
      "receive_Companys_Contact_Number": "",
      "receive_EmailId": "test@agent.com",
      "third_Party_Code": "xxxyyyxxxyyzzzz",
      "trstatusid": "4",
      "tr_Status_Name": "In Progress",
      "senderAgentDisplayName": "XXXYYY ZZZ",
      "receiverAgentDisplayName": "USD CAD",
      "autoapproval": true,
      "updated_At": null,
      "updated_by": null
    }
  ],
  "resMessage": null
}
```

***

### Success Response Description

<table><thead><tr><th width="278.75">Field</th><th width="118.9666748046875">Type</th><th>Description</th></tr></thead><tbody><tr><td>resCode</td><td>integer</td><td>API response code returned for the request.</td></tr><tr><td>resData</td><td>array</td><td>Contains the list of transaction records matching the search criteria.</td></tr><tr><td>transaction_Number</td><td>string</td><td>Unique transaction identifier generated by the system.</td></tr><tr><td>reference_Number</td><td>string</td><td>Reference number associated with the transaction.</td></tr><tr><td>sending_Country</td><td>string</td><td>Country from which the transaction was initiated.</td></tr><tr><td>sending_Currency</td><td>string</td><td>Currency used by the sender.</td></tr><tr><td>destination_Country</td><td>string</td><td>Beneficiary payout destination country.</td></tr><tr><td>destination_Currency</td><td>string</td><td>Currency received by the beneficiary.</td></tr><tr><td>payout_Method</td><td>string</td><td>Selected payout method such as Bank Transfer or Wallet Transfer.</td></tr><tr><td>transfer_Type</td><td>string</td><td>Transaction type such as C2C, B2B, C2B, or B2C.</td></tr><tr><td>sender_First_Name</td><td>string</td><td>Sender first name.</td></tr><tr><td>sender_Last_Name</td><td>string</td><td>Sender last name.</td></tr><tr><td>receiver_First_Name</td><td>string</td><td>Beneficiary first name.</td></tr><tr><td>receiver_Last_Name</td><td>string</td><td>Beneficiary last name.</td></tr><tr><td>receiver_Bank_Name</td><td>string</td><td>Beneficiary bank name.</td></tr><tr><td>receiver_Bank_Account_Number</td><td>string</td><td>Beneficiary bank account number.</td></tr><tr><td>payin_Amount</td><td>decimal</td><td>Amount paid by the sender.</td></tr><tr><td>payout_Amount</td><td>decimal</td><td>Amount received by the beneficiary.</td></tr><tr><td>exchange_Rate</td><td>decimal</td><td>Exchange rate applied for the transaction.</td></tr><tr><td>final_Rate_Payable</td><td>decimal</td><td>Final payable amount including fees and charges.</td></tr><tr><td>tr_Status_Name</td><td>string</td><td>Current transaction processing status.</td></tr><tr><td>created_At</td><td>datetime</td><td>Transaction creation date and time.</td></tr></tbody></table>

### Transaction Status Values

<table><thead><tr><th width="230.6500244140625">Status</th><th>Description</th></tr></thead><tbody><tr><td>In Progress</td><td>Transaction is currently being processed</td></tr><tr><td>Completed</td><td>Transaction completed successfully</td></tr><tr><td>Pending</td><td>Transaction is awaiting processing</td></tr><tr><td>Rejected</td><td>Transaction was rejected</td></tr><tr><td>Agency Blocked</td><td>Transaction blocked during agent or compliance validation</td></tr></tbody></table>

### Sample Failure Responses

**400 — Missing or Invalid Search Parameters**

```
{
  "success": false,
  "message": "At least one search parameter is required. Please provide one of: transactionnumber, senderMobileno, sender_IDnumber, post_Zip_Code, receiver_IDnumber, accountnumber, receiverMobileno, sendCompanyName, receiveCompanyName or topRecord"
}
```

This response is returned when no valid search parameter or `topRecord` value is provided in the request.

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
  "message": "Access to transaction records is restricted"
}
```

This response is returned when the authenticated agent does not have permission to access transaction records.

***

**404 — No Transaction Records Found**

```
{
  "success": false,
  "message": "No transaction records found"
}
```

This response is returned when no transaction records match the provided search criteria.

***

**500 — Internal Server Error**

```
{
  "success": false,
  "message": "Internal server error occurred while processing the request"
}
```

This response is returned when the system encounters an unexpected processing failure while retrieving transaction details.

### Important Notes

* At least one valid search parameter is required.
* Large transaction datasets should be filtered using date ranges or top record limits.
* Transaction status values may change during processing.
* Some transaction fields may vary depending on payout method and transfer type.
* Wallet transactions may contain wallet-specific payout fields.
* Business transactions may contain additional company-related fields.
* Returned transaction data depends on user access permissions and agent-level visibility.
