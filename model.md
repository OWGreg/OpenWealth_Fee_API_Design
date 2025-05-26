**Entity Relationships of a Payment Order (color-coded)**

_🟢 Green = SFTI-compatible entity (all fields)_  
_🔴 Red = Not part of current SFTI CA Payment API (or mostly incompatible)_

```mermaid
classDiagram

class PaymentOrder {
    +string paymentOrderId
    +date creationDate
    +enum status
    +object assetManager
    +Transaction[] transactions
}

class AssetManager {
    +string amId
    +string amName
    +string amLocation
    +string amAddress
}

class Transaction {
    +string transactionId
    +string externalRef
    +enum type
    +boolean performanceRelevant
    +enum statementOption
    +boolean nameClientInStatement
    +object dates
    +Creditor creditor
    +Debitor debitor
    +Amount amount
}

class Dates {
    +date valueDate
    +date executionDate
}

class Creditor {
    +string creditorIban
    +string creditorAccountRef
    +string bookingTextCreditor
    +string reasonCreditor
}

class Debitor {
    +string debtorName
    +string debtorIban
    +string debtorAccountRef
    +string bookingTextDebitor
    +string reasonDebitor
}

class Amount {
    +string currency
    +float amount
}

PaymentOrder --> AssetManager : hasOne
PaymentOrder --> Transaction : hasMany
Transaction --> Dates : hasOne
Transaction --> Creditor : hasOne
Transaction --> Debitor : hasOne
Transaction --> Amount : hasOne
```

---

### 🛑 Out-of-Scope Fields

| Field                  | Reason for Exclusion                                                                 |
|------------------------|--------------------------------------------------------------------------------------|
| `creditorIbanCurrency` | The target account's currency is determined by the IBAN itself; value is redundant.  |
