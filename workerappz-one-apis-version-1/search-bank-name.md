# Search Bank Name

### Description

The Search Bank Name API is used to retrieve the list of available payout banks, wallet providers, or cash payout locations for a specific receiving country and payout type.

This API helps users search and validate beneficiary payout institutions before creating a transaction.

The API supports:

* Bank payout search
* Wallet payout search
* Cash payout search

Search results can be filtered using:

* Receiving country
* Search keyword
* Payout type
* Pagination

This API is commonly used during beneficiary creation and transaction processing to allow users to select the correct payout institution and bank details.

The API supports both:

* full list retrieval,
* and keyword-based search.

If `searchText` is empty, the API returns the available payout list based on the provided `pageSize`.

If `searchText` is provided, the API filters and returns matching records based on the entered keyword.

***

### Endpoint

```
POST /api/v1/banklist/receivingcurrency=INR
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
  "receivingCountryCode": "IND",
  "page": 1,
  "searchText": "kotak",
  "PayoutType": "B",
  "pageSize": 3
}
```

***

### Request Field Description

<table><thead><tr><th width="197.183349609375">Field</th><th width="110.1500244140625">Type</th><th width="108.76666259765625">Required</th><th>Description</th></tr></thead><tbody><tr><td>receivingCountryCode</td><td>string</td><td>Yes</td><td>ISO country code of the receiving country where the payout will be processed.</td></tr><tr><td>page</td><td>integer</td><td>Yes</td><td>Page number used for paginated search results.</td></tr><tr><td>searchText</td><td>string</td><td>No</td><td>Search keyword used to filter payout institutions or bank names.</td></tr><tr><td>PayoutType</td><td>string</td><td>Yes</td><td>Type of payout method to search. Supported values are <code>B</code> (Bank), <code>W</code> (Wallet), and <code>C</code> (Cash).</td></tr><tr><td>pageSize</td><td>integer</td><td>Yes</td><td>Number of records to be returned per page.</td></tr></tbody></table>

### Search Behavior

The API supports two common search scenarios:

#### 1. List Retrieval Without Search

If `searchText` is empty, the API returns the payout institution list based on the specified `pageSize`.

Example:

* `pageSize = 10`
* `searchText = ""`

This returns the first 10 available records.

***

#### 2. Keyword-Based Search

If `searchText` is provided, the API filters and returns records matching the entered search keyword.

Example:

* `searchText = "kotak"`
* `pageSize = 3`

This returns payout institutions matching the keyword “kotak”.

### Sample Success Response

```
{
  "totalCount": 1649,
  "data": [
    {
      "bankName": "ALLAHABAD BANK",
      "bankAddress": null,
      "branchName": "KOTAKPURA",
      "bankCode": "ALLA0212361",
      "legacySetBankCode": ""
    },
    {
      "bankName": "ANDHRA PRAGATHI GRAMEENA BANK",
      "bankAddress": null,
      "branchName": "P.KOTAKONDA",
      "bankCode": "APGB0003171",
      "legacySetBankCode": ""
    },
    {
      "bankName": "KOTAK MAHINDRA BANK",
      "bankAddress": null,
      "branchName": "CHAURA RASTA BRANCH",
      "bankCode": "KKBK0003549",
      "legacySetBankCode": ""
    }
  ],
  "page": 1,
  "pageSize": 3
}
```

***

## Success Response Description

<table><thead><tr><th width="184.76666259765625">Field</th><th width="129.95001220703125">Type</th><th>Description</th></tr></thead><tbody><tr><td>totalCount</td><td>integer</td><td>Total number of available records matching the search criteria.</td></tr><tr><td>data</td><td>array</td><td>Contains the list of payout institutions or banks returned by the search request.</td></tr><tr><td>bankName</td><td>string</td><td>Name of the payout bank or financial institution.</td></tr><tr><td>bankAddress</td><td>string/null</td><td>Address of the bank or payout institution, if available.</td></tr><tr><td>branchName</td><td>string</td><td>Name of the bank branch or payout location.</td></tr><tr><td>bankCode</td><td>string</td><td>Bank routing code, IFSC code, or institution identifier.</td></tr><tr><td>legacySetBankCode</td><td>string</td><td>Legacy bank code used for internal or backward compatibility purposes, if applicable.</td></tr><tr><td>page</td><td>integer</td><td>Current page number returned in the response.</td></tr><tr><td>pageSize</td><td>integer</td><td>Number of records returned per page.</td></tr></tbody></table>

### Sample Failure Responses

**400 — Missing or Invalid Request Parameters**

```
 {
  "success": false,
  "message": "Remote API returned an error",
  "details": {
    "resCode": 400,
    "resData": null,
    "resMessage": "PayoutType is required. Valid values: B (Bank), W (Wallet), C (Cash)."
  }
}
```

This response is returned when required request parameters are missing or invalid.

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
  "message": "Access to the requested service is restricted"
}
```

This response is returned when the authenticated agent does not have permission to access the payout institution search service.

***

**404 — No Records Found**

```
{
  "success": false,
  "message": "No payout institution records found"
}
```

This response is returned when no payout institution records match the provided search criteria.

***

**500 — Internal Server Error**

```
{
  "success": false,
  "message": "Internal server error occurred while processing the request"
}
```

This response is returned when the system encounters an unexpected processing failure while retrieving payout institution details.



***

### Important Notes

* The API supports pagination for large result sets.
* The `searchText` field is optional.
* Search results may vary depending on payout corridor configuration.
* Bank availability depends on the selected country and payout type.
* The `bankCode` value should be used during beneficiary and transaction creation.
* Wallet and cash payout searches may return different payout provider structures depending on the corridor configuration.
