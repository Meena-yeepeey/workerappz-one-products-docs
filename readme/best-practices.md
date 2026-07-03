# Best Practices

The best practices below are recommended to ensure secure and reliable integration with the **WorkerAppz One API**.

#### Always Use HTTPS

All API requests must be sent using **HTTPS** to ensure that communication between the client application and the API server is encrypted and protected from unauthorized access.

***

#### Store API Credentials Securely

API credentials such as **clientId** and **secretKey** should always be stored securely on the server side and should never be exposed in public repositories or client-side applications.

***

#### Do Not Expose Tokens in Frontend Applications

Authentication tokens should only be used in **server-to-server communication** and must not be exposed in frontend code, browser requests, or mobile applications.

***

#### Validate Request Data Before Sending

Applications should validate all required request parameters before sending them to the API to avoid invalid requests and unnecessary API errors.

***

#### Handle API Errors Properly

Client applications should implement proper error handling to manage API responses and display meaningful messages when a request fails.

***

#### Use Pagination for Large Data Responses

When retrieving large datasets such as transaction history or bank lists, pagination parameters should be used to improve performance and reduce response size.

