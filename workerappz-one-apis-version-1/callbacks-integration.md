# Callbacks Integration

Callback APIs notify your system about transaction updates.

Your callback URL should accept POST requests.

Example:

POST https://yourdomain.com/callback

Example payload:

```json
{
  "transactionId": "XXXYYZZZ",
  "status": "SUCCESS",
  "amount": 898.50
}
```
