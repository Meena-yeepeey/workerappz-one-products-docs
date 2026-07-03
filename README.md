---
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# Introduction

### Overview

**WorkerAppz Payments** is a global cross-border payment and remittance platform that enables businesses, financial institutions, exchange houses, and payment providers to securely send, receive, and manage international payments across multiple countries and currencies.

The platform supports a wide range of payment solutions including:

* Cross-border money transfers
* Global individual payouts
* Business payments
* Wallet and bank payouts
* International remittance services
* Global prepaid card programs

WorkerAppz Payments supports multiple transaction models such as:

* **C2C (Customer to Customer)**
* **C2B (Customer to Business)**
* **B2C (Business to Customer)**
* **B2B (Business to Business)**

The platform enables organizations to process supplier payments, marketplace payouts, employee disbursements, partner settlements, and customer remittances through a secure and scalable infrastructure.

With support for real-time exchange rates, multi-currency transactions, dynamic payout configurations, and global payout networks, WorkerAppz Payments simplifies international payment processing while ensuring speed, reliability, and secure transaction management.

## Base URLs

WorkerAppz One APIs are available in different environments for testing and live transaction processing. All API endpoints in this documentation should be appended to the appropriate base URL based on the environment being used.

**Sandbox URL** (Testing Environment)

The sandbox environment is used for API testing, integration validation, and non-production transaction flows without affecting live transactions.

```
https://waonedev.workerappz.com
```

**Production URL** (Live Environment)

The production environment is used for live transaction processing and real-time payment operations.

```
https://waonedev.workerappz.com
```

**Example Endpoint**

```
https://waonedev.workerappz.com/api/v1/getexchangerate
```

## API Integration Flow

A typical integration flow is as follows:

```
Authenticate
↓
Get Request Fields
↓
Get Exchange Rate
↓
Search Bank / Payout Institution
↓
Beneficiary Account Check
↓
Create Transaction
↓
Get Transaction Details
```
