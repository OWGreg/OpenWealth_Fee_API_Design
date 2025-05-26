# Payment API – Entity Model

This document describes the draft entity structure for a fee-related payment API, compatible with the OpenWealth initiative.

---

## Entity: PaymentOrder

| Field           | Type   | Description                          |
|-----------------|--------|--------------------------------------|
| paymentOrderId  | String | Unique ID of the overall instruction |
| creationDate    | Date   | Timestamp of creation                |
| status          | Enum   | PENDING, SENT, EXECUTED, FAILED      |
| assetManager    | Object | See `AssetManager`                   |
| transactions    | Array  | List of `Transaction` objects        |

---

## Entity: AssetManager

| Field     | Type   | Description                                 |
|-----------|--------|---------------------------------------------|
| amId      | String | External ID (e.g. LEI, UID, internal ref)   |
| amName    | String | Name of the asset manager                   |
| amLocation| String | Legal address or base location              |

---

## Entity: Transaction

| Field         | Type   | Description                          |
|---------------|--------|--------------------------------------|
| transactionId | String | Optional unique ID                   |
| details       | Object | See `Details`                        |
| creditor      | Object | See `Creditor`                       |
| debtor        | Object | See `Debtor`                         |
| amount        | Object | See `Amount`                         |

---

## Entity: Details

| Field                   | Type    | Description                              |
|-------------------------|---------|------------------------------------------|
| externalRef             | String  | External reference (optional)            |
| type                    | Enum    | Transaction type (e.g. Management Fee)   |
| bookingTextCreditor     | String  | Creditor's booking reference             |
| bookingTextDebitor      | String  | Debtor's booking reference               |
| reasonCreditor          | String  | Reason from creditor's perspective       |
| reasonDebtor            | String  | Reason from debtor's perspective         |
| valueDate               | Date    | Value date (ISO 8601)                    |
| executionDate           | Date    | Execution date (ISO 8601)                |
| performanceRelevant     | Boolean | Is the transaction performance-relevant? |
| statementOption         | Enum    | Statement inclusion option               |
| nameClientInStatement   | Boolean | Show client name in statement            |

---

## Entity: Creditor

| Field           | Type   | Description                           |
|------------------|--------|--------------------------------------|
| creditorName     | String | Name of receiving institution        |
| creditorLocation | String | Location of the creditor             |

---

## Entity: Debtor

| Field             | Type   | Description                          |
|-------------------|--------|--------------------------------------|
| debtorName        | String | Name of the payer                    |
| debtorIban        | String | IBAN of the payer                    |
| debtorAccountRef  | String | Internal account reference (optional)|

---

## Entity: Amount

| Field     | Type   | Description                          |
|-----------|--------|--------------------------------------|
| currency  | String | ISO 4217 currency code (e.g. CHF)    |
| amount    | Float  | Positive amount, max. 2 decimals     |
