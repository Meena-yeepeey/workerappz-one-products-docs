# Authenticate

### Description

The Authentication API is used to validate and authorize an agent before accessing any protected WAOne API services.

This API verifies the credentials provided for the registered agent and returns a JWT access token upon successful authentication. The generated token must be included in the `Authorization` header for all subsequent API requests.

The authentication process ensures that only authorized agents and partner systems can securely access transaction, payout, and remittance services provided by the WAOne platform.

This API is the first step in the WAOne integration flow and must be completed before calling other APIs such as exchange rate, bank search, transaction creation, or transaction retrieval.

***

### Endpoint

```
POST /api/agent/v1/authenticate
```

***

### Request Body

```
{
 "clientId": "XXXXXXXXXXXXX",
    "secretKey": "XXXXXXYYYYXXXXXZZZZZZZZ",
    "agentId": "WASMXXXX",
    "agentName": "XXXYYY ZZZ"
}
```

***

### Request Field Description

<table><thead><tr><th width="117.2833251953125">Field</th><th width="103.7333984375">Type</th><th width="117.23333740234375">Required</th><th>Description</th></tr></thead><tbody><tr><td>clientId</td><td>string</td><td>Yes</td><td>Unique client identifier assigned during onboarding. This value is used to identify the organization or integration partner accessing the WAOne platform.</td></tr><tr><td>secretKey</td><td>string</td><td>Yes</td><td>Secure authentication key associated with the clientId. This key is used to verify the authenticity of the API request and must be kept confidential.</td></tr><tr><td>agentId</td><td>string</td><td>Yes</td><td>Unique identifier of the registered agent or partner entity initiating the API request. This value is used to identify the specific operational account within the WAOne platform.</td></tr><tr><td>agentName</td><td>string</td><td>Yes</td><td>Registered name of the agent or organization associated with the provided agentId. This is used for validation and identification purposes during authentication.</td></tr></tbody></table>

***

## Authentication Process

During authentication:

1. The system validates the provided `clientId` and `secretKey`.
2. The platform verifies whether the `agentId` and `agentName` are mapped to the authorized client.
3. If the credentials are valid, the API generates a JWT access token.
4. The token is then returned in the response and must be used in the authorization header for all secured APIs.

### Sample Success Response

```
{
  "resCode": 200,
  "resMessage": "Authentication successful",
  "resData": {
    "token": "JWT_ACCESS_TOKEN",
    "agentName": "XXXYYY ZZZ",
    "agentId": "WASMXXXX",
    "agentType": "SenderManagement"
  }
}
```

***

### Response Field Description

<table><thead><tr><th width="133.8499755859375">Field</th><th width="128.5333251953125">Type</th><th>Description</th></tr></thead><tbody><tr><td>resCode</td><td>integer</td><td>Status code returned by the API indicating the result of the authentication request.</td></tr><tr><td>resMessage</td><td>string</td><td>Message describing the authentication result.</td></tr><tr><td>token</td><td>string</td><td>JWT access token generated after successful authentication. This token must be included in the <code>Authorization</code> header for all protected API requests.</td></tr><tr><td>agentName</td><td>string</td><td>Name of the authenticated agent associated with the access token.</td></tr><tr><td>agentId</td><td>string</td><td>Unique identifier of the authenticated agent.</td></tr><tr><td>agentType</td><td>string</td><td>Represents the operational role or category assigned to the authenticated agent within the WAOne platform.</td></tr></tbody></table>

### Using the Access Token

After successful authentication, the returned JWT token must be included in the request header when calling secured APIs.

Example:

```
Authorization: Bearer JWT_ACCESS_TOKEN
```

### Sample Failure Responses

**400 — Missing Required Parameters**

```
{
    "resCode": 400,
    "resMessage": "clientId, secretKey, agentId and agentName are required"
}
```

This response is returned when one or more mandatory request fields are missing from the authentication request.

**401 — Invalid Authentication Credentials**

```
{  
   "resCode": 401,  
   "resMessage": "Invalid authentication credentials"
}
```

This response is returned when the provided authentication credentials are invalid or do not match the registered agent configuration.

**403 — API Access Restricted**

```
{  
    "resCode": 403,  
    "resMessage": "API access is not enabled for this agent"
}
```

This response is returned when the agent is authenticated successfully but does not have permission to access the API service.

**500 — Internal Server Error**

```
{  
   "resCode": 500,  
   "resMessage": "Internal server error occurred while processing the authentication request"
}
```

This response is returned when the authentication service encounters an unexpected internal processing failure.

**500 — External Authentication Service Failure**

```
{  
   "resCode": 500,  
   "resMessage": "External authentication service failure"
}
```

This response is returned when the external authentication or validation service is temporarily unavailable or fails during processing.

***

### Important Notes

* The access token is mandatory for all protected APIs.
* Authentication credentials are issued during onboarding.
* The `secretKey` should always be stored securely and must never be exposed publicly.
* Authentication should be performed securely over HTTPS connections only.
* Invalid or expired credentials will result in authentication failure.

